# Dachshund Attacks
Category: Cryptography
Points: 80
Author: Kaden Wu
## Problem Description
What if `d` is too small? Connect with `nc mercury.picoctf.net 37455`.
## Writeup
In order to solve this question, your first need to know a general skill called [netcat](https://www.tutorialspoint.com/the-netcat-command-in-linux).

Then, you can connect to the server via picoCTF's own [webshell](https://webshell.picoctf.org).

After you get the RSA values for N, C, and E, you can now proceed to solve the question. 

Plug the respective values into an [RSA decoder](https://dcode.fr/rsa-cipher).

`picoCTF{proving_wiener_3878674}`
