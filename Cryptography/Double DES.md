# Double DES
Category: Crypto
Points: 120
## Problem Description
I wanted an encryption service that's more secure than regular DES, but not as slow as 3DES... The flag is not in standard format. `nc mercury.picoctf.net 37751`  [ddes.py](https://mercury.picoctf.net/static/a31327d353582ee5a6eca77ad7b15aab/ddes.py)
## Writeup
Double DES is vulnerable to a meet-in-the-middle attack. More info [here](https://security.stackexchange.com/questions/122624/how-does-the-meet-in-the-middle-attack-work-on-double-des). First, we can test with some keys. Inputting an 8 bit key like `14481448` gives us `d69f0e9fdc803fcd`. We can use this to help decrypt the cipher. We can start off by brute forcing the first key, and then the second key, and then taking the intersection. We should also include the padding in our code, and also notice that the padding is just two spaces.
```python
import binascii
from Crypto.Cipher import DES
from tqdm import tqdm

padding = "  "
encrypted_flag = binascii.unhexlify("6f745ccee635f76746be185541b9f9c046b8d707f93d0522e2325fb041c59ec7bbbaa818d7c51381")

def pad(msg):
    block_len = 8
    over = len(msg) % block_len
    pad = block_len - over
    return (msg + " " * pad).encode()

ck = pad(binascii.unhexlify("13371337").decode())
cc = binascii.unhexlify("8f45ca8a9264c2aa")

encrypt_table = {}
for key in range(1000000):
    key = (f"{key:06}" + padding).encode()
    cipher = DES.new(key, DES.MODE_ECB)
    ec = cipher.encrypt(ck)
    encrypt_table[ec] = key

decrypt_table = {}
for key in range(1000000):
    key = (f"{key:06}" + padding).encode()
    cipher = DES.new(key, DES.MODE_ECB)
    dc = cipher.decrypt(cc)
    decrypt_table[dc] = key

ets = set(encrypt_table.keys())
dts = set(decrypt_table.keys())
for i in ets.intersection(dts):
    encrypt_key = encrypt_table[i]
    decrypt_key = decrypt_table[i]
    break
print("1st Key: %s" % encrypt_key)
print("2nd Key: %s" % decrypt_key)
c1 = DES.new(encrypt_key, DES.MODE_ECB)
c2 = DES.new(decrypt_key, DES.MODE_ECB)
fi = c2.decrypt(encrypted_flag)
flag = c1.decrypt(fi).decode()
print(flag)
```
This gives us:
```
1st Key: b'571957  '
2nd Key: b'991599  '
9af5126b7bc7f825b3cae0e32bd1acb4   
```
So, our flag is `9af5126b7bc7f825b3cae0e32bd1acb4`
<br>*credit to Hayden Housen when I was stuck he helped me move a little*
