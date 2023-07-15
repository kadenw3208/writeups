# The Numbers
Category: Crypto
Points: 50
Author: Kaden Wu
## Problem Description
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
## Writeup
When you download and open the file, this should pop up:
![Image](https://i.ibb.co/HprrJBv/image.png)
After inputting the numbers into [this cipher identifier](dcode.fr/cipher-identifier), it seems like the cipher is `Letter Number Code (A1Z26) A=1, B=2, C=3]`. After entering this into the cipher, we get: `PICOCTFTHENUMBERSMASON`
Therefore, We have our flag in flag format:
`picoCTF{THENUMBERSMASON}`
