---
title: CDCTF 2025 - Forensics - Foorensik challenges suite
date: 2025-09-21 22:00:00 +0100
categories: [write-up]
tags: [forensics, disk]
layout: post
---

## Challenge: Forensics - Foorensik1 (1/2)
<br>

### 1. Task description

*Flag in disk image. Forensic. Find it. You should know the drill. Flag Format cdctf{123_ex4mpl3_fl4g}*
<br><br>

### 2. Initial analysis

We're given the file `disk.7z` (1.2 MB) as the handout for both parts of this challenge suite. Once extracted, it produces a 1.1 GB disk image file `disk.img`.
The disk image does not import well to Autopsy, so no files are instantly recognised.
Executing `strings` on the disk image gives us a quick initial idea of what it contains:

![Disk strings](/assets/images/CDCTF2025/cdctf2025-1.png)

Searching for common flag file extensions, other than `.png`, returns no results.

A quick verification with `grep` is also handy to make sure the disk image contains actual PNG data we could extract:

![Grep verification](/assets/images/CDCTF2025/cdctf2025-2.png)

It seems there are 16 possible PNG files on the disk image.
<br><br>

### 3. PNG files extraction

A Python script could be used to extract all 16 PNG files from the disk image. The script:
- Reads the contents of the disk image file in binary mode
- Searches for occurrences of PNG headers (`89504e47` in hex)
- Searches for occurrences of PNG footers (`ae426082` in hex)
- Extracts what sits between each header-footer pair
- Saves it as a `.png` file

```python
#!/usr/bin/env python3

disk_file = "/tmp/ramdisk/disk.img"
png_header = bytes.fromhex("89504e47")
png_footer = bytes.fromhex("ae426082")

with open(disk_file, "rb") as f:
    data = f.read()

files, start = [], 0
while True:
    start = data.find(png_header, start)        # return -1 if no header found
    if start == -1:
        break

    end = data.find(png_footer, start)          # return -1 if no footer after header found
    if end == -1:
        break

    end += len(png_footer)                      # include footer
    files.append(data[start:end])
    start = end                                 # move search forward

for i, content in enumerate(files, start=1):
    filename = f"file{i}.png"
    with open(filename, "wb") as out:
        out.write(content)
    print(f"Extracted {filename} ({len(content)} bytes)")

print(f"Done - {len(files)} extracted files in total.")

```

This results in all 16 PNG files extracted successfully. Most of them are cat memes. Meow. One contains the flag:

![Flag file](/assets/images/CDCTF2025/cdctf2025-3.png)
<br><br>

### 4. Flag
```
cdctf{67_kn33_surgerY}
```
<br><br>

## Challenge: Forensics - Foorensik2 (2/2)
First blood by `OP_EN`; special acknowledgment from the event organisers.
<br>

### 1. Task description

*That wasn't too bad right? Now find the filename of the file containing the flag (in hex, except for extension)*
*Flag format cdctf{000102030405060708090a0b0c0d0e0f.ext}*
<br><br>

### 2. Initial analysis

PNG files do not contain their names anywhere between `IHDR` and `IEND` headers, so there is no way to determine the original name of the extracted flag file from its contents alone.
<br><br>

### 3. Data extraction

Importing the disk image into [FTK Imager](https://www.exterro.com/digital-forensics-software/ftk-imager) and searching for the `.png` extension shows a directory listing with all 16 occurrences of the `.png` extension:

![FTK data](/assets/images/CDCTF2025/cdctf2025-4.png)

Copy the hex data selected above, change it to lowercase (for example in CyberChef), and save it as a text file.
<br><br>

### 4. Filename extraction

As the flag format in the challenge description suggests, the filename consists of 32 lowercase hex characters, followed by the extension.

A Python script could be used for preparing a list of candidate flags for submission. The script:
- Reads the contents of the text file prepared above
- Searches for occurrences of the `.png` extension in hex
- Gets the 32 hex characters that precede each `.png` extension
- Prints a list of flag candidates for submission

```python
#!/usr/bin/env python3

hex_data = "/tmp/ramdisk/hex_data.txt"
extension = "2e706e67"                                  # .png in hex

with open(hex_data, "rt") as f:
    data = f.read()

candidates, position = [], 0

while True:
    index = data.find(extension, position)              # return -1 if no .png found
    if index == -1:
        break

    if index >= 32:                                     # get 32 hex characters before .png if available
        prefix = data[index-32:index]
        filename = prefix + ".png"
        candidates.append(filename)

    position = index + len(extension)                   # move search forward

for i in range(len(candidates)):
    print(f"Flag candidate #{i+1}:")
    flag_candidate = "cdctf{" + candidates[i] + "}"
    print(flag_candidate)

```

The above results in the following output:

![Candidate flags](/assets/images/CDCTF2025/cdctf2025-5.png)

Because the event engine allows 25 flag submission attempts for this challenge, and there are 16 candidate flags in the output, one of them should eventually work.
<br><br>

### 5. Flag
```
cdctf{3c089f34e56be99003d412246f248ead.png}
```
