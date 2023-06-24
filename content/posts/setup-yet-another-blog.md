---
title: "I've Set Up My Blog Yet Again"
date: 2021-05-08T22:36:03-04:00
draft: false
tags: ["meta"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "For the umpteenth time in my life, I've set up my blog."
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



<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
        src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>


# I've Set Up My Blog Yet Again

For the umpteenth time in my life, I've set up my blog. This time around, I'm going to be trying to write quick, and short nuggets as I go along my life. My future posts will be better. I'm writing this one with the singular purpose of testing whether everything on my blog works appropriately.

I've also set up MathJax so that I can do some fun things like solve a few the [cryptopals](https://cryptopals.com) challenges using my newly gained GA Tech [CS6260](https://omscs.gatech.edu/cs-6260-applied-cryptography) knowledge.  I've got to flex that I can now write $\LaTeX$ and have learned that the advantage of an adversary $\mathcal{A}$ in the [ind-cpa](https://en.wikipedia.org/wiki/Ciphertext_indistinguishability) experiment, with the oracles initialized using some symmetric encryption scheme $\mathcal{SE}$ may be expressed as:

$$\mathrm{Adv_{\mathcal{SE}}^{ind-cpa}}(\mathcal{A} ) = Pr[\mathcal{A} \Rightarrow 0 \ \mathrm{in} \operatorname {ind-cpa-0}] - Pr[\mathcal{A} \Rightarrow 0 \ \mathrm{in} \operatorname{ind-cpa-1}]$$

Where:

+ $Pr[\mathcal{A} \Rightarrow 0 \ \mathrm{in} \operatorname {ind-cpa-0}]$ is the probability of the attacker outputting 0 in experiment 0, i.e. being correct; and
+ $Pr[\mathcal{A} \Rightarrow 0 \ \mathrm{in} \operatorname {ind-cpa-1}] = 0$ is the probability of the attacker outputting 1 in experiment 1, i.e. being incorrect.

If someone happens to be reading this, please don't worry if none of that made sense, I honestly don't fully understand why the advantage is expressed the way it is to be honest. This post is just a test to check that the blog was set up correctly. 😅

Although, if you are interested, I think this may also be covered in Dan Boneh's [Online Cryptography Course](https://crypto.stanford.edu/~dabo/courses/OnlineCrypto/). I haven't taken the course, but I believe the book for the course covers it.
