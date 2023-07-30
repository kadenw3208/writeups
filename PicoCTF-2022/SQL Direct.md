# SQL Direct
Category: Web Exploitation
Points: 200
## Problem Description
Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 62254 -U postgres pico`Password is  `postgres`
## Writeup
After connecting to the server, we can use \dt to show tables.
```
┌──(kali㉿kali)-[~]
└─$ psql -h saturn.picoctf.net -p 62254 -U postgres pico
Password for user postgres: 
psql (15.2 (Debian 15.2-1))
Type "help" for help.

pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner   
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)
```
We can now select all entries from flags using the command `select * from flags`.
```
pico=# select * from flags;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
```
There's our flag!
<br>`picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}`
