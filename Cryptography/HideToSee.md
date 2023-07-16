# HideToSee
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
How about some hide and seek heh? Look at this image  [here](https://artifacts.picoctf.net/c/237/atbash.jpg).
## Writeup
This challenge is a combination of steganography (forensic techniques) and cryptography.
We first can use a steganography tool on this:
https://futureboy.us/stegano/decinput.html
Once we input the image and hit decode, we get this:
`krxlXGU{zgyzhs_xizxp_05y2z65z}`

Remember, when we opened up the picture, there was a picture of the Atbash cipher, so this might be an Atbash cipher. We use Atbash to decode this and get:
picoCTF{atbash_crack_05b2a65a}
