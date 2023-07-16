# Play Nice
Category: Crypto
Points: 110
Author: Kaden Wu
## Problem Description
Not all ancient ciphers were so bad... The flag is not in standard format. `nc mercury.picoctf.net 40742`  [playfair.py](https://mercury.picoctf.net/static/283dcc58048f3a6ac83b4c11ec696954/playfair.py)
## Writeup
After netcatting to the server, we find this:
```
Here is the alphabet: irlgektq8ayfp5zu037nov1m9xbc64shwjd2
Here is the encrypted message: h5a1sqeusdi38obzy0j5h3ift7s2r2
```
If we open up the Playfair file, we can see at the bottom that it leads to a Wikipedia page for the Playfair Cipher. 

We can try a Playfair cipher decoder, such as [this one](https://dcode.fr/playfair-cipher).

After putting it in, we get this long string as our result:
`XQYVHTG02JKPLZO8EYHU25KTIP2DKH`
After converting it to lowercase and putting this into the Netcat server, we find:
```
Congratulations! Here's the flag: 25a0ea7ff711f17bddefe26a6354b2f3
```
Thus, we have our flag:
`25a0ea7ff711f17bddefe26a6354b2f3`
