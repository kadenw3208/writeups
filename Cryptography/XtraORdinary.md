# XtraORdinary
Category: Crypto
Points: 150
## Problem Description
Check out my new, never-before-seen method of encryption! I totally invented it myself. I added so many for loops that I don't even know what it does. It's extraordinarily secure!

----------

 ## CHALLENGE ENDPOINTS

Download output.txt

- [output.txt](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/xtraordinary/output.txt)

Download encrypt.py

 - [encrypt.py](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/xtraordinary/encrypt.py)
## Writeup
We can remove all of the `ever`s, as they won't make a difference to our XOR result. The nested loops also won't make a difference. Python Code:
```python
import sys
from pwn import *
from random import *

c=bytes.fromhex("57657535570c1e1c612b3468106a18492140662d2f5967442a2960684d28017931617b1f3637")


random_strs = [
    b'my encryption method',
    b'is absolutely impenetrable',
    b'and you will never',
    b'ever',
    b'break it'
]

while True:
    for random_str in random_strs:
        for x in range(randint(0, pow(2, 0))):
            c = xor(c, random_str)

    fp = b"picoCTF{"
    key = xor(c[:len(fp)], fp)
    key = b'Africa!'
    f = xor(c, key)
    if f.startswith(b"picoCTF{"):
        print(f.decode())
        sys.exit()


```
(credit: I was extremely confused when ret2basic helped me make my code faster ;)
Using this gives us our flag.
<br>`picoCTF{w41t_s0_1_d1dnt_1nv3nt_x0r???}`
