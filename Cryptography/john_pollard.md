# john_pollard
Category: Crypto
Points: 500
Author: Kaden Wu
## Problem Description
Sometimes RSA [certificates](https://jupiter.challenges.picoctf.org/static/c882787a19ed5d627eea50f318d87ac5/cert) are breakable
## Writeup
We can use an RSA certificate decoder for this one:
https://certlogik.com/decoder/

After opening it and pasting in the certificate, we see:
```
Certificate:
Data:
        Version: 1 (0x0)
        Serial Number: 12345 (0x3039)
    Signature Algorithm: md2WithRSAEncryption
        Issuer:
            commonName                = PicoCTF
        Validity
            Not Before: Jul  8 07:21:18 2019 GMT
            Not After : Jun 26 17:34:38 2019 GMT
        Subject:
            commonName                = PicoCTF
            countryName               = US
            stateOrProvinceName       = PicoCTF
            localityName              = PicoCTF
            organizationName          = PicoCTF
            organizationalUnitName    = PicoCTF
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (53 bit)
                Modulus: 4966306421059967 (0x11a4d45212b17f)
                Exponent: 65537 (0x10001)
    Signature Algorithm: md2WithRSAEncryption
         07:6a:5d:61:32:c1:9e:05:bd:eb:77:f3:aa:fb:bb:83:82:eb:
         9e:a2:93:af:0c:2f:3a:e2:1a:e9:74:6b:9b:82:d8:ef:fe:1a:
         c8:b2:98:7b:16:dc:4c:d8:1e:2b:92:4c:80:78:85:7b:d3:cc:
         b7:d4:72:29:94:22:eb:bb:11:5d:b2:9a:af:7c:6b:cb:b0:2c:
         a7:91:87:ec:63:bd:22:e8:8f:dd:38:0e:a5:e1:0a:bf:35:d9:
         a4:3c:3c:7b:79:da:8e:4f:fc:ca:e2:38:67:45:a7:de:6e:a2:
         6e:71:71:47:f0:09:3e:1b:a0:12:35:15:a1:29:f1:59:25:35:
         a3:e4:2a:32:4c:c2:2e:b4:b5:3d:94:38:93:5e:78:37:ac:35:
         35:06:15:e0:d3:87:a2:d6:3b:c0:7f:45:2b:b6:97:8e:03:a8:
         d4:c9:e0:8b:68:a0:c5:45:ba:ce:9b:7e:71:23:bf:6b:db:cc:
         8e:f2:78:35:50:0c:d3:45:c9:6f:90:e4:6d:6f:c2:cc:c7:0e:
         de:fa:f7:48:9e:d0:46:a9:fe:d3:db:93:cb:9f:f3:32:70:63:
         cf:bc:d5:f2:22:c4:f3:be:f6:3f:31:75:c9:1e:70:2a:a4:8e:
         43:96:ac:33:6d:11:f3:ab:5e:bf:4b:55:8b:bf:38:38:3e:c1:
         25:9a:fd:5f
```
Since we want the 2 numbers `p` and `q`, we would naturally think of finding n. Right here in the middle, we find the modulus:
```Modulus: 4966306421059967 (0x11a4d45212b17f)```
This number isn't that big for a modulus! We can use a factorer to get the two factors, `67867967` and `73176001`. You can try inputting `picoCTF{p,q}` but it won't work, but inputting it the other way around does.
<br>Flag: `picoCTF{73176001,67867967}`
