# credstuff
Category: Crypto
Points: 100
Author: Kaden Wu
##  Problem Description
We found a leak of a blackmarket website's login credentials. Can you find the password of the user  `cultiris`  and successfully decrypt it? Download the leak  [here](https://artifacts.picoctf.net/c/151/leak.tar). The first user in  `usernames.txt`  corresponds to the first password in  `passwords.txt`. The second user corresponds to the second password, and so on.

## Writeup
After downloading the leak and extracting it, we can see the list of the usernames and passwords. We can use a tool like [diffchecker](https://diffchecker.com) to see what line the user `cultiris` is on.
![image](https://i.ibb.co/wC0ChKS/image.png)
It seems like the user `cultiris` is on line 378. We can now search for the 378th entry in the passwords file:
![imge2](https://i.ibb.co/r4L8MXZ/image.png)
At the 378th line of the `Changed Text` field, we can see that the 378th entry is `cvpbPGS{P7e1S_54I35_71Z3}`. The `cvpbPGS` makes us think of ROT13, so let's try decoding the entry with that, and it gives us:
`picoCTF{C7r1F_54V35_71M3}`
