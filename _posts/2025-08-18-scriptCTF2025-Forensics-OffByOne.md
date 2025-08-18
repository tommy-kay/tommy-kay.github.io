---
title: scriptCTF 2025 - Forensics - Off By One
date: 2025-08-18 01:00:00 +0100
categories: [write-up]
tags: [forensics, qr]
layout: post
---

#### `Forensics - Off By One`
46 solves out of 1190 teams. 

Embargoed after the event for verification.
<br><br>

### 1. Initial analysis

Scanning the QR code in the given `hidden.png` get us [Rick-rolled](https://www.youtube.com/watch?v=dQw4w9WgXcQ).
<br><br>

### 2. Deeper visual analysis

For this step, different tools could be used:
- [AperiSolve](https://www.aperisolve.com/)
- [StegOnline](https://georgeom.net/StegOnline/upload)
- [StegSolve](https://github.com/Giotino/stegsolve)

Inspecting individual colour channels of `hidden.png` reveals unusual information included at the top of the QR code in `Blue 0` channel:
![Blue 0](/assets/images/scriptCTF2025/scriptctf2025-1.png)
<br><br>

### 3. Extracting additional data

Extracting that data is as easy as selecting the right channel. Here's an example for `StegOnline`:
![Extracting Blue 0](/assets/images/scriptCTF2025/scriptctf2025-2.png)

Highlighted top hex data, including all trailing zeros of the hex sequence and a few extra hex characters, should be enough:
![Hex data](/assets/images/scriptCTF2025/scriptctf2025-3.png)
<br><br>

### 4. Constructing new QR code

To build the new QR code leading to the flag, a script is needed that:
- Takes the extracted hex data and converts it to a binary string
- Trims trailing binary characters until the total length of the string is a perfect square (as QR codes are square)
- Creates a black and white image where 1s are black pixels and 0s are white pixels of the QR code
- Scales up and displays the new QR code with the flag

```python
from PIL import Image
import math

# Extracted hex data with trailing zeros and some f-characters:
hex_data = "000000000000000fe423f8416cd042e9c0ba175ae5d0ba28ae841519043faaafe00010000fbedd507ce16a80a9763e120e6a20ffd7e6842356b025f148610054e20a38ffa800734683fb6ab610425100bad1fb85d4638c2eb1d5210519710feaa058000000000000007fff"

# Convert hex string to binary string:
data = bytes.fromhex(hex_data)
bin_str = ''.join(format(byte, '08b') for byte in data)

# Trim trailing binary characters by 1 until perfect square:
while True:
    length = len(bin_str)
    size = int(math.isqrt(length))
    if size * size == length:
        break
    bin_str = bin_str[:-1]
print(f"Final length: {len(bin_str)}, Square size: {size}x{size}")

# Build QR code, 1 is black and 0 is white:
img = Image.new("1", (size, size))
for i, bit in enumerate(bin_str):
    x = i % size
    y = i // size
    img.putpixel((x, y), 0 if bit == "1" else 1)

# Scale up for readability
img = img.resize((size*10, size*10), Image.NEAREST)
img.save("qr_flag.png")
img.show()

```

This results in the following image:

![New QR](/assets/images/scriptCTF2025/scriptctf2025-4.png)
<br><br>

### 5. Getting the flag

Uploading the image to an [online service](https://scanqr.org/image-qr-code-scanner/) or scanning it with an app gives us the following flag:

`scriptCTF{qrqrqrc0d3s}`
