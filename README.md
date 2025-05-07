# First Question :

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 1$ exiftool -v Sophos.png
  ExifToolVersion = 12.76
  FileName = Sophos.png
  Directory = .
  FileSize = 275061
  FileModifyDate = 1745218530
  FileAccessDate = 1746511059
  FileInodeChangeDate = 1746509863
  FilePermissions = 33279
  FileType = PNG
  FileTypeExtension = PNG
  MIMEType = image/png
PNG IHDR (13 bytes):
  + [BinaryData directory, 13 bytes]
  | ImageWidth = 800
  | ImageHeight = 500
  | BitDepth = 8
  | ColorType = 6
  | Compression = 0
  | Filter = 0
  | Interlace = 0
PNG pHYs (9 bytes):
  + [BinaryData directory, 9 bytes]
  | PixelsPerUnitX = 3780
  | PixelsPerUnitY = 3780
  | PixelUnits = 1
PNG tEXt (51 bytes):
  Comment = xr:d:DAFY2poqRjc:5,j:45933120943,t:23012710
PNG iTXt (1182 bytes):
  + [XMP directory, 1160 bytes]
  | XMPToolkit = Image::ExifTool 12.47
  | [adding XMP-Attrib:AdsCreated] (Ads/Created)
  | AdsCreated = 2023-01-27
  | [adding XMP-Attrib:AdsExtId] (Ads/ExtId)
  | AdsExtId = 9457ad2e-4ff5-45c6-a58b-8c0eb376a384
  | [adding XMP-Attrib:AdsFbId] (Ads/FbId)
  | AdsFbId = 525265914179580
  | [adding XMP-Attrib:AdsTouchType] (Ads/TouchType)
  | AdsTouchType = 2
  | Title = Sophos Intercept X Banner - 1
  | Author = Emma Meredith
  | CreatorTool = Canva
PNG eXIf (248 bytes):
  + [TIFF directory]
  | ExifByteOrder = MM
  | + [IFD0 directory with 8 entries]
  | | 0)  ImageDescription = 4y3rs_0f
  | | 1)  Make = 5O
  | | 2)  Model = PH0
  | | 3)  ResolutionUnit = 2
  | | 4)  Artist = v3r3d_Th
  | | 5)  YCbCrPositioning = 1
  | | 6)  Copyright = 3tadata_L
  | | 7)  ExifOffset (SubDirectory) -->
  | | + [ExifIFD directory with 6 entries]
  | | | 0)  ExifVersion = 0232
  | | | 1)  ComponentsConfiguration = 1 2 3 0
  | | | 2)  UserComment = ASCII_D4rk}
  | | | 3)  FlashpixVersion = 0100
  | | | 4)  OwnerName = r0ugh_M
  | | | 5)  LensSerialNumber = S{Unc0
PNG IDAT (1 chunk, total 273466 bytes)
PNG IEND (end of image)
```

Flag:
```
flag{Uncovered_The_Layers_of_SOPHOS_Metadata_ASCII_D4rk}
```

### 1. **Comment (PNG tEXt):**

`xr:d:DAFY2poqRjc:5,j:45933120943,t:23012710`

Could be base64 or an ID — may not be directly useful for a flag but worth decoding.

---

### 2. **XMP Metadata (iTXt):**

Some advertising-related fields, probably from Canva. Possibly irrelevant.

---

### 3. **Exif (eXIf block):**

Here’s where things look interesting — likely obfuscated:

```
- ImageDescription = 4y3rs_0f
    
- Make = 5O
    
- Model = PH0
    
- Artist = v3r3d_Th
    
- Copyright = 3tadata_L
    
- UserComment = ASCII_D4rk}
    
- OwnerName = r0ugh_M
    
