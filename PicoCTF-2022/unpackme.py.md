# `unpackme.py`
Category: Reverse Engineering
Points: 100
## Problem Description
Can you get the flag?Reverse engineer this  [Python program](https://artifacts.picoctf.net/c/49/unpackme.flag.py).
## Writeup
When we open the file, we realize that it is Base64 with a special twist. It is encoded using the symmetric encryption cipher `Fernet`. We can use a fernet decoder, with the payload as the token and the key string as the key, and we get:
<br>
```python
pw = input('What\'s the password? ')

if pw == 'batteryhorse':
  print('picoCTF{175_chr157m45_cd82f94c}')
else:
  print('That password is incorrect.')
```
Now, we can see our flag.
<br>
`picoCTF{175_chr157m45_cd82f94c}`
