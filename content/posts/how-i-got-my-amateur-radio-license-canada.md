---
title: "How I Got My Amateur Radio License in Canada"
date: 2021-10-27T05:36:03-04:00
draft: false
tags: ["amateur radio"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: false
hidemeta: false
comments: false
description: "I’ll detail the process I followed, how I studied, found an examiner, and chose my callsign."
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
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---



<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
        src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>


# How I Got My Amateur Radio License in Canada

I've wanted to get a license since I was a child, but back then I couldn't find any information on the process for Pakistan. I started seriously trying to get licensed in 2018, when I was much older. However, after my Pakistani amateur radio license application was denied, I decided to get licensed where I was then living, in Canada.

Here, I'll detail the process I followed, everything I did, what worked, and what didn't work. Hopefully, this will help someone else out as well. I initially joined an online [Radio Amateurs of Canada](https://www.rac.ca/) (RAC) class, and even bought a book, but never got around to finishing it. I ended up getting licensed after 15 hours of intense study overnight. I don't recommend it because I used more caffeine than is healthy. However, I scored 89% on my exam and passed Basic with Honors, and chose a memorable callsign.

## Joining an Online Class and Buying a Book

I joined the online [RAC basic course](https://www.rac.ca/amateur-radio-courses/) taught by Al Penney (VO1NO) from the [Annapolis Valley Amateur Radio Club (AVARC)](https://avarc.ca/) of Nova Scotia. The course is incredibly well taught, and I'm glad I joined it. I could ask all questions I wanted, and Al answered these patiently. The course material's slides were published on the AVARC website, and were instrumental in getting me licensed. At times the course was too fast-paced for me, but the companion book was always helpful then.

The companion book for the course was the Canadian Amateur Radio Basic Qualification Study Guide, which I bought from [Coax Publications](https://www.coaxpublications.ca/). This book explains all the material in simple language. There were plenty of topics I wasn't fully sure about, but the book explained them to me. It is a wonderful reference for the course material, and I plan on keeping mine for a long time.

However, I don't think you need either of these unless you need the additional help. Personally, I couldn't finish the course with work, and studying for my master's degree. I could have done without them, but I'm still happy to have explored this route.

## Intense Self-study Before my Exam

It was a year later when I decided to pick up studying for my exam again. By that time, I'd mostly forgotten the material. I needed a way to revise the material, and a quickly learn the topics I hadn't yet read.

I found the [Cold Lake Amateur Radio Society](https://clares.ca) website and study guide, and it was perfect for me. The lessons are freely available. The lessons teach about a topic, and immediately ask you related questions from the test bank! This was the fastest method to pick up new topics. I then went through the questions alone for the older chapters and, if needed, revised the material I'd forgotten.

However, a small fraction of the time, the lessons weren't complete. I felt like some topics were never covered before they quizzed me, but I didn't let that deter me. If I scored less than 80% on any topic, I'd revise it using the [AVARC slides](https://avarc.ca/index.php/online-basic-course/).

This combination made me happy with my preparation.

## Using Practice Tests to Ensure I'd Pass with Honors

After I thought I'd prepared, I started trying the official Innovation, Science and Economics Development Canada (ISED) [practice exam generator](https://www.ic.gc.ca/eic/site/025.nsf/eng/h_00040.html). I wanted to practice for the actual exam, and work out which topics I needed to study more closely. I was surprised when I barely passed with Honors on my first attempt.

![My first attempt at the amateur radio practice exam](/images/how-I-got-my-amateur-radio-license-canada/first-practice.png)

There was still room for improvement though, since I scored under 80% on three topics. I used the AVARC slides again to revise these topics before I attempted the exam again.

![My first attempt at the amateur radio practice exam](/images/how-I-got-my-amateur-radio-license-canada/second-practice.png)

Upon my second attempt, I'd gotten much better and happened to score less in a previously well-scored topic. I decided to revise one last time for my exam.

## Scheduling and Giving My Exam

In reality, I scheduled my exam before I started my self-study to give myself a deadline. I used the [accredited examiner search](https://www.ic.gc.ca/eic/site/025.nsf/eng/h_00003.html) on the ISED website to locate someone in the same city. I found Basil Burgess (VE3JEB), and emailed him. He administered my exam over Zoom. I loved the online exam, since it allowed me to study until the last minute.

The exam lasted a little over an hour, and I scored a neat 89%. Basil was kind enough to revisit the questions I got wrong, and explain why they were incorrect. With that he entered my score and I got an email from ISED. The email let me setup my account, displayed my score, and helped me choose my callsign.

![My score for the final exam](/images/how-I-got-my-amateur-radio-license-canada/final-exam-score.png)

## Choosing a Callsign

I wanted a somewhat memorable call-sign suffix. All the two-letter suffixes were unavailable so I was left with the three-letter suffixes.

To work out the right callsign, I filtered all the available callsigns that resembled three-letter English words. To do this I placed all the available callsigns on the ISED website in a line-separate file called `callsigns.txt`. I found and placed several 3-letter words in a line-separated file named `words.txt`. I filtered them out using the script below:

```python
# Tested using Python 3.9

callsigns = [line.strip() for line in open("callsigns.txt", "r")]
words = [line.strip() for line in open("words.txt", "r")]

wordsigns = (
        callsign
        for callsign in callsigns
        if callsign[-3:].lower() in words
        )

with open("wordsigns.txt", "w") as wordsigns_file:
    for item in wordsigns:
        wordsigns_file.write(f"{item}\n")
```

I was left with a file called `wordsigns.txt` from which I chose VE3HMM on suggestion from my friend Badar Jamal (AP2BDR). I also created a script that runs every hour, checking for 2-letter suffixes on the ISED website.

## Getting My License in the Mail

I received my certificate on the 10th business from when I passed my exam. I used it to sign up for EchoLink and DMR, immediately. The certificate is printed on paper. There was also a second smaller pocket-sized certificate, also printed on paper. I can probably cut out and carry the smaller version in my wallet.

![The full-sized amateur radio certifcate](/images/how-I-got-my-amateur-radio-license-canada/redacted-cert.jpg)

![The smaller pocket-size certificate](/images/how-I-got-my-amateur-radio-license-canada/redacted-wallet-cert.jpg)

Just as VE3JEB informed me, I didn't need to wait until my certificate arrived to begin transmitting. I started transmitting the moment the my named showed up in the [amateur search](https://apc-cap.ic.gc.ca/pls/apc_anon/query_amat_cs$.startup) on the ISED website. This only took a few hours.

![My name in the amateur search](/images/how-I-got-my-amateur-radio-license-canada/amateur-search.png)

## Closing Thoughts

I recommend getting licensed. If not for the ability to operate a radio station, then definitely for everything you get to learn. I'd never thought I'd be able to look at a random antenna and work out what frequency it was built for, as well as its radiation pattern. Nor did I imagine that I'd know the inputs of a product detector are the outputs of the beat frequency oscillator, and an intermediary frequency amplifier.

Since the day of my test, I've been browsing repeaters, and preparing to upgrade to an Advanced operator so that I can finally perform a moon-bounce. I've made contact with plenty of local operators, and even used a local echolink repeater to patch a repeater in Pakistan. If you get certified, shoot me an email <a href="mailto:hamradio@gilani.me">here</a>, and maybe we can hang out on the air sometime.

73

VE3HMM