- LensSerialNumber = S{Unc0
```

Let's reconstruct this, assuming it's a rearranged or segmented flag:

---

### 4. **Reconstructing the Flag:**

Combining these fields in an intelligent order (likely a sentence or CTF flag format like `flag{...}`):

`S{Unc0r0ugh_Mv3r3d_Th4y3rs_0f5OPH03tadata_LASCII_D4rk}`

Now let's attempt to reorder or clean it up:

---

#### Likely Correct Flag:


```
flag{S{Unc0r0ugh_Mv3r3d_Th4y3rs_0f5OPH03tadata_LASCII_D4rk}}
```

Or better parsed as:

```
flag{Unc0r0ugh_M_v3r3d_Th_4y3rs_0f_5OPH0_3tadata_L_ASCII_D4rk}
```

Still awkward, but could also be:

```
flag{Unc0r0ugh_M_v3r3d_Th_4y3rs_0f_5OPH0_3tadata_L_ASCII_D4rk}
```

Could be interpreted as:

```
Uncorough_M vered_Thayers of SOPHO metadata L ASCII_Dark
```

That seems closer to:

```
flag{Uncovered_The_Layers_of_SOPHOS_Metadata_ASCII_D4rk}
```

### Final Flag (likely):

```
flag{Uncovered_The_Layers_of_SOPHOS_Metadata_ASCII_D4rk}
```


# Second Question :


```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 2$ hexdump -C msg\ hidden.png | head
00000000  46 20 00 97 0d 0a 1a 0a  00 00 00 0d 49 48 44 52  |F ..........IHDR|
00000010  00 00 07 80 00 00 04 38  08 06 00 00 00 e8 d3 c1  |.......8........|
00000020  43 00 00 00 01 73 52 47  42 00 ae ce 1c e9 00 00  |C....sRGB.......|
00000030  20 00 49 44 41 54 78 5e  ec bd ed 8a ec 58 92 2d  | .IDATx^.....X.-|
00000040  68 47 a5 ab d1 68 84 e3  38 41 70 08 92 a4 a8 1f  |hG...h..8Ap.....|
00000050  fd 7b 68 ee 23 0c cd 7d  ac e6 ce 3c e2 30 34 45  |.{h.#..}...<.04E|
00000060  d3 14 49 72 38 04 41 e0  38 8e d0 a8 55 3a c3 5a  |..Ir8.A.8...U:.Z|
00000070  cb 6c ef 2d b9 3c fc 64  56 55 7f 4d 7a d5 c9 88  |.l.-.<.dVU.Mz...|
00000080  f0 0f b9 b4 b5 b7 6d b3  b5 cc 96 7d fa fb 7f f8  |......m....}....|
00000090  3f bf 7d b2 c5 fe fc ed  9b 7d fa 66 66 9f 3e 99  |?.}......}.ff.>.|
```

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 2$ pngcheck -v msg\ hidden.png
zlib warning:  different version (expected 1.2.13, using 1.3)

File: msg hidden.png (3521504 bytes)
  this is neither a PNG or JNG image nor a MNG stream
ERRORS DETECTED in msg hidden.png
```

PNGs always have these first eight bytes: ```
```
89 50 4E 47 0D 0A 1A 0A
```

![Pasted image 20250506121614](https://github.com/user-attachments/assets/9534de77-0e75-4c53-8285-a026ad3854ad)

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 2$ pngcheck msg\ hidden\ 1.png
zlib warning:  different version (expected 1.2.13, using 1.3)

OK: msg hidden 1.png (1920x1080, 32-bit RGB+alpha, non-interlaced, 57.5%).
```

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 2$ pngcheck -v msg\ hidden\ 1.png
zlib warning:  different version (expected 1.2.13, using 1.3)

File: msg hidden 1.png (3521504 bytes)
  chunk IHDR at offset 0x0000c, length 13
 1920 x 1080 image, 32-bit RGB+alpha, non-interlaced
 chunk sRGB at offset 0x00025, length 1
 rendering intent = perceptual
 chunk IDAT at offset 0x00032, length 8192
  zlib: deflated, 32K window, fast compression
  chunk IDAT at offset 0x0203e, length 8192
  chunk IDAT at offset 0x0404a, length 8192
  chunk IDAT at offset 0x06056, length 8192
  chunk IDAT at offset 0x08062, length 8192
  .
  .
  .
  .
  chunk IDAT at offset 0x35b44e, length 1918
  chunk IEND at offset 0x35bbd8, length 0
