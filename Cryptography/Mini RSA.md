# Mini RSA
Category: Crypto
Points: 70
## Problem Description
What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N. Let's decrypt this: [ciphertext](https://mercury.picoctf.net/static/81689952b7442c3e23a9f703198c0a4c/ciphertext)
## Writeup
```python                             
import gmpy2

c=12200123185888718861325247578988844221745345580555937133090883049102739910>
n=16157656843214630540782260519598878842336783177348929017407633211352136367>
for i in range(1000000):
    a, root = gmpy2.iroot(i*n + c, 3)
    if root:
        print(format(bytearray.fromhex(format(a, 'x')).decode()))
        break
```
Since the e value is small, we can use the `iroot` function from the `gmpy2` package.  This will brute force the flag.
`picoCTF{e_sh0u1d_b3_lArg3r_7adb35b1}`
