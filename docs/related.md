# Related Work

Every project stands on the shoulders of great projects that preceded it.
This section refers to some of the related projects and works that provided inspiration and
reference.
It is an annotated bibliography not an exhaustive academic list of references.

_Characterisation of a new lightweight LoRaWAN GPS bio-logger and deployment on griffon vultures Gyps fulvus_,
Gauld, J., Atkinson, P.W., Silva, J.P. et al.
Anim Biotelemetry 11, 17 (2023).
[https://doi.org/10.1186/s40317-023-00329-y](https://doi.org/10.1186/s40317-023-00329-y)

The tracking of griffon vultures using LoRaWAN GPS bio-loggers can be described as doing
almost everything that RadioJay tags are attempting, except that the actually deployed tags
weighted several grams. The description of the system mentions the option of using public
LoRaWAN networks (The Things Network specifically) but for the vulture tracking
private stations were deployed, most likely due to lack of TTN coverage.
Technical details are unfortunately not available and the tags made by Miromico have
all but disappeared from their web site.

_Micro-sized open-source and low-cost GPS loggers below 1 g minimise the impact on animals while collecting thousands of fixes_,
Wild TA, Koblitz JC, Dechmann DKN, Dietz C, Meboldt M, et al.
PLOS ONE 17(6) (June 2022): e0267730.
[https://doi.org/10.1371/journal.pone.0267730](https://doi.org/10.1371/journal.pone.0267730)

The TickTag project is a DIY GPS biologger that is fully open source and invites anyone to make
their own. Is is an inspiring example for making all details of the project available. It is also
one of the lightest weight DYI trackers coming in at 0.65 grams without battery or housing (which
alas add significant weight). The project also makes the design files for a programming board available
which rounds everything out. The sources for hardware and software are available at
https://github.com/trichl/TickTagOpenSource

_Vildehaye: A Family of Versatile, Widely-Applicable, and Field-Proven Lightweight Wildlife Tracking and Sensing Tags_,
S. Toledo et al.,
2022 21st ACM/IEEE International Conference on Information Processing in Sensor Networks (IPSN),
Milano, Italy, 2022, pp. 1-14,
[https://doi.org/10.1109/IPSN54338.2022.00008](https://doi.org/10.1109/IPSN54338.2022.00008)

The Videhaye project has produced a whole array of bird tags that work together with the ATLAS
TDOA (time difference of arrival) localization system. The tags are modular and sensors can be added,
the data being downloaded via radio link. The engineering os very nicely done and a number of papers
describe various aspects, but unfortunately nothing is open source.
The project also produced a very interesting paper about what happens when tiny batteries are
overloaded by the power demands of radio transmission:
[The Secret Lives of Miniature Batteries](https://www.mdpi.com/1424-8220/24/3/748)

_Mobile-BAT—A Novel Ultra-Low Power Wildlife Tracking System_,
Erhardt S, Koch M, Kiefer A, Veith M, Weigel R, Koelpin A.
Sensors. 2023; 23(11):5236. [https://doi.org/10.3390/s23115236](https://doi.org/10.3390/s23115236)

The Mobile-BAT project built very lightweight tags to track bats using cellular GSM stations to
determine location. The tags make ingenious use of an integrated radio IC as SDR (software defined radio)
to decode the cell station IDs of GSM stations. When the bats return to roost the tags download the
data to a nearby station via radio link.

[Activity and migratory flights of individual free-flying songbirds throughout the annual cycle: method and first case study](https://nsojournals.onlinelibrary.wiley.com/action/showCitFormats?doi=10.1111%2Fjav.01068),
Bäckman, J., Andersson, A., Alerstam, T., Pedersen, L., Sjöberg, S., Thorup, K. and Tøttrup, A.P. (2017),
J Avian Biol, 48: 309-319. [https://doi.org/10.1111/jav.01068](https://doi.org/10.1111/jav.01068)

This study as well as several others by the same principal author use bio-loggers with accelerometers
to record the activity of birds through a full migration cycle. The papers describe the methodology for
recording the actograms in detail allowing the RadioJay to use the same or a very similar methodology.

[Energy Consumption Analysis of LPWAN Technologies and Lifetime Estimation for IoT Application](https://doi.org/10.3390/s20174794),
Singh RK, Puluckul PP, Berkvens R, Weyn M.
Sensors. 2020; 20(17):4794. [https://doi.org/10.3390/s20174794](https://doi.org/10.3390/s20174794)

This paper has a very detailed analysis of the energy consumption of several Low-Power Wide-Area
networks, including LoRaWAN as well as NB-Iot. It supports the case that LoRaWAN is the most
appropriate choice for ultra-lighteight tags at this point in time and characterizes where
NB-IoT becomes a better choice: basically when transferring larger amounts of data.

Gould, L.A., Manning, A.D., McGinness, H.M. et al.
[A review of electronic devices for tracking small and medium migratory shorebirds](https://animalbiotelemetry.biomedcentral.com/articles/10.1186/s40317-024-00368-z#Sec9),
Anim Biotelemetry 12, 11 (2024).
[https://doi.org/10.1186/s40317-024-00368-z](https://doi.org/10.1186/s40317-024-00368-z)

This review describes the state of the art in commercially available GPS trackers for small birds.

_Three-dimensional tracking of a wide-ranging marine predator: flight heights and vulnerability to offshore wind farms_,
Cleasby, I.R., Wakefield, E.D., Bearhop, S., Bodey, T.W., Votier, S.C. and Hamer, K.C. (2015),
J Appl Ecol, 52: 1474-1482.
[https://doi.org/10.1111/1365-2664.12529](https://doi.org/10.1111/1365-2664.12529)

Interesting tracking of birds around wind farms and an inspiration for the RadioJay altimeter tags.
Some of the examples of dives show that a logger must be able to provide high temporal resolution
of rapid altitude changes otherwise critical data will not be captured. This is part of what makes
purely real-time data transmission for this type of study questionable and also puts into question
whether GPS tags can reliably record this type of event.
