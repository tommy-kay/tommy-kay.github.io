---
layout: home
title: idekCTF 2025 - Misc - Z-hard
date: 2025-08-04 11:00:00 +0100
categories: [write-up]
tags: [misc,osint,geoosint]
---

#### `misc/Z - hard`
9 solves out of 843 teams; second-blooded by `OP_EN`.
<br><br>

### 1. `torga`
Reverse image search of the ruins on the hill returns *Castle of Miranda do Douro*.

GSV Photo Sphere location: [41.4969674, -6.2753894.](https://www.google.co.uk/maps/place/Miranda+do+Douro's+Castle/@41.4969622,-6.2754122,3a,75y,159.98h,93.29t/data=!3m7!1e1!3m5!1s1InTQdIJOe479l7DPAv6VQ!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D-3.2873590495245963%26panoid%3D1InTQdIJOe479l7DPAv6VQ%26yaw%3D159.9838895762535!7i16384!8i8192!4m7!3m6!1s0xd3967d2538acd4f:0x13fad2f2d68dce11!8m2!3d41.4966098!4d-6.2752261!10e5!16s%2Fm%2F0h63hwk?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)

To verify the picture, switch to *Jul 2014* in `See more dates`.
<br><br>

### 2. `mini_cooper`
Searching for the phrase `Central Coast Council`, printed on the wheelie bin, returns results for two Australian councils: one in NSW and one in Tasmania.

Reverse image search lottery of the coastal view results in the following [Facebook post](https://www.facebook.com/groups/383640681840827/permalink/2697682563769949/?sale_post_id=2697682563769949), narrowing the location down to Penguin, Tasmania.

Switching to `Satellite` view in Google Maps helps identify and inspect cul-de-sacs in the town a bit quicker.

GSV Photo Sphere location: [-41.1111428, 146.0649474.](https://www.google.co.uk/maps/place/Penguin+TAS+7316,+Australia/@-41.1111428,146.0649474,3a,75y,233.82h,86.7t/data=!3m7!1e1!3m5!1s4WXTdYxMdvfA1xWeG7SlCw!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D3.3016627301451535%26panoid%3D4WXTdYxMdvfA1xWeG7SlCw%26yaw%3D233.81837382008388!7i16384!8i8192!4m6!3m5!1s0xaa7bc7ad92d905cd:0x403c94dd0ddf250!8m2!3d-41.1140595!4d146.0731033!16zL20vMDNibjA1!5m1!1e4?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 3. `vagrant`
Searching for the phrase `The News Tribune`, printed on the blue newspaper tube, returns results for a newspaper covering Tacoma County and Pierce County in the state of Washington, USA.

The search for the exact location is tedious. To make it easier:
- Switch to `Satellite` view in Google Maps
- Note the layout of access roads
- Note the presence of a tennis court, clearly visible from the satellite

GSV Photo Sphere location: [47.2397457, -122.6311317.](https://www.google.co.uk/maps/place/Tacoma,+WA,+USA/@47.2397457,-122.6311317,3a,75y,23.75h,82.42t/data=!3m7!1e1!3m5!1s4O1Ec0T5S5jtzXDr8_Jtgg!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D7.580859029874929%26panoid%3D4O1Ec0T5S5jtzXDr8_Jtgg%26yaw%3D23.752379297959692!7i16384!8i8192!4m6!3m5!1s0x549054ee2b659567:0x62219c07ebb09e82!8m2!3d47.255134!4d-122.4420002!16zL20vMDEwdDR2?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 4. `walkable`
Reverse image search lottery, focused on the silo, island, bridge, and the mountain range behind them, narrows down the location to Valdez, Alaska.

GSV coverage in the area is limited, and finding the correct location is fairly easy, although switching to `Satellite` view to pinpoint the nearby parking bay is helpful.

GSV Photo Sphere location: [61.1380127, -146.3191159.](https://www.google.co.uk/maps/place/Valdez+Container+Terminal/@61.1380127,-146.3191159,3a,75y,6.83h,76.48t/data=!3m7!1e1!3m5!1sKZbL4ucOBUkEgQNEfDP0Ug!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D13.515561529864883%26panoid%3DKZbL4ucOBUkEgQNEfDP0Ug%26yaw%3D6.832348705608638!7i13312!8i6656!4m15!1m8!3m7!1s0x56b644030f1a7539:0x1f54b4edc991a14f!2sValdez,+AK,+USA!3b1!8m2!3d61.1308812!4d-146.3498607!16s%2Fm%2F01z22hm!3m5!1s0x56b6452a520250b5:0xc4075ebcd13b2740!8m2!3d61.1249505!4d-146.3082087!16s%2Fg%2F11glxc2_ns!5m1!1e4?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 5. `1f5ff`
Reverse image search of the airport terminal building is trivial, and results in *Aeropuerto Internacional Chacalluta*.

GSV Photo Sphere location: [-18.3501287, -70.3356245.](https://www.google.co.uk/maps/place/Aeropuerto+Internacional+Chacalluta/@-18.3501287,-70.3356245,3a,60y,332.54h,78.63t/data=!3m7!1e1!3m5!1s1pJWH7cOmYJygOWsg0R6vw!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D11.368094283113095%26panoid%3D1pJWH7cOmYJygOWsg0R6vw%26yaw%3D332.5398215463107!7i13312!8i6656!4m6!3m5!1s0x915aae7540ba91f5:0x8018102dd50e1605!8m2!3d-18.349067!4d-70.3354879!16s%2Fm%2F0405fvf?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 6. `shipping`
Reverse image search lottery of the bay view results in the [following post,](https://www.shutterstock.com/image-photo/aerial-summer-view-road-alley-houses-2305123707) which narrows down the location to the Thai island of Ko Sichang.

GSV Photo Sphere location: [13.1514795, 100.8066122.](https://www.google.co.uk/maps/place/Tha+Thewawong,+Ko+Sichang+District,+Chon+Buri,+Thailand/@13.1514795,100.8066122,3a,75y,79.82h,75.24t/data=!3m10!1e1!3m8!1snknS1VKk6QiOHtd1E14MYw!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D14.757451457577105%26panoid%3DnknS1VKk6QiOHtd1E14MYw%26yaw%3D79.81988258403672!7i13312!8i6656!9m2!1b1!2i39!4m6!3m5!1s0x3102b01879ffa291:0x303d84ae1b45620!8m2!3d13.1499153!4d100.8084675!16zL20vMGNocmd0?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 7. `blue`
Not attempted. Well done to whoever managed to get it. You're the dog's b\*ll\*cks.
<br><br>

### 8. `crop_circles`
To identify the country, zoom in on the GSV car antenna. According to `GeoGuessr` tip sites, this type of antenna is only used in:
- Panama (straight)
- Oman (right-leaning)
- Namibia (left-leaning; present here)

Flat, green farmlands in Namibia are rare, as is GSV coverage of **D roads**.

[PlonkIt for Namibia](https://www.plonkit.net/namibia) also points to *baity agricultural fields* near Mariental.

GSV Photo Sphere location: [-24.6132249, 17.934065.](https://www.google.co.uk/maps/@-24.6132249,17.934065,3a,75y,287.26h,78.27t/data=!3m7!1e1!3m5!1s_0PQYd4Y8aan06-ymAH1xA!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D11.731687752589721%26panoid%3D_0PQYd4Y8aan06-ymAH1xA%26yaw%3D287.255717564271!7i16384!8i8192!5m1!1e4?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 9. `cabbage`
Reverse image search of the church results in the following [blog post](https://blog.naver.com/kwan4404/223178781715) in Korean. The church is present there on a photograph at the very bottom. There is however a campsite advertisement banner on the fourth-last photo, which has the phone number `010-6343-6516`.

Searching for `korea phone number "010-6343-6516"` returns [another blog post](https://blogsailing.com/5709) with an `OpenStreetMap` location of the campsite. The church is in the same area.

GSV Photo Sphere location: [37.5574945, 128.5650274.](https://www.google.co.uk/maps/@37.5574945,128.5650274,3a,37.5y,113.19h,81.73t/data=!3m7!1e1!3m5!1s3ozbgMQN2ia0fWABjee02w!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D8.27124224006667%26panoid%3D3ozbgMQN2ia0fWABjee02w%26yaw%3D113.18738374713476!7i13312!8i6656?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>

### 10. `blocks`
To identify the country, zoom in on the road-side marker and the isolator at the top of the utility pole. Tips from [PlonkIt](https://www.plonkit.net/philippines) help identify the country as The Philippines.

The tall, square, yellow road stones are unique to the Philippines. They show:
- Distance to *Kilometer Zero* in Manila (top figure preceeded by `K`)
- The next city and its distance (bottom)

On the road stone in this sphere, only the distance to [Kilometer Zero](https://en.wikipedia.org/wiki/Kilometre_zero#:~:text=A%20small%20obelisk%20located%20near,marker%20sometime%20during%20the%202010s.) is present (`188`).

Searching for the exact location took couple hours. I primarily used Google Map's `Directions from here` set at *Kilometer Zero* and tried different roads roughly 180-200 kilometres away as `Directions to here`.

I narrowed down the location by observing blue light posts, side blocks, and larger blocks containing stones, all in the same area. Annoyingly, these features appear separately in many other spots.

GSV Photo Sphere location: [13.9097061, 121.9948618.](https://www.google.co.uk/maps/@13.9097061,121.9948618,3a,60y,240.51h,90t/data=!3m7!1e1!3m5!1ssoZwqCOmb7saV_55w3ed8Q!2e0!6shttps:%2F%2Fstreetviewpixels-pa.googleapis.com%2Fv1%2Fthumbnail%3Fcb_client%3Dmaps_sv.tactile%26w%3D900%26h%3D600%26pitch%3D0%26panoid%3DsoZwqCOmb7saV_55w3ed8Q%26yaw%3D240.51282333699237!7i16384!8i8192?entry=ttu&g_ep=EgoyMDI1MDczMC4wIKXMDSoASAFQAw%3D%3D)
<br><br>
