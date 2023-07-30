# Packets Primer
Category: Forensics
Points: 100
## Problem Description
Download the packet capture file and use packet analysis software to find the flag.

-   [Download packet capture](https://artifacts.picoctf.net/c/195/network-dump.flag.pcap)
## Writeup
When we open up the file, we get a `.pcap` file. To read this, we can use a tool like [WireShark](https://www.wireshark.org/download.html). After that, we can follow one of the tcp streams to get the flag.
<br> `picoCTF{p4ck37_5h4rk_b9d53765}`
