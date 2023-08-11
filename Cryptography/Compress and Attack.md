# Compress and Attack
Category: Crypto
Points: 130
## Problem Description
Your goal is to find the flag. [compress_and_attack.py](https://mercury.picoctf.net/static/24f9e793900aeba6f183dce8e0b14e90/compress_and_attack.py)  `nc mercury.picoctf.net 33976`
## Writeup
We can use an oracle and slowly bruteforce every character using pwntools.
```python
from pwn import *
import string

sh = remote("mercury.picoctf.net", 33976)

def oracle(text):
    sh.recvuntil("encrypted:")
    sh.sendline(text)
    sh.recvline()
    sh.recvline()
    return int(sh.recvline().decode())

k = "picoCTF{"

length = oracle(k)
print(k, end="")

cur = ""
while cur != "}":
    for i in string.printable:
        if oracle(k + i) == length:
            k += i
            cur = i
            print(i, end="")
            break
```
<br>Flag: `picoCTF{sheriff_you_solved_the_crime}`
