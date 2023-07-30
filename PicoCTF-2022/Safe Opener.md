# Safe Opener
Category: Reverse Engineering
Points: 100
## Problem Description
Can you open this safe?I forgot the key to my safe but this  [program](https://artifacts.picoctf.net/c/83/SafeOpener.java)  is supposed to help me with retrieving the lost key. Can you help me unlock my safe?Put the password you recover into the picoCTF flag format like:`picoCTF{password}`
## Writeup
This question revolves around the fact that the encoder used to encode the password is a Base64 Encoder, as we see in the python file. We can use a Base64 decoder to decode the text in the file. 
`picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}`
