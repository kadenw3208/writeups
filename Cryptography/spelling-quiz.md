# spelling-quiz
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
I found the flag, but my brother wrote a program to encrypt all his text files. He has a spelling quiz study guide too, but I don't know if that helps.

----------

**CHALLENGE ENDPOINTS**

Download public.zip

[public.zip](https://artifacts.picoctf.net/picoMini+by+redpwn/Cryptography/spelling-quiz/public.zip)
## Writeup
When we open up the file, we get: <br> Flag: `brcfxba_vfr_mid_hosbrm_iprc_exa_hoav_vwcrm
`


Using Ctrl+F, you can test each letter to see which one has the highest frequency, and that letter should generally be `e`.  After a lot of Ctrl+F, we see that the highest frequency should be `r`. After setting this equal to `e` in a special decoder called [QuipQiup](https://quipqiup.com), we can see the result:
![image](https://i.ibb.co/GJJvFJj/image.png)
<br>Flag: `picoCTF{perhaps_the_dog_jumped_over_was_just_tired}`
