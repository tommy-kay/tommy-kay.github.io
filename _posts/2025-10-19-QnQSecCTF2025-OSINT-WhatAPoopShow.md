---
title: (own) QnQSec CTF 2025 Special Round - Osint - What a poop show
date: 2025-10-20 03:00:00 +0100
categories: [write-up]
tags: [osint, geoosint]
layout: post
---

## Challenge: Osint - What a :poop: show

This is the official write-up by the challenge author.

This is an easy (Geo)OSINT challenge submitted for the Special Round of QnQSec CTF 2025.
<br><br>

### 1. Description and handout

*Back in the day, brave construction and maintenance workers relieved themselves high above the waves, with only the sea to catch what fell below.*

*Find the coordinates of the southernmost loo on the structure shown in the picture, as seen on Google Maps, in decimal degrees.*

*Once found, truncate them to **3** decimal places, separate them with a comma, then add curly brackets and the prefix.*

*For example, if you believe the coordinates are: `lat -43.911999°` and `lon 7.000999°`, the flag should be `QnQSec{-43.911,7.000}`.*

Handout:

![Challenge handout](/assets/images/QnQSecCTF2025/qnqsecctf2025-1.png)

### 2. Initial analysis

A reverse image search of the handout file returns results pointing to articles and posts about a preserved, disused toilet from the 1940s located on the [Forth (Rail) Bridge](https://en.wikipedia.org/wiki/Forth_Bridge) in Scotland.

The challenge description asks for the coordinates of the *southernmost* toilet, hinting at the fact there is more than one of them on the bridge.

Due to the bridge's sheer size and length, locating toilets visually, even in high-resolution photos, is challenging. It's much easier to do it using train cab view videos.
<br><br>

### 3. Setup

Searching for `Forth Rail Bridge cab view` on YouTube returns many results. 
In this write-up, [the following video](https://www.youtube.com/watch?v=HLkw7q935Wk) from Scotland's national train operator `ScotRail` is used.

The video's description states that the train is heading towards Edinburgh. The footage begins at a station just before the bridge and ends at the approach to the station just after the bridge.
Taking this information into account when inspecting the bridge area on the map, it can be established that:
- The train is going south
- The footage begins at `North Queensferry` and ends at `Dalmeny`

![Area Setup](/assets/images/QnQSecCTF2025/qnqsecctf2025-2.png)

Therefore, the *southernmost* toilet on the bridge will be the *last* toilet identified in the video.
<br><br>

### 4. Locating toilets

For locating structures on the bridge, it is useful to lower the speed and increase the resolution of the video.

There are **three** toilets and three canteens on the bridge, one of each per bridge tower.

The first structure identified is a canteen. Canteens are located on the left-hand side of the tracks (eastern side of the bridge) at `0:53`, `1:22`, and `1:47` in the [video](https://www.youtube.com/watch?v=HLkw7q935Wk):

![Canteen](/assets/images/QnQSecCTF2025/qnqsecctf2025-3.png)

Toilets are located on the right-hand side of the tracks (western side of the bridge) at `1:04`, `1:30`, and `1:54` (**the toilet** in question) in the [video](https://www.youtube.com/watch?v=HLkw7q935Wk):

![Toilet - cab view](/assets/images/QnQSecCTF2025/qnqsecctf2025-4.png)

Take note of features that could help pinpoint the exact location of the toilet on a 3D map, such as the portal and the vertical ties.
<br><br>

### 5. Getting coordinates

As the toilet is located close to the southern portal, finding it on Google Maps or Google Earth is straightforward, although switching to the 3D view is necessary:

![Toilet - 3D view](/assets/images/QnQSecCTF2025/qnqsecctf2025-5.png)

Either right-clicking on the toilet in Google Maps or hovering over it in Google Earth gives us the full coordinates:

![Google Earth coordinates](/assets/images/QnQSecCTF2025/qnqsecctf2025-6.png)

The coordinates need to be truncated to three decimal places, which provides approximately:
- 111 metres of latitude accuracy
- 60 metres of longitude accuracy

This compensates for any inaccuracy caused by the "guesswork" of using a 3D map.
<br><br>

### 6. Flag

```
QnQSec{55.994,-3.385}
```

<br>
I hope you've enjoyed my first ever challenge. Cheers,

`[OP_EN]tommy_kay`
