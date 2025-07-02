# [interencdec - Easy](https://play.picoctf.org/practice/challenge/418?category=2&page=1)

## Challenge Description

Can you get the real meaning from this file.
Download the file [here](https://artifacts.picoctf.net/c_titan/111/enc_flag).

## Challenge Overview

This challenge gives a file with no extensions, only containing a string which looks like a Base64 encoded string. With no other clue other than Caesar and Base64 tagged on the question.

## Provided Resources / Clues
- The Encoded String  

        YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==
- Tags (Base64, Caesar)
- Challenge Name (Interencdec) - possibly meaning there are multiple layers of encoding algorithms

## Assumptions

- At first glance, my first suspicion was the file name extensions, i have tried renaming it into various file types to see if any clues were hidden within, including txt, py, png, jpg...
- After decoding with Base64 for the first time, I was so confused and brainfreezed by the single quotes being present in the decoded string, which costed me alot of time

## Solving Steps

1. Decode the original string with **Base64 algorithm**, you will get  

        b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='
2. Remove the `b'` and `'` from the beginning and ending of the string
3. Then decode the string again with **Base64 algorithm**, resulting in  

        wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
    which matches the format of the flags `picoCTF{...}`
4. Use **Caesar Cipher** with a shift of **19**, or **-7**, getting the final answer!

## Answer

    picoCTF{caesar_d3cr9pt3d_890d2379}

## Resources Used

- [Hash Type Identifier](https://hashes.com/en/tools/hash_identifier) - To identify what type of hash or encoding the flag is encrypted with
- [CyberChef](https://gchq.github.io/CyberChef/#input=ZDNCcWRrcEJUWHRxYUd4NmFIbGZhek5xZVRsM1lUTnJYemc1TUdzeU16YzVmUT09Cg) - To try various combinations of decoding algorithms

## Lessons Learnt
- Base64 encoded strings uses `=` as padding, to fit the required character lengths of the algorithm, which are multiples of 4
- The string with `b''` is actually a *Python byte object*, which usually happens when a user encodes a string using Python, Python prints it like `b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='`
- Removal of characters does not always cause loss of data, specifically in this case we needed to remove the single quotes, which are only used as wrappers around the actual content that we are trying to decode, so don't be afraid to try

## Reflection

This challenge was not entirely 'Easy' , as people that did not acknowledge the Python byte string format might get very confused about the decoded string format. So, the wider our knowledge base the faster and better we get to solve complex problems.
