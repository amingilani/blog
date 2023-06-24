---
title: "Essential Equations for Amateur Radio Operators: A Handy Reference"
date: 2023-06-24T01:53:15-04:00
draft: false
tags: ["Amateur radio", "Study guide", "Equations", "Exam preparation"]
author: "Amin Shah Gilani"
showToc: true
TocOpen: true
hidemeta: false
comments: false
description: "A compendium of key equations and formulas for amateur radio operators, compiled as a study aid for the upcoming ham radio exam."
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
    URL: "https://github.com/amingilani/blog/tree/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

# Essential Equations for Amateur Radio Operators: A Handy Reference

As I prepare for my upcoming amateur radio exam, I've come across several essential equations. I decided to compile them here, to serve as a handy reference for myself and fellow ham radio enthusiasts. 

I hope these equations will serve as a useful reference as you navigate your ham radio journey. Don't hesitate to suggest any changes or additions to this guide via the link at the bottom of this post.

Notes:

1. The creation of this post makes liberal use of an artifical intelligence language model,
2. This post will be continuously updated to introduce more equations I begin to use, and
3. If there are any errors, please reach out.

## 1. Ohm's Law


Ohm's Law is fundamental in the field of electronics and finds wide application in ham radio operations. It relates the electric voltage (E), current (I), and resistance (R) in a circuit. The formula is:

$$E = I \times R$$

where:
- $E$ is the electromotive force or voltage measured in volts,
- $I$ is the current measured in amperes,
- $R$ is the resistance measured in ohms.

## 2. Power Calculation

Power in an electrical circuit can be calculated using the following formula:

