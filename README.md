# LSB-steganography-javascript
LSB(Least Significant Bit) method for steganography using javascript.

# Demo
Demo(follow step by step) - https://jsfiddle.net/norlihazmeyGhazali/quo42a2n/ - tested on .txt file

# How it works
The main important concept in steganography is hiding secret information inside image without decreased image qualitiy. This image react as a cover and at the same time, your secret data is hiding inside. You can send those image to someone, and the one who received this image will use same tools to extract/get the data back into original form.

Internally, the secret data's binary bit was used and replacing the cover image pixel's bit. The replacing occured on the Lease Significant Bit also known as LSB which remove or clear first two bits from cover image's pixel and replaced with secret data. Only first two bits were used in order to retain the quality of cover image. See below how the replacing bits occured :

The binary used here is just for an example for illustration purpose :

**Secret Data byte(a) :** `1101 0110`

**Cover image rgba(b)** : `0110 11011, 1100 0011, 1111 0011, 0000 1010`

1) Internally, the first two bits(b) for every pixel's byte was set into 0(clear), and become like this :

```javscript
 0110 11000, 1100 0000, 1111 0000, 0000 1000
         ^^         ^^         ^^         ^^
         |          |          |          |
         \          |          |          /
           \        |          |         /
             \      |          |        /
                  clear bit(set to 0)
```

2) Take 2 bits of (a) from left(right hand) to the right(left hand)

```javscript
                (right) 1101 0110 (left) - Secret Data
                
         10         01         01         11
         ||         ||         ||         ||
 0110 11000, 1100 0000, 1111 0000, 0000 1000
         ^^         ^^         ^^         ^^
         |          |          |          |
         \          |          |          /
           \        |          |         /
             \      |          |        /
                  and become like below
0110 11010, 1100 0001, 1111 0001, 0000 1011
```

Quality of cover image still acceptable unless the replacing occured at the highest nibble(bits 4-7) instead of lowest nibble(bits 0-3). 

Super Important Reminders/Notes
========================
1) Please do not select/choose .txt file containing too much data inside, as it may bloated/slow down your pc's performance as its need more resources to operate/iterate every bits/bytes for each data.
2) Select only .txt file, others may/maybe not works
3) Data extracted from image still 100% not accurated,, depends on file size and data inside.
4) Only test with chrome 57.0.2987.133. Others browser may or may not works.
5) Fork if you found it useful and want to contribute to it, ohh pleaseee.....
6) This lib still in development mode :)
