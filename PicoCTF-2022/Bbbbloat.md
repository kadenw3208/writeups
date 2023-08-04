# Bbbbloat
Category: Forensics
Points: 300
## Problem Description
Can you get the flag?Reverse engineer this  [binary](https://artifacts.picoctf.net/c/47/bbbbloat).
## Writeup

We can disassemble this file in Ghidra to get:
![im](https://i.ibb.co/KKFSDZF/image.png)
On the right, we can see if the register is equal to `0x86187`, we can see that the flag will be printed. `0x86187` is equivalent to `549255` in base 10. We can input this into the master server to get our flag.
<br> `picoCTF{cu7_7h3_bl047_44f74a60}`
