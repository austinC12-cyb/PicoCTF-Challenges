# [Transformation - Easy](https://play.picoctf.org/practice/challenge/104?category=3&page=1)

## Challenge Description

I wonder what this really is... [enc](https://mercury.picoctf.net/static/0d3145dafdc4fbcf01891912eb6c0968/enc) ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])

## Challenge Overview

Given a file with the most random combination of chinese words, and google translate can't help you here...

## Provided Resources / Clues

- The Encoded String

        灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弲㘶㠴挲ぽ

- The Encoding Algorithm
  ```python
  ''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
  ```

## Assumptions

- Yes, I really tried Google Translate, it said something about crocodiles... NOT HELPFUL
- This is Python Bit Manipulation techniques which I was not familiar with, so I needed some ChatGPT magic

## Solving Steps

1.  Figure out the **reverse function** for the encoding algorithm given, which is
    ```python
    "".join([chr(ord(c) >> 8) + chr(ord(c) & 0xFF) for c in encoded])
    ```
2.  Place the given encoded string and run it in the function like shown

    ```python
    encoded = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸弲㘶㠴挲ぽ"
    flag = "".join([chr(ord(c) >> 8) + chr(ord(c) & 0xFF) for c in encoded])

    print(flag)
    ```

## Answer

    picoCTF{16_bits_inst34d_of_8_26684c20}

## Resources Used

- ChatGPT helped me figure out the reverse function

## Lessons Learnt

- A **Code Point** is a numerical value that represents an abstract character within a character encoding system
- Python `chr()` function takes an _integer_ as an argument and returns the string representing a character at that code point, the valid range for the argument is from 0 through 1,114,111
- Python `ord()` function takes string argument of a single Unicode character and return its integer Unicode code point value
- `<< 8` in Python represents **shifting 8 bits to the left side**, the higher 8 bits of the 16 bit character in this case working with Unicode. **Commonly used for packing two 8 bit characters into a single Unicode character**. `>> 8` on the other hand does the opposite and shifts the higher 8 bits to the lower end in a character.
- `& 0xFF` works hand in hand with `<<`, it **masks the lower 8 bits**, allowing users to **extract** the value of the lower 8 bits.
- Weird chinese characters might indicate we are working with Unicode characters.

## Reflection

Reverse Engineering requires a good grip on **Bit Manipulation** and also some familiarity with various programming languages. I will work more on my Python skills
