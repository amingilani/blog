---
title: "Generating a Secure Passphrase"
date: 2022-12-24T21:05:42-05:00
draft: true 
tags: ["security", "crypto"]
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

In this short two-part guide, I'll walk you through my personal favorite
password creation mechanism using a techique called diceware. In the second
part, I'll explain why these passwords are probably significantly more secure
than your existing password. Hopefully this will keep you secure online, and if
you like it, feel free to share this with people important to you.

Passwords created by humans aren't safe. Even if you add complex rules about
the password, like using symbols, numbers, mixed case letters, the password
will still not be a random enough. There's a popular [XKCD
comic](https://xkcd.com/936/) about this.

Human unreliability in creating random passwords, and memorizing them is acknowledged by NIST, and researched
and hopefully we will eventually move to passwordless authentication.

# Part 2: How Secure Is Your New Passphrase?

In this part, we'll determine how and why this password is secure by:

1. Learning how randomness is measured as entropy;
2. Comparing the entropy of this passphrase to entropy other passwords; and
3. Determining how long it'll take for a sophisticated adversary to guess your passphrase


## Entropy As A Measure Of Randomness

How do you measure an something as abstract as randomness or chance? We
actually already have common phrases we use to concretely express the notion.
When you say something has a "one in a million chance", that's specific. That
means that there are are a million different ways something could have been,
but it went like _this_.

Each coin side of a coin have a 1 in 2 chance of facing up when it's flipped,
giving it 2 possible states. Each number on a dice has a 1 in 6 chance of
happening, and so there are 6 possibiltiies. And we can intuitively tell that
6 possible states is more random than 2 possible states, since if we flipped
a coin and rolled a die, it's less likely for the number 2 to appear on the die
than heads on a coin.

In information theory, randomness is expressed as how digits in base-2 it takes
to express the number of states, and this unit is called _bits of entropy_.
More intuitively though, we can rewrite it as the number of coinflips needed to
match the randomness of the chance occurring. This unit was defined by Claude
Shannon in 1940, and base-2 was chosen because "[i]t is practically more
useful" for "[p]arameters of engineering importance".

So, how random is the roll of a single die? We can rewrite the question and ask
how many times must I flip a coin for the resulting sequence of heads and tails
to be as random as the roll of a dice? The math behind this is not important,
but the answer is at least 2 bits of entropy.

$$ log_2 6 = \frac{log(6)}{log(2)} = 2.584 \cdots $$

## How Random Is Our Passphrase?


