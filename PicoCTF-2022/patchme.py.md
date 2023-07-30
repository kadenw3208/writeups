# `patchme.py`
Category: Reverse Engineering
Points: 100
## Problem Description
Can you get the flag?Run this  [Python program](https://artifacts.picoctf.net/c/202/patchme.flag.py)  in the same directory as this  [encrypted flag](https://artifacts.picoctf.net/c/202/flag.txt.enc).
## Writeup
We can see that it requires a password when we download both files and then run the python file using `python3 patchme.flag.py`. So we go back to look at the python file.

```python
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "ak98" + \
                   "-=90" + \
                   "adfjhgj321" + \
                   "sleuth9000"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), "utilitarian")
        print(decryption)
        return
    print("That password is incorrect")
```
We can see that our user password has to be a concatenation of 4 different strings. After adding the strings back together, we get a password of `ak98-=90adfjhgj321sleuth9000`. After inputting that we get our flag.
<br> `picoCTF{p47ch1ng_l1f3_h4ck_21d62e33}`
