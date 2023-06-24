---
title: "Crypto Pals 3 of Set 1: Single Byte Cipher"
date: 2021-05-09T22:14:44-04:00
draft: false
tags: ["cryptopals", "crypto"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "Solving the cryptopals single byte cipher challenge"
disableHLJS: false # to disable highlightjs
disableShare: false
hideSummary: true
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/amingilani/tree/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

This problem is where the tediousness took off. I've spent about 5 hours on this. While I understood some of the hints, everything took a while to get right, especially when I started making assumptions. I used CyberChef to work out the solution manually, and so I don't know if that's considered cheating, and my filteration is a bit weak. I hope it won't come back to bite me in the future challenges.

## The Problem

A message has been XOR-ed against a single character, resulting in this hex encoded string:

```
1b37373331363f78151b7f2b783431333d78397828372d363c78373e783a393b3736
```

Find the message. Importantly, don't search for the string manually, let your code select the right one.

## The Solution

After reading the problem statement, I didn't know the format for the key. Questions I had were:

+ Was the key a "single character" as in the body of the problem statement?
+ Was the key a "Single-byte" as in the title of the question?

I decided to go with a single hex character for no other reason than the fact that it was what was given in the last question. However, I still got bad results. I ran the problem through [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('None')XOR_Brute_Force(1,100,0,'Standard',false,true,false,'')&input=MWIzNzM3MzMzMTM2M2Y3ODE1MWI3ZjJiNzgzNDMxMzMzZDc4Mzk3ODI4MzcyZDM2M2M3ODM3M2U3ODNhMzkzYjM3MzY) and saw the solution, but I still couldn't reproduce it in Python.

Until now, I'd been passing the single character as a decimal value, but now I decided to convert it to a hexadecimal string $k$ and try checking if a key $K$ with following three formats works. Note that $n$ is the length of the input string:

1. $K \leftarrow (\\{0\\}^{n-1} \mathbin\Vert k)$
2. $K \leftarrow (k \mathbin\Vert \\{0\\}^{n-1})$
3. $K \leftarrow \\{k\\}^{n}$

The third format worked, when I manually scanned the output and I was left with filtering for the right solution. I used two phases:

1. I filtered the bytearrays that could be converted to a native string without raising an error
2. I filtered the strings that contained common English phrases

I created the common English phrases by hand, and it isn't well done. I realize most common letter in the English language is `e`, but that kind of frequency analysis wouldn't work for this phrase because the most common letter here was an `o`.

The decoded string is `Cooking MC's like a pound of bacon`, and the key in hexadecimal is `58`

## Code


```
import binascii


input = "1b37373331363f78151b7f2b783431333d78397828372d363c78373e783a393b3736"


def xor_hex_and_char(input_hex: str, guess_character_decimal: int) -> bytes:
    """XORs a hexadecimal numbers and a single character decimal number

    Args:
        input_hex (str): an input string in hexadecimal format
        guess_character_decimal (int): a single decimal value betwen 0 and 255 inclusive

    Returns:
        bytes: a bytestring
        str: string
    """
    input_decimal = int(input_hex, 16)  # to base10

    # convert the guess character into a repeating fixed length string
    guess_character_hex = f"{guess_character_decimal:x}"  # to base16
    guess_hex = guess_character_hex.rjust(
        2, "0"
    )  # ensure it's two characters, e.g. `a` -> `0a`
    guess_hex = guess_hex * (len(input) // len(guess_hex))  # repeat until
    guess_decimal = int(guess_hex, 16)  # to base10

    result_decimal = guess_decimal ^ input_decimal  # XOR
    result_hex = f"{result_decimal:x}".rjust(len(input), "0")

    return binascii.unhexlify(result_hex), guess_character_hex


def filter_strings(possible_answers):
    """filters bytestrings for those that can be decoded into native strings"""
    sentences = []
    for (answer, key) in possible_answers:
        try:
            answer = answer.decode()
            sentences.append([answer, key])
        except UnicodeDecodeError:
            continue
    return sentences


def check_phrases(sentence):
    """checks if a sentence contains common phrases in the English language

    Returns:
        Boolean: True if it does, false if not
    """

    # A list of common phrases in the English language
    COMMON_PHRASES = [" a ", " of ", " an "]

    if any(phrase in sentence[0] for phrase in COMMON_PHRASES):
        return True
    return False


if __name__ == "__main__":
    # all the possible answers
    possible_answers = (xor_hex_and_char(input, number) for number in range(256))

    # filtered for answers that can be decoded into native strings
    filtered_answers = filter_strings(possible_answers)

    # filtered further for those that contain common English phrases
    final_answer = [answer for answer in filtered_answers if check_phrases(answer)]

    # print out the array containing the single final answer
    print(final_answer)
```


