# unpackme
Category: Reverse Engineering <br>
Points: 300
## Problem Description
Can you get the flag?Reverse engineer this  [binary](https://artifacts.picoctf.net/c/205/unpackme-upx).
# Writeup
We can first unpack this binary by using `upx -d` command. After that, we can analyze in Ghidra.
![im](https://i.ibb.co/xFJKZds/image.png)
Same as `Bbbbloat`, `0xb83cb` translates to `754635`. 
<br> `picoCTF{up><_m3_f7w_5769b54e}`
