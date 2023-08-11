# It's not my fault 1
Category: Crypto
Points: 300
## Problem Description
What do you mean RSA with CRT has an attack that's not a fault attack? Connect with `nc mercury.picoctf.net 41175`. [not_my_fault.py](https://mercury.picoctf.net/static/caa819502b5c603aa2873e71ee070db0/not_my_fault.py)
## Writeup
When we first try to nc to the server, we have to pass an md5 check first. This can be bruteforced with a script:
```python                                  
import hashlib

def solve(strst, h_e):
    i = 0
    while True:
        test_string = strst + str(i)
       test_string_hash = str(hashlib.md5(test_string.encode("utf-8")).hexdigest())

        if test_string_hash[-len(h_e) :] == h_e:
            return test_string

        i += 1
n=input("Enter a string: ")
h=input("Enter a hash: ")
print(solve(n,h))
```
This script will bruteforce every single possible outcome by testing if it ends with the hash.<br>
Now, we can move on and see that we are given a public modulus and a clue, which is the public exponent. We can use the `gcd` function of the library `gmpy2` to solve this. This solve script will bruteforce the possibilities for the p and q values. <br>
```python
import gmpy2
n = 100287481027687100569150985755985227864153931989696992648840905230091804>
e = 114349339533784290571104260455273876991535892053107156967012077843296179>
m = 7516789928765

for i in range(1000000):
    f = gmpy2.gcd(m-pow(m, e*i, n), n)
    if f > 1:
        print(i, f)
        
        break
```
After getting the p and q values, and entering them in for p and q in the master server, we get the flag.
<br>Flag: `picoCTF{1_c4n'7_b3l13v3_17'5_n07_f4ul7_4774ck!!!}`
