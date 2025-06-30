# [Rotation - Medium](https://play.picoctf.org/practice/challenge/373?category=2&page=1)

## Main Problem

This challenge provides an encrypted text, which is the flag itself.  
The Flag - **xqkwKBN{z0bib1wv_l3kzgxb3l_429in00n}**

## Thoughts

Since the challenge only provided a string of text, I assumed that it was using **Caesar Cipher**, a technique that shifts each letter a number of places down the alphabetical order.

## Solving Steps

I utilized an online decipher tool to decrypt this Caesar Cipher, [dCode](https://www.dcode.fr/caesar-cipher), and pasted the encrypted text inside to brute-force the answer by trying all 25 possible shifts.

This was a Caesar Cipher with a **shift of -8 (or +18)**.

**Note**: In Caesar ciphers, shifting 8 positions backward is the same as shifting 18 forward, since the English alphabet has 26 letters and the shifts wrap around in a circle.

## Answer

    picoCTF{r0tat1on_d3crypt3d_429af00f}

## Reflection

This was an extremely easy solve and I plan to write a simple Python script to decode Caesar Ciphers.