$$P = I \times E = I^2 \times R = \frac{E^2}{R$$

where:
- $P$ is the power expressed in watts,
- $I$ is the current expressed in apmeres,
- $E$ is the electromotive force (voltage) expressed in volts.
- $R$ is the resistance expressed in ohms.

So whether you have the current, the electromotive force, or the resistance, you can calculate the power in an electrical circuit.

## 3. Radio Wavelength Calculation in a Medium

The wavelength of a radio wave in a vacuum is calculated using the formula:

$$\lambda = \frac{c}{f}$$

where:
- $\lambda$ is the wavelength,
- $c$ is the speed of light in a vacuum (approximately $300,000,000$ m/s),
- $f$ is the frequency.

However, when radio waves travel through a medium such as a cable, the wavelength is affected by the medium's Velocity Factor ($VF$). The Velocity Factor is the ratio of the speed of a signal in the medium to the speed of light in a vacuum.

Taking the Velocity Factor into account, the wavelength of a radio wave in a medium is given by:

$$\lambda_m = \frac{c}{f} \times  VF$$

where:
- $\lambda_m$ is the wavelength of the wave in the medium,
- $VF$ is the Velocity Factor of the medium.

Here are some common Velocity Factor values:

- Polyethylene coaxial cable: $VF = 0.66$
- Foam or air dielectric coaxial cable: $VF = 0.80 - 0.88$
- Solid dielectric twin lead: $VF = 0.82$
- Open wire line: $VF = 0.97 - 0.99$

Using these values and the above formula, you can calculate the wavelength of radio waves in various mediums.
## 4. Half-Wave Dipole Antenna Length

A half-wave dipole antenna is one of the simplest forms of antennas, and its length is determined by the wavelength of the frequency it is designed to receive or transmit. The formula for calculating the length of a half-wave dipole antenna is:

$$L = \frac{\lambda}{2}$$

where:
- $L$ is the length of the antenna,
- $\lambda$ is the wavelength.

However, if the frequency $f$ is known and the wavelength is not, the wavelength can be calculated by:

$$\lambda = \frac{VF \times c}{f}$$

Then, the length of the antenna is given by:

$$L = \frac{VF \times c}{2f}$$

This is assuming that the antenna is in free space. When an antenna is installed in a real-world environment, its effective electrical length can be affected by factors such as proximity to other objects and the antenna's height above the ground. Consequently, antennas often require some adjustment from this theoretical length for optimal operation.

Remember to use the wavelength $\lambda$ calculated considering the Velocity Factor $VF$ of the medium, as discussed in the previous section, for more accurate measurements. Some common velocity factors were also provided in the Radio Wavelength Calculation and Velocity Factor section.

## 5. Time Constants in RC and RL Circuits

The time constant of an RC (resistor-capacitor) or RL (resistor-inductor) circuit is a measure of the time required for the circuit to charge or discharge through approximately 63.2% of the difference between the initial and final values. 

For an RC circuit, the time constant ($\tau$) is calculated as:

$$\tau = R \times C$$

For an RL circuit, the time constant is given by:

$$\tau = \frac{L}{R}$$

where:
- $\tau$ is the time constant,
- $R$ is the resistance,
- $C$ is the capacitance,
- $L$ is the inductance.

## 6. Resonant Frequency of an RLC Circuit

The resonant frequency ($f_r$) of a series or parallel RLC circuit is given by:

$$f_r = \frac{1}{2\pi\sqrt{LC}}$$

where:
- $f_r$ is the resonant frequency,
- $L$ is the inductance,
- $C$ is the capacitance.

## 7. Q-factor of a Circuit

The Q-factor (or quality factor) of a resonant circuit is a dimensionless parameter that describes how under-damped an oscillator or resonator is, or equivalently, characterizes a resonator's bandwidth relative to its center frequency. There are several ways to calculate the Q-factor.

One common formula is:

$$Q = \frac{R_L}{2\pi f L}$$

where:
- $Q$ is the Q-factor,
- $f$ is the frequency,
- $L$ is the inductance,
- $R_L$ is the load resistance.

However, if you are dealing with a resonant (RLC) circuit, the Q-factor can also be calculated as:

$$Q = \frac{1}{R}\sqrt{\frac{L}{C}}$$

where:
- $R$ is the resistance,
- $L$ is the inductance,
- $C$ is the capacitance.

The first formula gives the Q-factor in terms of the load resistance, inductance, and operating frequency. This formula is commonly used when designing or analyzing RF circuits with a known load resistance and operating frequency.

The second formula calculates the Q-factor based on the inherent resistance, inductance, and capacitance of the circuit. It provides a way to calculate the Q-factor when the physical parameters of the circuit components are known.

Also, the Q-factor can be understood as the ratio of the resonant frequency to the bandwidth, represented as:

$$Q = \frac{f}{\Delta f}$$

where:
- $f$ is the resonant frequency,
- $\Delta f$ is the bandwidth at which the power drops to half its peak value.


## 8. Total Resistance

Resistance calculation in a circuit can be done differently based on whether the resistors are arranged in series or in parallel.

### 1. Resistors in Series

When resistors are connected in series, the total resistance ($R_{total}$) is the sum of the resistances of each component. This can be represented as:

$$R_{total} = R_1 + R_2 + R_3 + \ldots + R_n$$

Where $R_1, R_2, R_3, \ldots, R_n$ represent the resistances of each component.

### 2. Resistors in Parallel

For resistors connected in parallel, the reciprocal of the total resistance is equal to the sum of the reciprocals of each resistance. This is represented as:

$$\frac{1}{R_{total}} = \frac{1}{R_1} + \frac{1}{R_2} + \frac{1}{R_3} + \ldots + \frac{1}{R_n}$$

To find the total resistance, calculate the reciprocal of the right-hand side and then take the reciprocal of the result.

## 9. Total Capacitance

For capacitors, the rules are inverted compared to resistors. 

### 1. Capacitors in Series

For capacitors in series, the reciprocal of the total capacitance ($C_{total}$) is equal to the sum of the reciprocals of each capacitance:

$$\frac{1}{C_{total}} = \frac{1}{C_1} + \frac{1}{C_2} + \frac{1}{C_3} + \ldots + \frac{1}{C_n}$$

### 2. Capacitors in Parallel

When capacitors are connected in parallel, the total capacitance is the sum of the capacitances of each component:

$$C_{total} = C_1 + C_2 + C_3 + \ldots + C_n$$

Where $C_1, C_2, C_3, \ldots, C_n$ represent the capacitances of each component.
