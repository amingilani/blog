---
title: "Cryptopals 1 of Set 1: Hex to Base64"
date: 2021-05-09T02:08:44-04:00
draft: false
tags: ["cryptopals", "crypto"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "Converting a hexadecimal number to a base64 number"
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

Initially, I went in a completely different direction by converting to a decimal and then mapping to a base64 number, but I learned more about [Base64](https://tools.ietf.org/html/rfc3548.html)'s input scheme while solving this. Eventually I figured out the solution, it wasn't mathematical, it required learning about Base64.

## The Problem

The challenge is to map this:

```
49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d
```

To this [Base64](https://en.wikipedia.org/wiki/Base64) value:

```
SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t
```

## The Solution

The solution became clearer when I read hint at the bottom:

> Always operate on raw bytes, never on encoded strings. Only use hex and base64 for pretty-printing.

I converted the hex string into raw bytes using [`binascii`](https://docs.python.org/3/library/binascii.html) where I say the message:

> I'm killing your brain like a poisonous mushroom

Charming. I then read the `base64` library's [`encode`](https://github.com/python/cpython/blob/3.9/Lib/base64.py#L51-L62) function which seemed to be using `binascii` as well. So I used that to convert to base64, and cleaned the result by converting it to a string.

## The Code

```
import binascii

input = "49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d"
expected = "SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t"

# Convert the hex to bytes
bytes = binascii.a2b_hex(input)
print(bytes)
# => b"I'm killing your brain like a poisonous mushroom"

# Pass the bytes to base64
base64 = binascii.b2a_base64(bytes, newline=False)
print(base64)
# => b'SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t\n'

# Convert to a string
cleaned_result = base64.decode()
print(cleaned_result)
# => SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t

print(cleaned_result == expected)
# => True
```
