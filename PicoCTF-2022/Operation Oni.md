# Operation Oni
Category: Forensics
Points: 300
## Problem Description
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into  `/tmp`  not your home directory.

-   [Download disk image](https://artifacts.picoctf.net/c/71/disk.img.gz)
-   Remote machine:  `ssh -i key_file -p 52691 ctf-player@saturn.picoctf.net`
## Writeup
after unzipping the file with `gzip -d disk.img.gz`, we can now use `mmls` to find that the offset is  `206848`. We can now use the fls command with `fls -o 206848 disk.img` to look for the root directory. 
```
┌──(kali㉿kali)-[~]
└─$ fls -o 206848 disk.img     
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 79: proc
d/d 80: dev
d/d 81: tmp
d/d 82: lib
d/d 85: var
d/d 94: usr
d/d 104:        bin
d/d 118:        sbin
d/d 464:        media
d/d 468:        mnt
d/d 469:        opt
d/d 470:        root
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
```
Since the root directory is in 470, we target that next.
```
┌──(kali㉿kali)-[~]
└─$ fls -o 206848 disk.img 470 
r/r 2344:       .ash_history
d/d 3916:       .ssh
```
We continue, going further into ssh:
```
┌──(kali㉿kali)-[~]
└─$ fls -o 206848 disk.img 3916
r/r 2345:       id_ed25519
r/r 2346:       id_ed25519.pub
```
We can now use the icat command to find the public key.
```
┌──(kali㉿kali)-[~]
└─$ icat -o 206848 disk.img 2345 
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
```
Now that we can put it into a file called `key_file` to access the server via `ssh`.  However, there is one small problem:
```
┌──(kali㉿kali)-[~]
└─$ ssh -i key_file -p 52691 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:52691 ([13.59.203.175]:52691)' can't be established.
ED25519 key fingerprint is SHA256:n94nLukQlGYTSdsVuSurElo+nztyfGCaqM5iWQiaeOA.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:1: [hashed name]
    ~/.ssh/known_hosts:2: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:52691' (ED25519) to the list of known hosts.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'key_file' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "key_file": bad permissions
ctf-player@saturn.picoctf.net's password: 
```
It seems that our permissions are too loose. Luckily, that can be fixed by using `chmod 400 key_file` to make the permissions read only. Now when we do that, we can find the flag:
```
┌──(kali㉿kali)-[~]
└─$ ssh -i key_file -p 52691 ctf-player@saturn.picoctf.net

Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.19.0-1024-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ ls
flag.txt
ctf-player@challenge:~$ cat flag.txt
picoCTF{k3y_5l3u7h_af277f77}ctf-player@challenge:~$ ^C
ctf-player@challenge:~$ ^C
ctf-player@challenge:~$ 
```
<br>`picoCTF{k3y_5l3u7h_af277f77}`
