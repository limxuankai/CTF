# Flag Shop

**Challenge Type: Pwn**  

## Challenge

Yes But No has just opened our very own flag shop! In the flag shop, you can buy flags from the shop by shopping from flags in our flag shop. P.S free hats are available as part of our opening gift!

`nc nc.yes-but-no.org 10000`
## Solution 

1) Connect to the server. upon connecting you shall see this: 
```
Welcome to YBN's Flag Shop! Unfortunately due to global inflation and other political matters that affect financial stuff and whatnot, we have increased our prices by 100%.  
Luckily, we have a 50% off sale! Happy shopping!  
you have $69 dollars  
-------------------Listing-------------------
| YBN's official fake flag - $50      (1)   |
| YBN's official real flag - $100000  (2)   |
| YBN hat (opening gift) - $0         (3)   |
---------------------------------------------
[1] Buy an item!
[2] Help Menu
```
2) Click to buy their real flag to get this screen: 
```
how many of the item do you want?
```
3) Reply 0
> Explaination time: So because there is little to no input validation, you can just yoink the flag by demanding 0. 
4) Flag: YBN{Fl4G_AcqU1R3D_Th4Nk_Y0u_F0r_V151t1ng_Th3_Fl4G_Sh0P}

### P.S 

My first ever Pwn ctf problem that I solved. <br>
If you were to hexdump it, you will find a roblox video titled free giftcards <br>
Is it just me or the YBN creators like to play roblox 💀