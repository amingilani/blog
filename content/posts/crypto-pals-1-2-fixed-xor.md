---
title: "Crypto Pals 2 of Set 1: Fixed XOR"
date: 2021-05-09T04:11:07-04:00
draft: false
tags: ["cryptopals", "crypto"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "XOR-ing two fixed numbers"
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
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link

---

I found this a bit too easy. My first solution worked well, and I didn't learn anything new by attempting this challenge.

## The Problem

XOR the first two numbers to produce the third:

```
1c0111001f010100061a024b53535009181c
686974207468652062756c6c277320657965
746865206b696420646f6e277420706c6179
```

## The Solution

I used Python, which can execute [Bitwise XOR](https://en.wikipedia.org/wiki/Bitwise_operation#XOR) on any integer value. To leverage this ability, I converted the hexadecimal numbers to integers and XOR-ed them. I then converted the result back to a hexadecimal number again.


## The Code

```
input_1 = "1c0111001f010100061a024b53535009181c"
input_2 = "686974207468652062756c6c277320657965"
expected = "746865206b696420646f6e277420706c6179"

# convert to decimal
decimal_1 = int(input_1, 16)
decimal_2 = int(input_2, 16)


# XOR the two decimals
decimal_result = decimal_1 ^ decimal_2

# convert the to decimal
hex_result = f"{decimal_result:x}"

print(hex_result == expected)
#=> True
```