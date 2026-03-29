---
title: TexSAW 2026 - OSINT - Snapshot Street
date: 2026-03-29 18:00:00 +0100
categories: [write-up]
tags: [osint,geoosint]
layout: post
---

## Challenge: OSINT - Snapshot Street

25 solves out of 510 teams; 3rd solve by `OP_EN`.
<br><br>

### 1. Description and handout

*Wandering through this country, or is it a continent?, you’ll notice a mix of everyday city life: a café where locals gather, a ᗰajor fast-food spot bustling with activity, and a modest lodge tucked nearby.*

*These three locations form a loose triangle in the area. Looking around and in between them can help narrow down the exact location. If you look closely, it’s like taking a beautiful SS of the scene and you might just spot the street hidden in plain sight.*

*Find the name of the street.*

*Flag format: texsaw{streetname_st} or texsaw{drivename_dr}*

<br>
Handout:

![Challenge handout](/assets/images/TexSAW2026/texsaw2026-osint-1.png)
<br><br>

### 2. Initial analysis

From the challenge description we can gather that:
- The place is somewhere in Australia, which is both a country and a continent
- The place is likely in or around a city
- A cafe, a hotel/lodge and a McDonald's "restaurant" are nearby, forming a triangle with the target street inside

<br>
From the photo we can gather that:
- The beach is patrolled by lifeguards, as there is a flag pole visible
- The shoreline is recessed and at a low tide, and the mudflat is exposed
<br><br>

### 3. Reverse image search

The reverse image search lottery, coupled with the keyword `Australia`, returns some results for beaches near Darwin, Northern Territory, among others: 

![Reverse image search](/assets/images/TexSAW2026/texsaw2026-osint-2.png)

This is a good starting point, as beaches there are [tidal](https://www.tide-forecast.com/locations/Darwin-Australia/tides/latest).
<br><br>

### 4. Locating the photo spot

To establish the location where the photo was taken, search for `McDonald's` in Google Maps around Darwin.

There aren't that many McDonald's spots in or around the city (or in the whole of Northern Territory for that matter), so the beach can be located quickly:

[Photo location - Mindil Beach](https://maps.app.goo.gl/WMzKRvR9pgtv55e48)
<br><br>

### 5. Exploring the area

Zooming in on the area in Google Maps quickly reveals a candidate cafe without any searching:

![Area - zoom](/assets/images/TexSAW2026/texsaw2026-osint-3.png)

<br>
Searching for the keyword `lodge` in the area returns a result for `Park Lodge`, which looks modest enough:

![Park Lodge](/assets/images/TexSAW2026/texsaw2026-osint-4.png)
<br><br>

### 6. Locating the street

There aren't that many streets inside the triangle formed by the three spots. 
The `SS` clue in the challenge description suggests that the name of the street could begin with the letter **S**:

![Triangle](/assets/images/TexSAW2026/texsaw2026-osint-5.png)
<br><br>

### 7. Flag

```
texsaw{Salonika_St}
```
