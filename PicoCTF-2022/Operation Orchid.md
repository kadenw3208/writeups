# Operation Orchid
Category: Forensics
Points: 400
## Problem Description
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into  `/tmp`  not your home directory.

-   [Download compressed disk image](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)
## Writeup
When we first look at the question, it seems just like any other normal challenge that we have done before. We unzip the image, use mmls, and start searching.
```
┌──(kali㉿kali)-[~]
└─$ fls -o 411648 disk.flag.img     
d/d 460:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 81: proc
d/d 82: dev
d/d 83: tmp
d/d 84: lib
d/d 87: var
d/d 96: usr
d/d 106:        bin
d/d 120:        sbin
d/d 466:        media
d/d 470:        mnt
d/d 471:        opt
d/d 472:        root
d/d 473:        run
d/d 475:        srv
d/d 476:        sys
d/d 2041:       swap
V/V 51001:      $OrphanFiles
```
We hunt for root.
```
┌──(kali㉿kali)-[~]
└─$ fls -o 411648 disk.flag.img 472
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
```

We cat out `flag.txt.enc` first.
```
┌──(kali㉿kali)-[~]
└─$ icat -o 411648 disk.flag.img 1782               
Salted__�ށ��e��B�J▒�c�$QE&$��4jM�KGeE�1�^Ȥ7� ���؎$�'%                                                                             
```
Interesting. Let's look at `.ash_history` next.
```
┌──(kali㉿kali)-[~]
└─$ icat -o 411648 disk.flag.img 1875
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```
We can see that this was encrypted using the `AES256` encryption algorithm. The flag was encrypted, outputted into `flag.txt.enc` and then shredded. First, we output the text into our own `flag.txt.enc` file.
```
┌──(kali㉿kali)-[~]
└─$ icat -o 411648 disk.flag.img 1782 > flag.txt.enc
```
Now, we decrypt using `openssl` and get the flag.
```
┌──(kali㉿kali)-[~]
└─$ openssl aes256 -d -in flag.txt.enc -k unbreakablepassword1234567
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
4057D7242E7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:124:
picoCTF{h4un71ng_p457_5113beab} 
```
<br>`picoCTF{h4un71ng_p457_5113beab}`