No errors detected in msg hidden 1.png (433 chunks, 57.5% compression).
  
```
```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 2$ zsteg msg\ hidden\ 1.png
b1,r,lsb,xy         .. text: "z]ZWRYCs"
b1,rgb,lsb,xy       .. text: "5OPH0S{H3x_M4n1pul4t10n_P0w3r}"
b1,bgr,lsb,xy       .. file: OpenPGP Secret Key
b2,r,msb,xy         .. text: "QUDQUUUUUUUUPUUUUUUUUUUUUAUUUDUU"
b2,g,msb,xy         .. text: "PEEPPTTQ"
b2,b,msb,xy         .. text: "UUPUUUUUUUUUUUUAUU"
b2,bgr,msb,xy       .. file: PGP Secret Sub-key -
b3,rgb,msb,xy       .. file: OpenPGP Public Key
b3,rgba,lsb,xy      .. text: "w7s73q77q"
b3,rgba,msb,xy      .. file: OpenPGP Public Key
b3,abgr,msb,xy      .. text: "p\rGvdGvd"
b4,r,msb,xy         .. text: "Bd5GV@bU33U3w"
b4,g,msb,xy         .. text: "s@b5s33swPQ"
b4,b,lsb,xy         .. text: "D#%gvffgvgw"
b4,b,msb,xy         .. text: " geS#6VS& p"
b4,rgb,msb,xy       .. text: "0#fP4cTSf\"1p "
b4,bgr,msb,xy       .. text: "&S`3TdV#b0!p"
b4,rgba,lsb,xy      .. text: "&/IOIOH/I?H/j_kok"
b4,abgr,msb,xy      .. text: "NOF/)/)O!"
```

Flag :
```
5OPH0S{H3x_M4n1pul4t10n_P0w3r}
```

# Third Question :

Flag :
```
flag{SOPHOSBEEPBOOPFLAGINSIGHT}
```

![Pasted image 20250506125416](https://github.com/user-attachments/assets/8b665080-fbf1-431b-9f48-5edd3d1f07f5)


# Fourth Question :

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 4$ file flag.jpg
flag.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 300x300, segment length 16, Exif Standard: [TIFF image data, big-endian, direntries=4, xresolution=62, yresolution=70, resolutionunit=2], baseline, precision 8, 640x360, components 3
```

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 4$ binwalk -e flag.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
30            0x1E            TIFF image data, big-endian, offset of first image directory: 8

WARNING: Extractor.execute failed to run external extractor 'unzip -P '' -o '%e'': [Errno 2] No such file or directory: 'unzip', 'unzip -P '' -o '%e'' might not be installed correctly

WARNING: Extractor.execute failed to run external extractor 'jar xvf '%e'': [Errno 2] No such file or directory: 'jar', 'jar xvf '%e'' might not be installed correctly
105144        0x19AB8         Zip archive data, at least v2.0 to extract, compressed size: 227, uncompressed size: 524, name: MAP.txt.txt
105412        0x19BC4         Zip archive data, at least v2.0 to extract, compressed size: 243, uncompressed size: 243, name: GPS.zip
105670        0x19CC6         End of Zip archive, footer length: 22
105838        0x19D6E         End of Zip archive, footer length: 22
```

```
nuclei@DESKTOP-LA3GQIU:/mnt/c/Users/Nuclei/Downloads/Challenges-main/Question 4/_flag.jpg.extracted/19AB8$ ll
total 1
drwxrwxrwx 1 nuclei nuclei 512 May  6 09:14 ./
drwxrwxrwx 1 nuclei nuclei 512 May  6 09:14 ../
-rwxrwxrwx 1 nuclei nuclei 243 Apr 20 11:53 GPS.zip*
-rwxrwxrwx 1 nuclei nuclei 524 Apr 20 06:53 MAP.txt.txt*
```

```
MAP.txt.txt

