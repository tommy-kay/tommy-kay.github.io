---
title: TexSAW 2026 - Misc - Three Secrets
date: 2026-03-29 18:00:00 +0100
categories: [write-up]
tags: [misc]
layout: post
---

## Challenge: Misc - Three Secrets

17 solves out of 510 teams; 4th solve by `OP_EN`.
<br><br>

### 1. Description and handouts

*When the three secrets are brought together only then can the flag be constructed.*

*Note 1: texsaw{} is already provided to you. Note 2: Please use underscores () between words when submitting your flag. Flag format: texsaw{super_epic_flag} ex: texsaw{orThog0n@l_PiZZ@$0X}*

<br>
Handouts:

[one.mp3](https://texsaw.org/files/67054494f98171d7de151d95de053358/one.mp3) | [two.gif](https://texsaw.org/files/dd0d3690790a1de85f527f1aaa9d514e/two.gif) | [three.png](https://texsaw.org/files/b65b9ccf15356f90c98f03c68a845bd7/three.png)
<br><br>

### 2. Part 1 - `one.mp3`

Obtaining the first part of the flag is as easy as opening the file in `Audacity` (or similar) and switching to `Spectrogram` view:

![Flag part 1](/assets/images/TexSAW2026/texsaw2026-misc-1.png)

Part 1 of the flag: `Ob$cur3`
<br><br>

### 3. Part 2 - `two.gif`

Opening the file in `GIMP` or similar reveals that the GIF has only one frame. This is rather odd for a file that weighs 3.4 MB. 

Inspecting the file using `gifsicle` confirms that there is some data appended to it:

![GIF - Extra data](/assets/images/TexSAW2026/texsaw2026-misc-2.png)

<br>
Executing `strings` on the file indicates that there could be another `.mp3` file appended to it, as `LAME3.100` is an MP3 encoding library:

![GIF - MP3](/assets/images/TexSAW2026/texsaw2026-misc-3.png)

<br>
Opening the file in `ImHex` or similar hex editor, preferably with structure highlighting, shows where the GIF ends and the Xing MP3 header begins:

![GIF - MP3 boundary](/assets/images/TexSAW2026/texsaw2026-misc-4.png)

<br>
Executing `binwalk` on the file does not produce any immediate results. Therefore, extracting the MP3 file can be done by either carving all bytes from the Xing MP3 header to EOF manually, or by using a short script:

```python
#!/usr/bin/python

gif_file = "two.gif"
output_file = "extracted.mp3"

pattern = bytes([0x58, 0x69, 0x6e, 0x67])       # 58 69 6e 67  "Xing"

with open(gif_file, 'rb') as gif_file:
    data = gif_file.read()

offset = data.find(pattern)

mp3_data = data[offset:]

with open(output_file, 'wb') as mp3_file:
    mp3_file.write(mp3_data)

```

<br>
Opening the extracted MP3 in `Audacity` or similar, regardless if in `Waveform` or `Spectrogram` view, shows that there's additional audio appended to the end of the track.

Simply listening to the appended bit in the last few seconds gets us the second part of the flag.

Part 2 of the flag: `steganography`
<br><br>

### 4. Part 3 - `three.png`

After eliminating known steganography methods, I followed the way of researching musical cryptograms. [This blogpost](https://www.audiocipher.com/post/musical-cryptogram) points the way to [Bücking, Correspondenz systematisch (1804)](https://img.atlasobscura.com/DMMlQ_CETi3FA3PGnQiCKZcIRZIP8_c-kZh7FpmbzMU/rs:fill:12000:12000/q:81/sm:1/scp:1/ar:1/aHR0cHM6Ly9hdGxh/cy1kZXYuczMuYW1h/em9uYXdzLmNvbS91/cGxvYWRzL2Fzc2V0/cy85ZGU1NGQ5YjI5/MzY3OWQxMjRfWjEw/NC5CODMtMTgwNC1t/dXNpYy1jb2RlLmpw/Zw.jpg), which was used in this part to simply encrypt the word `challenge`.

Part 3 of the flag: `challenge`
<br><br>

### 5. Flag

```
texsaw{Ob$cur3_steganography_challenge}
```
