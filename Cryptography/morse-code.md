# morse-code
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
Morse code is well known. Can you decrypt this? Download the file  [here](https://artifacts.picoctf.net/c/79/morse_chal.wav). Wrap your answer with picoCTF{}, put underscores in place of pauses, and use all lowercase.
## Writeup
We can use an online morse code decoder to solve this:
https://morsecode.world/international/decoder/audio-decoder-adaptive.html
We get a result of:
`WH47H47H90DW20U9H7`
After converting to lowercase and adding spaces, we have our flag:

`picoCTF{wh47_h47h_90d_w20u9h7}`
