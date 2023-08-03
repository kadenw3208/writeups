# triple-secure
Category: Crypto
Points: 150
## Problem Description
To get the flag, you must break RSA not once, but three times!

----------

## CHALLENGE ENDPOINTS

Download public-key.txt

- [public-key.txt](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/triple-secure/public-key.txt)

Download encrypt.py

- [encrypt.py](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/triple-secure/encrypt.py)

## Writeup
Since we are given three RSA values, we can multiply them together and then divide to find `p, q` and `r` separately. This script implements that perfectly:
```python                      
from Crypto import *
from Crypto.Util.number import *
from sympy import *
n1=1519249205981417557494105524889126882216253352057638164345391685543531088>
n2=1589648225960890155930714294194044723278198663250257299109635874235427634>
n3=1686674102429090951505772727521639850573218239886691855048437390588251757>
e=65537
c=55275571305494866268683556383431645566366406459750705638787916848720845686>
a=int(sqrt(n1*n2*n3, 2))
r=a//n1
q=a//n2
p=a//n3
p1=(p-1)*(q-1)
p2=(p-1)*(r-1)
p3=(q-1)*(r-1)
d1=pow(e,-1,p1)
d2=pow(e,-1,p2)
d3=pow(e,-1,p3)
f=pow(c, d3, n3)
f=pow(f, d2, n2)
f=pow(f, d1, n1)
print(long_to_bytes(f).decode())
```
This script will calculate the square root of the numbers multiplied together first, and then that is p^2^ * r^2^  * q^2^ . So, we can take the square root to find `pqr` and then just calculate each value separately. Once we have the values, we can find the flag.
<br>`picoCTF{1_gu3ss_tr1pl3_rs4_1snt_tr1pl3_s3cur3!!!!!!}`
