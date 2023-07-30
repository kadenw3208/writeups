# Forbidden Paths
Category: Web Exploitation
Points: 100
## Problem Description
Can you get the flag?Here's the  [website](http://saturn.picoctf.net:55287/).We know that the website files live in  `/usr/share/nginx/html/`  and the flag is at  `/flag.txt`  but the website is filtering absolute file paths. Can you get past the filter to read the flag?
## Writeup
We know that since the website files live in `/usr/share/nginx/html/` we have to cd to the original 4 times via `../../../../`. We also have to put on the flag file at the very end to get our flag.
<br>
Final payload: `../../../../flag.txt`
<br>
`picoCTF{7h3_p47h_70_5ucc355_e5a6fcbc}`