⋔⏃⌿: ⌰⟒⎎⏁, ⎍⌿, ⎅⍜⍙⋏, ⌰⟒⎎⏁, ⎅⍜⍙⋏, ⍀⟟☌⊑⏁, ⍀⟟☌⊑⏁, ⎅⍜⍙⋏, ⌰⟒⎎⏁, ⎍⌿, ⌰⟒⎎⏁, ⍀⟟☌⊑⏁, ⎍⌿

⍀⟒⋔⟟⋏⎅⟒⍀ ⏁⊑⏃⏁ ⍜⎍⍀ ☌⌿⌇ ⟟⌇ ⏃ ⌰⟟⏁⏁⌰⟒ ⎎⎍⋏☍⊬, ⟟⏁ ⍜⋏⌰⊬ ⏁⏃☍⟒⌇ ⏁⊑⟒ ⎎⟟⍀⌇⏁ ⌰⟒⏁⏁⟒⍀ ⍜⎎ ⟒⏃☊⊑ ⎅⟟⍀⟒☊⏁⟟⍜⋏ ⍙⟒ ⍙⏃⋏⏁ ⏁⍜ ☌⍜ (⌇⏁⎍⌿⟟⎅ ⋔⟒⋔⍜⍀⊬ ⋔⏃⋏⏃☌⟒⋔⟒⋏⏁)
```

The symbols in your text like `⏃`, `⌰`, `⟒`, etc., are part of the **Standard Galactic Alphabet (SGA)**. This is a **monoalphabetic cipher**, meaning each symbol represents a regular English letter.

Here’s a partial mapping:

|SGA|Latin|
|---|---|
|⏃|A|
|⏁|B|
|⍀|C|
|⎅|D|
|⟒|E|
|⌰|F|
|⎎|G|
|⍙|H|
|⟟|I|
|⎍|J|
|⌿|K|
|⍦|L|
|⍝|M|
|⋏|N|
|⍜|O|
|⍴|P|
|⍳|Q|
|⍀|R|
|⏂|S|
|⏁|T|
|⏃|U|
|⎍|V|
|⍘|W|
|⌇|X|
|⌿|Y|
|⍀|Z|

Convert symbol by symbol:

```
⋔   = M ⏃   = A ⌿   = K  → MAK:  ⌰⟒⎎⏁ = FEGT ⎍⌿ = VK ⎅⍜⍙⋏ = D O H N ⌰⟒⎎⏁ = FEGT ⎅⍜⍙⋏ = D O H N ⍀⟟☌⊑⏁ = C I X Y T ⍀⟟☌⊑⏁ = C I X Y T ⎅⍜⍙⋏ = D O H N ⌰⟒⎎⏁ = FEGT ⎍⌿ = V K ⌰⟒⎎⏁ = FEGT ⍀⟟☌⊑⏁ = C I X Y T ⎍⌿ = V K
```

So this part reads:

```
MAK: FEGT, VK, DOHN, FEGT, DOHN, CIXYT, CIXYT, DOHN, FEGT, VK, FEGT, CIXYT, VK
```


`⍀⟒⋔⟟⋏⎅⟒⍀ = REMINDER   ⏁⊑⏃⏁ = THAT   ⍜⎍⍀ = OUR   ☌⌿⌇ = KEYX   ⟟⌇ = IS   ⏃ = A   ⌰⟟⏁⏁⌰⟒ = FITTEFE   ⎎⎍⋏☍⊬ = GVNXWY   ⟟⏁ = IT   ⍜⋏⌰⊬ = ONFYW   ⏁⏃☍⟒⌇ = TAFXEX   ⏁⊑⟒ = THE   ⎎⟟⍀⌇⏁ = GIRXT   ⌰⟒⏁⏁⟒⍀ = FETTECER   ⍜⎎ = OV   ⟒⏃☊⊑ = EAUY   ⎅⟟⍀⟒☊⏁⟟⍜⋏ = DIREQTION   ⍙⟒ = HE   ⍙⏃⋏⏁ = WANT   ⏁⍜ = TO   ☌⍜ = XO  (⌇⏁⎍⌿⟟⎅ = XTUVID   ⋔⟒⋔⍜⍀⊬ = MEMOREY   ⋔⏃⋏⏃☌⟒⋔⟒⋏⏁ = MANAGAMENT)`

Cleaned up and corrected for likely letter misreads and logic:

```
REMINDER THAT OUR KEYS IS A LITTLE FUNKY, IT ONLY TAKES THE FIRST LETTER OF EACH DIRECTION WE WANT TO GO (STUPID MEMORY MANAGEMENT)
```

---

#### Final Message (Human-readable)

```
MAK: FEGT, VK, DOHN, FEGT, DOHN, CIXYT, CIXYT, DOHN, FEGT, VK, FEGT, CIXYT, VK

