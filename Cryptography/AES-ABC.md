# AES-ABC
Category: Crypto
Points: 400
## Problem Description
AES-ECB is bad, so I rolled my own cipher block chaining mechanism - Addition Block Chaining! You can find the source here: [aes-abc.py](https://jupiter.challenges.picoctf.org/static/1b1beb0a49c958d0f2423800eaff58a7/aes-abc.py). The AES-ABC flag is [body.enc.ppm](https://jupiter.challenges.picoctf.org/static/1b1beb0a49c958d0f2423800eaff58a7/body.enc.ppm)
## Writeup
The main thing to notice in the script is:
```python
n_curr_blk = (prev_blk + curr_blk) % UMAX
```
In order to decode this, we just have to do the opposite, namely, `n=(curr_blk-prev_blk)%UMAX`. 
```python
from Crypto.Util.number import long_to_bytes
import math
BLOCK_SIZE = 16
UMAX = int(math.pow(256, BLOCK_SIZE))

f = open("body.enc.ppm", "rb")
#first three lines of the file are headers
h1 = f.readline()
h2 = f.readline()
h3 = f.readline()

fs = []
while True:
    d = int.from_bytes(f.read(16), "big")
    if d == 0:
        break
    fs.append(d)
pic = []
for i in range(1, len(fs)):
    a= (fs[i] - fs[i - 1]) % UMAX
  
    a= long_to_bytes(a)
   
    pic.append(a)
with open("flg.ppm", "wb") as fi:
    fi.write(h1)
    fi.write(h2)
    fi.write(h3)
    fi.write(b"".join(pic))
```
This script starts off by taking the first three lines of the file `body.enc.ppm`, because we need this in the final image. Then, we read all the data from the file, and apply the decryption process we talked about earlier. Now, we can store the contents in `flg.ppm`. After opening the image, we can open up the file. 
![im](https://i.ibb.co/kDvqj8p/image.png)
<br>`picoCTF{d0Nt_r0ll_yoUr_0wN_aES}`
