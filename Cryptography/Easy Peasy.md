# Easy Peasy
**THIS CHALLENGE IS SO ANNOYING**
<br>Category: Crypto
Points: 40
## Problem Description
A one-time pad is unbreakable, but can you manage to recover the flag? (Wrap with picoCTF{}) `nc mercury.picoctf.net 11188`  [otp.py](https://mercury.picoctf.net/static/3cdfde8de474ba94b23aba4a2dfc7eeb/otp.py)
## Writeup
The main part of this challenge lies here:
```python
if stop >= KEY_LEN:
		stop = stop % KEY_LEN
```
This means that the key is reused. The KEY_LEN is only 50000, so we can echo in the terminal a character, just say `a` for simplicity.  We can enter 16 bytes of the text on a different line. So we can echo the characters like this:
`$ python -c "print('a'*499683);print('a'*32)" | nc mercury.picoctf.net 11188`<br>After doing so, we can see that the encrypted text is `03463d1959523d1907513d190503163d1903543d1904573d1900003b3d190457`. Since we also know that the encrypted flag is `551e6c4c5e55644b56566d1b5100153d4004026a4b52066b4a5556383d4b0007`, we can solve the challenge now. Being aware that OTP is a combination of XOR ciphers, we can XOR these two values, along with the plaintext of the a characters (`6161616161616161616161616161616161616161616161616161616161616161`, since a=61 in ascii) to get the hexadecimal value. The code for this is `$ '{:x}'.format(v1^v2^v3)`. Now, all we have to do is convert this hex value to ascii to get the flag.<br>
Flag: `picoCTF{7904ff830f1c5bba8f763707247ba3e1}`

