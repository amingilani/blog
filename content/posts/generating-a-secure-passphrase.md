---
title: "Secure Passwords 1: Making a Good Password"
date: 2022-12-24T21:05:42-05:00
draft: false
tags: ["security", "crypto", "authentication"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "This tutorial walks you through creating a good password. Humans are bad at making and remembering good passwords. A good password requires randomness which we incorporate in this process."
disableHLJS: false # to disable highlightjs
disableShare: false
hideSummary: true
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "/images/generating-a-secure-passphrase/dice-paper-pen.png" # image path/url
    alt: "<alt text>"
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
editPost:
    URL: "https://github.com/amingilani/tree/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---


I often have to explain password security to people and found that using
phrases like "secure passphrase" and "high entropy" is daunting to the average
person. I hope this two-part series sheds light on what it takes to create a
good password and why some passwords are better than other.


## Intro: Human-Generated Passwords Are Not Secure

Passwords created by humans aren't safe. Even if you add complex rules about
the password, like using symbols, numbers, and mixed case letters, the password
will still not be random enough. There's a popular [XKCD
comic](https://xkcd.com/936/) about this.

Human unreliability in creating and memorizing secure passwords is acknowledged
by NIST[^1]. The passwords we produce are trivially insecure and often
incorporate personal information easily accessible to an adversary. However, it
is possible to create memorable and secure passwords.

In this first part of a two-part guide, I'll walk you through my personal
favorite password creation mechanism using a technique called diceware. You
will create a password that is easier to memorize and more secure than this
one: `SV8uFHnWU7eoe23uRc9Nq4oQrw`.

In the second part, I'll explain why these passwords mathematically more secure
than your existing password, explain how attackers try to compromise your
passwords, and why a strong password keeps you safe. Hopefully this will keep
you secure online, and if you like it, feel free to share this with people
important to you.


## Creating A Secure Password

To create a truly randomly generated password, we need three things:

1. An incredibly random number
1. A way to express that number as a password
1. A process to commit that password to memory

![A cartoon kitten playing with 5 dice](/images/generating-a-secure-passphrase/kitten-playing-dice.png)

To create the randomness we'll use dice. You can use a single die, but it's
better to use 5 dice. Then we'll use a table to look up the word corresponding
to our dice rolls. Finally, we'll type the password repeatedly over the next
two weeks until typing it becomes muscle memory.

### Step 1: Generating A Random Number with Dice

Generate a five-digit number by rolling the dice. You can either roll one die
five times or roll all five dice at the same time and read the values from
left to right. Repeat this twelve times by writing each number below the first.

As an example, here is a list that I generated:

> 1. 45132
> 1. 22335
> 1. 53645
> 1. 14214
> 1. 63663
> 1. 44212
> 1. 63642
> 1. 33345
> 1. 33242
> 1. 43625
> 1. 65255
> 1. 44221

### Step 2: Turn The Random Numbers into Words

We now need a table that can take those numbers and turn them into words. There
are many ways to accomplish this, but my preferred way is to use
[this](http://archive.today/fvX6l) EFF-provided wordlist. For each number you
generated in the previous step, look up the corresponding word, and write it
next to the number.

Continuing my example, here are my words:

> 1. 45132 -- pouring
> 1. 22335 -- deceptive
> 1. 53645 -- shame
> 1. 14214 -- broadly
> 1. 63663 -- unglue
> 1. 44212 -- pelt
> 1. 63642 -- unfixable
> 1. 33345 -- handling
> 1. 33242 -- habitat
> 1. 43625 -- passably
> 1. 65255 -- upswing
> 1. 44221 -- pendant

Congratulations, you now have a randomly generated password that was done
completely without the aid of a computer. At this point, you're likely
the only person in the world to see this unique combination of words.

### Step 3: Commit The Words To Memory

I find the easiest way to memorize your password is by typing it repeatedly.
This was the same way we used to memorize phone numbers when we had landlines.
I have yet to see this method fail, even for very forgetful people.

Rewrite your password as three groups of 4 words on a small slip of paper.
Here's how mine would look:

> pouring deceptive shame broadly
> unglue pelt unfixable handling
> habitat passably upswing pendant

Set this as the primary password for whatever you're using it for--like a
password manager--and, most importantly, configure it so it should **prompt you
for your password every time you need to use it**. This ensures you write this
phrase multiple times.

Since you've grouped the words so conveniently, you'll only need to glance at
your paper 3 times to write the password. By the third week, you will no
longer need the piece of paper and you should burn it. The password now only
exists in your head.


## Conclusion

You've just learned how to create and memorize a very strong password. It is a
bit long, and since it's more than a word, you can call it a passphrase. If you
use this password with only a single service (like a password manager), you can
continue using this password indefinitely--until you suspect it has been
compromised.

Some facts about your passphrase:

* With a word list of 7776 words, and 12 words, your password is 1 in
  48,873,677,980,689,257,489,322,752,273,774,603,865,660,850,176. That is over
  155 bits of entropy (we'll cover what that means in the next part).
* It is at least 3 times more secure than this password with just 152 bits of
  entropy: `SV8uFHnWU7eoe23uRc9Nq4oQrw`.
* As of 2022, if the largest cracking network on the planet[^2] tried to attack
  your password:
  * It will take 2.1 E26 E38 years to do it.
  * Since the universe is only (lol) 13.7 E9 years old. It would take 15.6
    quadrillion times longer than the age of the universe to crack your
    password.


In the next part, we'll dive into the maths behind how to calculate these bits
of entropy and how your passphrase compares to others. We'll also understand
why how passwords are stored on a website's servers and how higher entropy
makes you more secure. Additionally, we'll discuss some common techniques
attackers use to compromise your passwords and how a password like this renders
them impotent.



[^1]: NIST is the US National Institute of Standards and Technology. Its
    [Publication SP 800-63B -- Authentication and Lifecycle
    Management](https://doi.org/10.6028/NIST.SP.800-63-3) from its Digital
    Identity Guidelines are technical requirements for federal agencies
    implementing digital identity services. SP 800-63B § Appendix A notes:
    "Humans [...] have only a limited ability to memorize complex, arbitrary
    secrets, so they often choose passwords that can be easily guessed. [...]
    Online services have introduced rules in an effort to increase the
    complexity of these memorized secrets." e.g. "composition rules, which
    require the user to choose passwords constructed using a mix of character
    types, such as at least one digit, uppercase letter, and symbol. However,
    analyses of breached password databases reveal that the benefit of such
    rules is not nearly as significant as initially thought, although the
    impact on usability and memorability is severe."
[^2]: "largest cracking network" is one way to describe the bitcoin mining
    network. It's a distributed system rewarded to guess a key that
    unlocks the next bitcoin block. The peak hash rate as of writing this
    article was ~325.11 EH/s in October 2022 according to
    [Bitcoin.com](https://news.bitcoin.com/3-bitcoin-mining-records-set-in-october-btc-hash-price-taps-lifetime-low-while-hashrate-and-difficulty-surged/).
