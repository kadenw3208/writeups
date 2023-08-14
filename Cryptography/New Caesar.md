# New Caesar
Category: Crypto
Points: 60
## Problem Description
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) `apbopjbobpnjpjnmnnnmnlnbamnpnononpnaaaamnlnkapndnkncamnpapncnbannaapncndnlnpna`  [new_caesar.py](https://mercury.picoctf.net/static/d8a6722e08659449dd091668c0c9bbca/new_caesar.py)
## Writeup: 
When we open up new_ceasar.py, we see:<br>
```python
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
	enc = ""
	for c in plain:
		binary = "{0:08b}".format(ord(c))
		enc += ALPHABET[int(binary[:4], 2)]
		enc += ALPHABET[int(binary[4:], 2)]
	return enc

def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
	enc += shift(c, key[i % len(key)])
print(enc)
```
We can see that in the `b16_encode` function, each letter is taken apart, put into binary, and recombined. We can reverse this:
```python
def b16_decode(cipher):
    dec = ""
    for i in range(0, len(cipher), 2):
        c1 = cipher[i]
        c2 = cipher[i + 1]
        c1 = ALPHABET.index(c1)
        c2 = ALPHABET.index(c2)
        b1 = "{0:04b}".format(c1)
        b2 = "{0:04b}".format(c2)
        bb = int(b1 + b2, 2)

        dec += chr(bb)
    return dec
```
This code loops through two characters of the ciphertext at a time, and finds their positions in the alphabet. Then, it is encoded into binary and then recombined at the end. The next part to look at is the shifting part:
```python
LOWERCASE_OFFSET = ord("a")
def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]
```
To decode this, we just do the exact opposite:
```python
def shift(c, k):
    t1 = ord(c) + LOWERCASE_OFFSET
    t2 = ord(k) + LOWERCASE_OFFSET
    return ALPHABET[(t1 - t2) % len(ALPHABET)]
```
When we decode the final flag, we need a function to check if the characters are ascii characters:
```python
def ascii(s):
    return len(s) == len(s.encode())
```
Then, to implement the functions:
```python
for letter in ALPHABET:
    decrypt = ""
    for i, c in enumerate(cipher):
        decrypt += shift(c, letter)
    decrypt = b16_decode(decrypt)

    if ascii(decrypt) and " " not in decrypt:
        print(decrypt)
```
What this code will do is loop through each part of the alphabet (ALPHABET = string.ascii_lowercase[:16]) and slowly first unshift the cipher. Then, we decode it using our `b16_decode` function. At the very end, we check to see if the characters are ascii, and that there aren't any extra spaces. Doing so gives us:
```python
et_tu?_23217b54456fb10e908b5e87c6e89156
CR=RS=@D@C@CAC
2A,AB
?202 ,?3?
```
Only the first one seems like it could be a flag, so we have our answer.<br>
Flag: `picoCTF{et_tu?_23217b54456fb10e908b5e87c6e89156}`
