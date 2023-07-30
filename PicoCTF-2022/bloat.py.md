# `bloat.py`
Category: Reverse Engineering
Points: 200
## Problem Description
Can you get the flag?Run this  [Python program](https://artifacts.picoctf.net/c/104/bloat.flag.py)  in the same directory as this  [encrypted flag](https://artifacts.picoctf.net/c/104/flag.txt.enc).
## Writeup
This problem is almost identical to `patchme.py`, but the difference is that when we open up the file, the way of checking the password is different, so let's open it up:
```python
import sys
a = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \
            "[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~ "
def arg133(arg432):
  if arg432 == a[71]+a[64]+a[79]+a[79]+a[88]+a[66]+a[71]+a[64]+a[77]+a[66]+a[68]:
    return True
  else:
    print(a[51]+a[71]+a[64]+a[83]+a[94]+a[79]+a[64]+a[82]+a[82]+a[86]+a[78]+\
a[81]+a[67]+a[94]+a[72]+a[82]+a[94]+a[72]+a[77]+a[66]+a[78]+a[81]+\
a[81]+a[68]+a[66]+a[83])
    sys.exit(0)
    return False
```
It seems like that long string could be our password, so we print out that string and get `happychance`, which is our password. Now the same way follows from `patchme.py` to get the flag.
<br>`picoCTF{d30bfu5c4710n_f7w_161a4f09}`
