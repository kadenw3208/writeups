# Sum-O-Primes
Category: Crypto
Points: 400
## Problem Description
We have so much faith in RSA we give you not just the product of the primes, but their sum as well!

-   [gen.py](https://artifacts.picoctf.net/c/97/gen.py)
-   [output.txt](https://artifacts.picoctf.net/c/97/output.txt)
## Writeup
We are given the sum of the primes, but how can that help us? It's actually very convenient since you only need to check `p` and `q` that add up to the `x` value. We can use a tool that I found online called [z3 solver](https://github.com/Z3Prover/z3). This is a very efficient solving tool. We can use its algorithm to brute force the values for p and q. 
```python                           
from z3 import * 
x=23779403848993729529240484510333216858689977576400976881301578388787382965>
n=14107968002788601163232271919683185628377930258855714024361251700443482916>
p, q = z3.Ints('p q')


zz = z3.Solver()
zz.add(x == p + q, n == p * q)

assert zz.check() == z3.sat, 'Could not find a solution.'

p = zz.model()[p].as_long()
q = zz.model()[q].as_long()

print(p)
print(q)
```
In this code, the `zz.add()` function is the function that will get the values for which `p+q=x` and `p*q=n`. Then we can get the p and q values to print them out. This gives us:
```
┌──(kali㉿kali)-[~]
└─$ python3 Sumoprimes.py
124238665297436351535057644565670615375443538969172645932414670332019048252346424732454374287700184761196786959193566174940923144061340753375696812236797799085284060917522754635338715470410049507726019057956507759394465391650189663615302576713255389112522546651929487111766739718243933329068430413385177473431
113555373192500943757347200537661553211456236794837122880601113555854781406339483423434917996351857545875405098238265321751218735544249960436269109023300381364677749208091802101469817073745908605989047665985314018377915624692143738631532769850077802552967686024344490545101481143954168442661650896889584367639
```
Now, we can decrypt the cipher using DCODE to get the flag.
<br>`picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_3921def5}`