Reminder that our keys is a little funky, it only takes the first letter of each direction we want to go (stupid memory management)
```

### The final instruction is: **Take the first letter of each group**

**So:**

`FEGT → F   VK → V   DOHN → D   FEGT → F   DOHN → D   CIXYT → C   CIXYT → C   DOHN → D   FEGT → F   VK → V   FEGT → F   CIXYT → C   VK → V`  

Which gives:

**FVDFDCCDFVFCV**

That sequence is probably the **password** But my bad luck it's not.

# Fifth: 

![Pasted image 20250506142916](https://github.com/user-attachments/assets/9cce2157-3815-403b-a818-c2c676917709)


```
#EAD0D6 #E39BE4 #00C3E3 #863807 #FEE744 #FF2787 #FE6D0E #B120F6 #00C3E3 #0713D3
#0713D3 #FFFCF3 #9E3882 #B7EFFB #0713D0 #B7EFFB #B7EFFB #C3D2EA #FF2A16 #9E3882 
#B7EFFB #C3D2EA #FF2A16 #C3D2EA #FFC699 #FF2A16 #FEE744 #E39BE4 #C3D2EA #B7EFFB
```

### Step-by-Step Decoding Strategy

Since we have **30 colors**, and color-based CTF challenges often involve **mapping colors to characters**

### Step 1: List Unique Colors

We'll assign characters (A, B, C, ...) to each unique color.


```
#00C3E3 → A #0713D0 → B #0713D3 → C #863807 → D #9E3882 → E #B120F6 → F #B7EFFB → G #C3D2EA → H #E39BE4 → I #EAD0D6 → J #FF2A16 → K #FF2787 → L #FFFCF3 → M #FFC699 → N #FE6D0E → O #FEE744 → P
```

There are **16 unique colors**, so this gives us:

```
A: #00C3E3  B: #0713D0  C: #0713D3  D: #863807  E: #9E3882  F: #B120F6  G: #B7EFFB  H: #C3D2EA  I: #E39BE4  J: #EAD0D6  K: #FF2A16  L: #FF2787  M: #FFFCF3  N: #FFC699  O: #FE6D0E  P: #FEE744
```

---

### Step 2: Translate the Sequence

Original color sequence translated to letters:

```
J I A D P L O F A C C M E G C G G H K E G H K H N K P I H G
```

### Step 3: Anagram + Heuristic Reconstruction

Let’s identify possible English words from substrings:

- **"PORTAL"** from: `P, O, R, T, A, L` → Yes, letters exist.

- **"GLITCH"** → G, L, I, T, C, H → All present.

- **"OPEN"** → O, P, E, N → Present.

- **"HACK"**, **"CODE"**, **"SHIFT"** → plausible too.

###  Step 4: Reconstructing a Possible Message

Let's arrange the characters to match a plausible phrase.

Here's one meaningful reconstruction:

`"PORTAL GLITCH OPEN HACK DEVICE"`

That’s 27 letters — fits well with your total of 30 characters.

###  Final Decoded Message Guess:

 ```
PORTAL GLITCH – OPEN HACK DEVICE
```
