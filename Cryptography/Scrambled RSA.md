# Scrambled: RSA
Category: Crypto
Points: 140
## Problem Description
Hmmm I wonder if you have learned your lesson... Let's see if you understand RSA and how the encryption works. Connect with `nc mercury.picoctf.net 61477`.
## Writeup
This type of RSA has multiple outputs for every input depending on the length size. For example, inputting `a` only has 1 ciphertext, inputting `ab` has 2 ciphertexts, `abc` has 3 ciphertexts, etc. We also notice that part of these numbers appear in the next number, which means we can just write a script to brute force every single character to find the flag.
```python                             
from pwn import *
import string
chars = string.ascii_letters+string.digits+"_-\{\}"

dflag = ''
k = []
r = remote("mercury.picoctf.net", 61477)
flag = r.recvline(keepends=False).decode()[6:]
r.recvline()
r.recvline()

while '}' not in dflag:
    for i in chars:
        payload = dflag+i
        r.sendafter("me: ", payload+"\n")
        enc = r.recvline(keepends=False).decode().split("Here you go: ")[1]
        for chunks in k:
            enc = enc.replace(chunks, '')
        if(enc in flag):
            flag = flag.replace(enc, '')
            k.append(enc)
            dflag += i
            print(dflag)
            break

```
In this code we can make good use of the remote() and revcline() functions to help us bruteforce the flag. This code will erase the known parts of the encrypted, check to see if the new encrypted text is in the flag, and append it to our decrypted flag if it is.
<br>Flag: `picoCTF{bad_1d3a5_4981729}`
