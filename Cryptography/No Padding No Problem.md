
# No Padding No Problem
Category: Crypto
Points: 90
## Problem Description
Oracles can be your best friend, they will decrypt anything, except the flag's ciphertext. How will you break it? Connect with `nc mercury.picoctf.net 10333`.
## Writeup
Upon connecting to the server, we can see the ciphertext, the modulus, and the public key. We aren't allowed to type in the ciphertext to decrypt, though. So what else can we do? If you add a number by the modded amount, it won't change the result. So we can just add n to c and then put that in as the ciphertext. this gives: `290275030195850039473456618367455885069965748851278076756743720446703314517401359267322769037469251445384426639837648598397`. Now, we can use `long_to_bytes` function in python to get the flag. 
<br> Flag: `picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_1772735}`
