---
title: VuwCTF 2026 - OSINT - cousin 
date: 2026-08-02 11:00:00 +0100
categories: [write-up]
tags: [osint,geoosint]
layout: post
---

## Challenge: OSINT - cousin

4 solves left out of 125 teams left (after bans); First Blood by `OP_EN`.
<br><br>

### 1. Description and handout

*I parked near the intersection of a Park and a Drive and walked up to an NZ trig station to take this photo. Find the trig identification code and the date that the island in the photo was legally named. > Flag format is VuwCTF{MKID_YYYY_MM_DD}*

<br>
Handout:

![Challenge handout](/assets/images/VuwCTF2026/vuwctf2026-osint-1.png)
<br><br>

### 2. Initial analysis

From the challenge description we can gather that:
- The island is somewhere in New Zealand (duh)
- The island is close enough to be photographed from a nearby [triangulation station](https://en.wikipedia.org/wiki/Triangulation_station)
- The trig station is in a close distance to an intersection of two streets; one with a name ending with the word "Park", and one with a name ending with the word "Drive"

From the photo itself we can note the general "outline" of the island, not much beyond that.
<br><br>

### 3. Reverse image search

The reverse image search lottery does not produce any results, which I'm sure was the author's intention. 
<br><br>

### 4. Locating the photo spot

A good starting point for narrowing down the location is making use of the fact that the photo was taken near the intersection of a street whose name ends with "Park".
Such street names are rare in the Angloshpere, but they [do exist](https://addressfinder.com/nz/blog/can-you-provide-a-list-of-street-types-nz).
<br>

A simple [overpass turbo](https://overpass-turbo.eu/) query can be used to identify and show such streets on the map:
```
[out:json][timeout:60];

// Limit search to New Zealand:
area["ISO3166-1"="NZ"][admin_level=2]->.nz;   

// Streets whose name ends with "Park", note the regular expression-like use of $:
way(area.nz)
  ["highway"]
  ["name"~" Park$", i];

out body;
>;
out skel qt;
```
The above query returns a manageable number of results for "manual" verification on Google Maps + Street View. Things to look for:
- Close proximity of the street to a coastline
- Presence of islands within "photographable" distance off the coastline

<br>
One of those results leads us to the vicinity of Gisborne, where not one, but two junctions of `Tuamotu Park` and `Hamilton Drive` [exist](https://maps.app.goo.gl/wDjp5DGG8CHQQSeNA).
<br>
As Google Street View coverage of the coastline in the area does not exist, confirming the match requires a manual image search for `Tuamotu Island Gisborne`.
<br><br>

### 5. Locating the trig station

Searching for trig stations in the area can also be carried out in overpass turbo:
```
[out:json][timeout:60];

// Limit this search as well to New Zealand only:
area["ISO3166-1"="NZ"][admin_level=2]->.nz;

// Limit this search further to the vicinity of Gisborne:
node(area.nz)
  ["place"="city"]
  ["name"="Gisborne"]
  ->.g;

// Show trig stations within 10 kilometres of Gisborne:
node
  ["man_made"="survey_point"]
  ["survey_point:structure"="beacon"]
  (around.g:10000);

out body;
>;
out skel qt;
```
The above query returns a few results:

![Trig stations query results](/assets/images/VuwCTF2026/vuwctf2026-osint-3.png)
<br>

Surely, the handout photo could have only been taken near a trig station located on Tuaheni Hill near the coast:

![Trig station](/assets/images/VuwCTF2026/vuwctf2026-osint-4.png)
<br>

The trig station code can be noted directly from the above result: `A65U`.
<br><br>

### 6. Obtaining the name legalisation date

A lengthy Google search eventually leads to an [official media release](https://www.linz.govt.nz/sites/default/files/news/nzgb_media-release_820-place-name-decisions-announced_20211118_english.pdf) from The New Zealand Geographic Board, announcing over 800 name decisions, primarily in Gisborne area.
Since links in the release no longer work, as NZGB notices older than a few years are no longer present on their website, another manual search was needed. 
The 18 November 2021 notice was archived by [gazette.govt.nz](https://gazette.govt.nz/notice/id/2021-ln4906#:~:text=Pursuant%20to%20sections%2010(1)(b)%2C%2024(2)(a)%20and%2021(2),took%20effect%20on%2018%20November%202021.%20Schedule).
<br><br>

### 7. Flag

`VuwCTF{A65U_2021_11_18}`
<br><br>

### 8. Closing comments

As is usually the case with CTF write-ups:

![Meme](/assets/images/VuwCTF2026/meme.jpg)

Please keep in mind that solving this challenge was far from being linear, and also involved spending time on:
- Google phrase or image searches
- Getting overpass turbo queries to work
- Getting VPN to work in order to access `gov.nz` sites (yes, I was blocked for some reason)
- Using the wrong approach of trying dates from the [wrong sources](https://www.fadetogray.co.nz/a-tale-of-two-islands)

Cheers,
<br>
`[OP_EN]tommy_kay`
