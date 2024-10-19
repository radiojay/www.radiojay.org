# Proposal for Extending the Motus CTT packet format

_Thorsten von Eicken, 7/11/2024_

The original packet format used by the Cornell/CTT FSK tags only transmits the tag ID and is not extensible per-se. This proposal extends the format by using some tricks.

The packet extension has been designed with the thought that the Motus stations can become a data collection network where any data sent by tags in the vicinity can be captured, relayed, stored, and made available. The data can hold information about air pressure, animal activity, gps location, cell location, temperature, heart rate, VOC or other chemical air composition, or anything else.

An important constraint for the extension design is to keep backwards compatibility:
existing stations should be able to receive the transmissions of new "data" tags
(just without the data portion) and new
receivers should be able to receive the transmissions of old "data-less" tags.

## Current packet format

The current packet format consists of:

- 2 byte preamble (alternating 1's and 0's to synchronize the bit clock)
- 2 byte sync (fixed value to detect the start of actual packet bits)
- 4 byte ID (the CTT tag ID)
- 1 byte CRC (SMBUS version, can detect up to 4 bit errors)

Total: 9 bytes

The 4-byte ID can encode 2^20 distinct values. Each byte encodes 5 bits using the dictionary:
[ 0x00, 0x07, 0x19, 0x1e, 0x2a, 0x2d, 0x33, 0x34, 0x4b, 0x4c, 0x52, 0x55, 0x61, 0x66, 0x78, 0x7f, 0x80, 0x87, 0x99, 0x9e, 0xaa, 0xad, 0xb3, 0xb4, 0xcb, 0xcc, 0xd2, 0xd5, 0xe1, 0xe6, 0xf8, 0xff ].
CTT seems to use the hex form of the encoded value as "tag ID" (as opposed to the 2^20 values).

## Proposed packet format

The proposed packet format adds more bytes to the end of the current packet, terminated by a 16-bit CRC.
At the receiving end the full length is always received, then the two CRCs are checked and a
determination is made whether the received bytes hold an original short packet, a long packet,
or no packet (noise).

The specific format proposed is:

- original 9 bytes
- 1 byte format (4 bits format and 4 bits sub-format or data)
- 10 bytes data
- 2 bytes CRC16 (DNP version, can detect up to 6 bit errors, calculated over entire packet starting with ID)

Total: 22 bytes

### Shorter packet enhancement

In order to support packet lengths longer than the original CTT 9 bytes but shorter than the 22 bytes the formats could be grouped into lengths. For example:

- formats 1-4: 14 bytes total, provides 2 bytes of data
- formats 5-8: 16 bytes total, provides 4 bytes of data
- formats 9-12: 18 bytes total, provides 6 bytes of data
- formats 13-15: 22 bytes total, provides 10 bytes of data

## Packet format considerations

This packet format was chosen with the following considerations:

- compatibility with current packet format, such that old receivers can receive the ID (no data)
  of new tags and new receivers can receive the ID of old tags
- the total length is roughly 2x the original length so not a high multiplier in TX energy
  requirement and also not a high addition of receiver "deaf time" when only short packets
  are in the air
- 10 bytes can hold a meaningful amount of data, incl GPS or some historical data
- the 16-bit CRC can detect up to 6 bit errors for packet sizes up to 16 bytes, this format
  maximizes the use of the CRC

Normally variable-length FSK packets start with a length byte and receivers have support to
automatically stop RX at that length, but this is not an option if compatibility with existing
tags is desired.

Note: it may be possible to define other packet lengths using this same scheme, for example,
packet format 0 could be shorter and tack-on just a 12-bit or 20-bit data value and CRC.

## Appendix: FSK transmission parameters

- frequency: 434.0 Mhz
- bit rate: 25kbps
- deviation: 25kHz (single-sided i.e. MI=2)
- channel bandwidth: 50kHz (double-sided) [note: need to double-check!]
- NRZ & no whitening, MSB transmitted first
