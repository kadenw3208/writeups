# Roboto Sans
Category: Web Exploitation
Points: 200
## Problem Description
The flag is somewhere on this web application not necessarily on the website. Find it.Check  [this](http://saturn.picoctf.net:61304/)  out.
## Writeup
Seing the word "Robot" in the title, we go check robots.txt. This is what we find:
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```
The `==` makes us think of Base64. When we try to decode that line of text, we get `js/myfile.txt`. We visit that part of the website and get the flag. 
<br> `picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}`
