# Very Smooth
Category: Crypto
Points: 400
Author: Kaden Wu
## Problem Description
Forget safe primes... Here, we like to live life dangerously... >:)

-   [gen.py](https://artifacts.picoctf.net/c/149/gen.py)
-   [output.txt](https://artifacts.picoctf.net/c/149/output.txt)

## Writeup

After opening the file up, it seems like the numbers are in hexadecimal. We can use a hex decoder and then find the decimal values of these numbers.
This can be decoded via the [Pollard-PM1 Factorization Algorithm](https://en.wikipedia.org/wiki/Pollard%27s_p_%E2%88%92_1_algorithm#:~:text=Pollard's%20p%20%E2%88%92%201%20algorithm%20is,an%20algebraic%2Dgroup%20factorisation%20algorithm.).
I wrote a script to do this for us:
```python
import gmpy2
import primefac


n = int(input("Enter your number for Pollard-PM1 factorization: "))
q = primefac.pollard_pm1(n)
p = n/q
print(p)
print(q)
```

We can enter in our n value and get `p` and `q`, and after that we can just plug it into DCODE for the flag:
`picoCTF{p0ll4rd_f4ct0r1z4at10n_FTW_7c8625a1}`
