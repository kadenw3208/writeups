# b00tl3gRSA-3
Category: Crypto
Points: 450
Author: Kaden Wu
## Problem Description
Why use p and q when I can use more? Connect with `nc jupiter.challenges.picoctf.org 3726`.
## Writeup
When you connect to the server, it gives you some typical RSA. The modulus `n` is easy to factor, but there are tons of different factors! You can use alpertron to find the totient:
`104 213312 493511 786853 029298 213837 667060 440382 171090 090494 213280 987863 139990 138932 614653 588149 781786 240386 155312 247111 561921 324369 377528 691113 130508 057741 916322 119477 213356 291429 128693 073225 884247 768165 716431 821501 399171 904364 081670 851971 892384 573600 812709 059867 286847 623107 525709 464705 976238 651319 520563 855093 564891 084165 700722 446890 434560 000000`
Deleting the spaces and entering the result into DCODE, you get:
<br>
`picoCTF{too_many_fact0rs_8606199}`
