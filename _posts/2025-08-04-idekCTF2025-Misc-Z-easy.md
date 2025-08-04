---
title: idekCTF 2025 - Misc - Z-easy
date: 2025-08-04 11:00:00 +0100
categories: [write-up]
tags: [misc,osint,geoosint]
---

#### `misc/Z - easy`
23 solves out of 843 teams; second-blooded by `OP_EN`.
<br><br>

### 1. `taxi`
Searching for the phrase `Vulcano Taxi Santi` written on the taxi returns a tour service operating in Vulcano Porto, Italy.

Switching to `Terrain` view in Google Maps helps identify a narrow, winding mountain road in the southern part of the island.

GSV Photo Sphere location: [38.3768717, 14.987448.](https://www.google.com/maps/place/Taxi+Vulcano+Santi+Tour/@38.3768717,14.987448,3a,75y,246.19h,87.18t/data=!3m10!1e1!3m8!1sI80ZsR0eZLUQ55OPcHD8QQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D2.8182514126332308%26panoid%3DI80ZsR0eZLUQ55OPcHD8QQ%26yaw%3D246.19194769312307!7i13312!8i6656!9m2!1b1!2i39!4m6!3m5!1s0x13167e937f3ada0d:0xdb866063caea885b!8m2!3d38.4136195!4d14.9596991!16s%2Fg%2F11f3r1frvx?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 2. `bridge`
Reverse image search of the bridge and the skyline (especially the tower) narrows down the area to Macau and the island of Taipa.

GSV Photo Sphere location: [22.1635853, 113.5495017.](https://www.google.co.uk/maps/place/Macao/@22.1635853,113.5495017,3a,75y,335.16h,78.56t/data=!3m7!1e1!3m5!1sH1T-9f9rI9dHmdPdcBQLHw!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D11.437736148404099%26panoid%3DH1T-9f9rI9dHmdPdcBQLHw%26yaw%3D335.1570674708349!7i13312!8i6656!4m6!3m5!1s0x34017ae0e235c8f3:0xc67be32cb485acf6!8m2!3d22.198745!4d113.543873!16zL20vMDR0aHA?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 3. `site`
Reverse image search lottery focused on what looks like an amusement park narrows down the area to Pamukkale, Turkey.

GSV Photo Sphere location: [37.9247485, 29.1159054.](https://www.google.co.uk/maps/place/Pamukkale,+20190+Pamukkale%2FDenizli,+T%C3%BCrkiye/@37.9247485,29.1159054,3a,75y,252.94h,65.24t/data=!3m10!1e1!3m8!1sFddd42w1FDEYV-mKRnKOiA!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D24.755488458637075%26panoid%3DFddd42w1FDEYV-mKRnKOiA%26yaw%3D252.94427162277825!7i16384!8i8192!9m2!1b1!2i39!4m6!3m5!1s0x14c713c95620da2f:0xb1190f5f451efcd6!8m2!3d37.9136957!4d29.1187097!16zL20vMDNuYnNs?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 4. `sanic`
Zooming in on the gantry in the distance reveals what looks like `San Antonio  West` and `Houston  East` on the signs.

Inspecting the section of `Interstate 10` between San Antonio and Houston for T-interchanges narrows down the area to Seguin, Texas.

GSV Photo Sphere location: [29.6160679, -97.876556.](https://www.google.co.uk/maps/@29.6160679,-97.876556,3a,75y,86.86h,83.73t/data=!3m7!1e1!3m5!1stbqgPNveFkGyxLOiAkdr_g!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D6.274209770986943%26panoid%3DtbqgPNveFkGyxLOiAkdr_g%26yaw%3D86.86446957583287!7i16384!8i8192?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 5. `bus_stop`
To narrow down the country:
- Reverse image search for the green Light Goods Vehicle behind the bus stop returns a Polish [FSC Lublin.](https://en.wikipedia.org/wiki/FSC_Lublin)
- Carry out the usual GeoOSINT traffic signs verification.

To narrow down the region:
- Searching for the phrase `skip 603 600 600` painted on the skip returns results for a company operating in the Poznan area.
- Reverse image search lottery focused on the bus shelter returns a [bus shelter](https://www.shutterstock.com/image-photo/poland-poznan-21-april-bus-stop-411211795) in Poznan.

Zooming in on the side of the bus shelter roof reveals bus line number `211` on a black background.

Searching for the phrase `Poznan bus lines` returns a [website](https://visitpoznan.pl/en/moving-around-the-city) that gives an overview of the public transport in the city, as well as refers to Poznan's public transport authority's website. Network maps are available [here.](https://www.ztm.poznan.pl/mapy-i-schematy-sieci/)

A more tedious solution involves following the [route](https://www.ztm.poznan.pl/wp-content/uploads/download/maps-and-network-diagrams/linie-autobusowe-nocne/211-2024.08.19.pdf) in Google Maps.

An alternative approach involves constructing an `overpass turbo` query, limiting results to buildings with the number `51` in close proximity to places of worship in the city:
```
[out:json][timeout:60];

// Define the search area for Poznan
{{geocodeArea:Poznan}}->.searchArea;

// 1. Find all buildings with addr:housenumber=51
(
  way["building"]["addr:housenumber"="51"](area.searchArea);
  node["building"]["addr:housenumber"="51"](area.searchArea);
  relation["building"]["addr:housenumber"="51"](area.searchArea);
)->.buildings51;

// 2. Find all places of worship, religious buildings, or crosses
(
  node["amenity"="place_of_worship"](area.searchArea);
  way["amenity"="place_of_worship"](area.searchArea);
  node["building"="religious"](area.searchArea);
  way["building"="religious"](area.searchArea);
  node["man_made"="cross"](area.searchArea);
  way["man_made"="cross"](area.searchArea);
)->.religious;

// 3. Find all bus stops
(
  node["highway"="bus_stop"](area.searchArea);
)->.busstops;

// 4. Filter bus stops that are within 100 meters of BOTH a building number 51 AND a religious feature
// First, those near buildings
node.busstops(around.buildings51:100)->.near_51;

// Then, those near religious features
node.near_51(around.religious:100)->.result;

// Output result
.result out body;
>;
out skel qt;
```
GSV Photo Sphere location: [52.3667423, 16.9446307.](https://www.google.co.uk/maps/place/Forteczna,+Pozna%C5%84,+Poland/@52.3667423,16.9446307,3a,75y,14.06h,76.24t/data=!3m7!1e1!3m5!1sTi32KtBTbr6C4rsvg01EPQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D13.758350010956477%26panoid%3DTi32KtBTbr6C4rsvg01EPQ%26yaw%3D14.059843168915409!7i16384!8i8192!4m6!3m5!1s0x47045af3f27a4a63:0xcec4c6f73be7a074!8m2!3d52.3676172!4d16.9398362!16s%2Fg%2F1tx141_5?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 6. `no_entry`
Entering what's written on the white board into Google Translate detects the language used as Mizo, spoken in Mizoram, India.

Reverse image search focused on the opposite hills narrows down the area to Aizawl, India.

Looking again at the white board, the first word of the upper sentence, although not fully visible, seems identical to the first word of the lower sentence. Searching for `Tlangnuam` returns results for *Tlangnuam View*, which narrows down the area even further.

GSV Photo Sphere location: [23.7056862, 92.7155214.](https://www.google.com/maps/place/Tlangnuam,+Aizawl,+Mizoram+796005,+India/@23.7056862,92.7155214,3a,75y,323.52h,69.68t/data=!3m10!1e1!3m8!1s5b1_anuHeWXRDviZB3DsyQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D20.320016195902326%26panoid%3D5b1_anuHeWXRDviZB3DsyQ%26yaw%3D323.5203332297309!7i13312!8i6656!9m2!1b1!2i39!4m6!3m5!1s0x374d948e0883c8a9:0x1830da15bd52687!8m2!3d23.7024073!4d92.7145435!16s%2Fg%2F11h1299j5!5m1!1e4?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 7. `parking`
Reverse image search lottery, focused on the mast and the building, returns results for *Rantum Loran-C transmitter* in Sylt, Germany.

GSV Photo Sphere location: [54.8107632, 8.288909.](https://www.google.co.uk/maps/place/Loran+C+Station/@54.8107632,8.288909,3a,75y,110.48h,69.07t/data=!3m7!1e1!3m5!1ssZaVf_Qz0cY3-xViQQdeag!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D20.92855849350063%26panoid%3DsZaVf_Qz0cY3-xViQQdeag%26yaw%3D110.48255091685502!7i16384!8i8192!4m6!3m5!1s0x47b4e12991c73a19:0xca5da1a4e0582167!8m2!3d54.8084207!4d8.2935951!16s%2Fg%2F11bv5v0qmx?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 8. `tour_bus`
Zooming in on the bus reveals a few distinct features:
- Red rims on a yellow bus lol
- Headwear
- Attire
- Big guns
- Facial features

which all scream: *Russia! Far East!*

While the tundra-like terrain in Russia, surrounded by mountains, is ubiquitous, its GSV coverage is not. After dropping the Pegman in random places for a while, I narrowed down the area to the *Kamchatka Peninsula*, confirmed by the long thin antenna of the GSV car and the road surface.

GSV Photo Sphere location: [53.9496019, 157.7387358.](https://www.google.co.uk/maps/@53.9496019,157.7387358,3a,75y,115.77h,80t/data=!3m7!1e1!3m5!1s04uFthOYKLSaiHmoM79QMQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D9.995759945371177%26panoid%3D04uFthOYKLSaiHmoM79QMQ%26yaw%3D115.76653142346791!7i13312!8i6656?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 9. `dragon`
Reverse image search focused on the pagoda narrows down the area to Penghu County, Taiwan. 

This [blogpost](https://rainieis.tw/chimei/) mentions the proximity of the pagoda to the *Shuangxin Stone Weir*.

GSV Photo Sphere location: [23.2187982, 119.4464139.](https://www.google.co.uk/maps/place/Twin+Hearts+Stone+Weir/@23.2187982,119.4464139,2a,75y,159.25h,67.78t/data=!3m7!1e1!3m5!1sOeY4PnooJSTKTDtG7Yd3yA!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D22.220631839851876%26panoid%3DOeY4PnooJSTKTDtG7Yd3yA%26yaw%3D159.25047889574103!7i13312!8i6656!4m6!3m5!1s0x346da7e955555555:0xe00b582ef57cb008!8m2!3d23.220255!4d119.4469133!16s%2Fm%2F03h142z!5m1!1e4?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 10. `2011`
Not attempted. Well done if you've found it.
<br><br>
