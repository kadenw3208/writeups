# ReadMyCert
Category: Crypto
Points: 100
Author: Kaden Wu
## Problem Description
How about we take you on an adventure on exploring certificate signing requestsTake a look at this CSR file  [here](https://artifacts.picoctf.net/c/422/readmycert.csr).
## Writeup
Once you open up the CSR certificate, you can see this:
```
-----BEGIN CERTIFICATE REQUEST-----
MIICpzCCAY8CAQAwPDEmMCQGA1UEAwwdcGljb0NURntyZWFkX215Y2VydF8zNzNi
NGFiMH0xEjAQBgNVBCkMCWN0ZlBsYXllcjCCASIwDQYJKoZIhvcNAQEBBQADggEP
ADCCAQoCggEBAKr+AToJg/TVTvfd9XzYR0gC5TOXa2+T24gjE8n7SHqynuo0Zlfy
oCqZHkxLha4QZszow4M+klP9fe1hy90LAU2enQGELrF3OF5SbNIVnPq97qrSHNI7
D9faAdsBqvezCto1MuMrRD35gwhQPga3WobkMdbJdDwuBpem/Tl3ko3Y9sxq2nAF
cmMNPj40GLtCfW55O8Awn2uN5gGZe+Nw2ArU9AYFidPtFZjBovHv7BVJz5XlhRhu
oiBALZES9kgfOyiwZrcJYZCJh9cJz3d+n2roMyAYMM/VZIjl0aZqSdOPeGYzs3GP
p/jFku8KNBn+mjyyw0H1vRnrK1hkNKXrXOcCAwEAAaAmMCQGCSqGSIb3DQEJDjEX
MBUwEwYDVR0lBAwwCgYIKwYBBQUHAwIwDQYJKoZIhvcNAQELBQADggEBAG0c6ed5
a5zHU5IeI1KBvhGa+zGlrbm4lGQnGoI8wwlr6VN6v07/BGpwWfhjJatAOQ3txT5O
xDrM5A8caxpgGUXmat+C/9XCSQgRA+JckSk3rd6Wz7rYRuKsnycHzVIwyvIgSdjM
5/RKRdYHyFqYHPo9Tf1fThbV0tyQ+kr0tmsO6ZuaKgyDSxtky4U51XzSByKygHOT
Oi+VkzWvn74aOgbelBFMz+3vxaRHW85pe93jN6Gvc+HwYzUFja/SZXaN95sNRhcq
20SbOmg4r2pHUg0Lfs/0EHqDSg6JtKItqZmQUNhUQ7jmL6PtUpQQlkwlfMmEijRn
vlIEqBAkSbo63XQ=
-----END CERTIFICATE REQUEST-----
```
The stuff in the middle looks like base64, so we can use a decoder like base64decode.org.
```
00�0<1&0$UpicoCTF{read_mycert_373b4ab0}10U)	ctfPlayer0"0
	*H
��0
�:	N|GH3koۈ#Hz4fW*LKfÃ>S}aM.w8^Rl;
52+D=P>Z1t<.9wjprc
>>4B}ny;0k{p
Iϕn @-H;(f	a	w~j3 0dѦjIӏxf3qŒ
4<A+Xd4\�&0$	*H
	100U%0
+0
	*H
��mykS#R1d'<	kSzNjpYc%@9
>N:k`Ej߂I\)7ޖϺF⬟'R0 IJEZ=M_NܐJk雚*Kd˅9|"s:/5:ޔLŤG[i{7sc5ev
F*D:h8jGR
~zJ-PTC/RL%|Ʉ4gR$I:t
```
The result isn't as good as we wanted it to be, but in the very first line we can see a flag.
`picoCTF{read_mycert_373b4ab0}`
