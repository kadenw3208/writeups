# Power Cookie
Category: Web Exploitation
Points: 200
## Problem Description
Can you get the flag?Go to this  [website](http://saturn.picoctf.net:65442/)  and see what you can discover.
## Writeup
When you open and continue as guest, you get to a screen where it says you can't get through. However, we can go to Inspect Element > Application > Cookies to modify the `isAdmin` cookie. Once you modify that cookie to 1, it gives you the plan.
`picoCTF{gr4d3_A_c00k13_5d2505be}`
