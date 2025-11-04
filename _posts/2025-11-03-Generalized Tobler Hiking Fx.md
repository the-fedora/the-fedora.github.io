---
title: "Generalized Tobler Hiking Function"
style: post
date: 2025-11-03 19:15:00 -0600
categories: GIS cost-path hiking-equation
tags: [GIS,cost path,analysis,hiking equation,Waldo Tobler]
---
## Introduction
I wrote this note in mid-October of last year, while working through some things for a predictive model for cultural resources that I will *hopefully* publish later this year, or possibly early next year.

### Background
In 1993, [Waldo Tobler](https://en.wikipedia.org/wiki/Waldo_Tobler) published a short article with a few notes on Geographic Information Systems, including deriving a "hiking equation". This was based on data [Eduard Imhof](https://en.wikipedia.org/wiki/Eduard_Imhof) published in 1950, and is a basic data-driven description of how people move across the landscape. There are some simplifying assumptions -- e.g., you slow down on slope, whether going up or down (anisotropic movement model). But despite -- or perhaps because -- of the simplicity, it tracks very well to real-world conditions. To wit: the model predicts a speed of 5km/h on flat trail. This is just a bit more than 3mph, which is a rule of thumb we used for planning hikes in Boy Scouts.

The [paper](http://escholarship.org/uc/item/05r820mz.pdf) also gives general scaling rules for walking off-trail, or traveling on horseback. What I wanted, however, was something more generic: a normalized 0-1 scale that I could use as a percentage, or scale to any maximum speed I needed. This is that.

***14 October 2024***

*This note has been lightly edited from my original notes and derivation, for spelling, formatting, and clarity.*

## A Note On Generalizing Tobler's (1993) "Hiking Function"
Tobler's original function was presented in unpretentious pseudo-code, and given the simplicity of the function was perfectly readable that way:

`W = 6 exp (-3.5 * abs(S + 0.05))`

where `W` is *walking velocity*; and `S` is slope in form "rise over run", or `tan(`$\theta$`)`, where $\theta$ is slope angle in degrees.

This results in a flat-ground hiking speed of `~5km/h`, for hiking on-trail. Tobler off-trail speed may be approximated by taking $$\frac{3}{5}$$ of the results, and horse travel may be similarly approximated by taking $$\frac{5}{4}$$ of the calculated speed.

Speed here is in `km/h`, but slope is effectively dimensionless.

So, the goal for this note is to generalize this function so that we simply have a decimal range of `0:1`. This could be approximated by dividing by 5, but as noted above, the original function only results in *about* 5km/h for flat ground. The approximation may well be good enough... but less fun.

So: we will normalize Tobler's notation somewhat, and reduce the function as a fraction with the denominator set as the `Right Hand Side (RHS)` of the original function, replacing `S` with $0 \div 1 = 0$. Thus:

$$v_p = \frac{6 \times e^{-3.5 \times |m + 0.05|}}{6 \times e^{-3.5 \times |0 + 0.05|}}$$

Note that we are using $v_p$ for "percent velocity", $m$ for slope, and have written out the natural exponentiation in standard format instead of Tobler's pseudo-code. From here:

$$(1) : v_p = \frac{6e^{-3.5|m + 0.05|}}{6e^{-3.5|0 + 0.05|}},$$

$$(2) : v_p = \frac{6e^{-3.5|m + 0.05|}}{6e^{-0.175}},$$

$$(3) : v_p = \frac{e^{-3.5|m + 0.05|}}{e^{-0.175}},$$

$$(4) : v_p = \frac{e^{-|3.5m + 3.5*0.05|}}{e^{-0.175}}$$

Thus, the equation for grade slopes (e.g. $\frac{dy}{dx}$ or $\frac{\% slope}{100}$):

$$(5a) : v_p = \frac{e^{-|3.5m + 0.175|}}{e^{-0.175}},$$

and for slopes in degrees:

$$(5b) : v_p = \frac{e^{-|3.5 tan \theta + 0.175|}}{e^{-0.175}}.$$

This can be translated back into pseudo-code as:

$$(5c) :$$ `vp = exp(-1*abs(3.5 * m + 0.175)) / exp(-0.175)`

or, for slopes given in degrees:

$$(5d) :$$ `vp = exp(-1 * abs(3.5 * tan(deg) + 0.175)) / exp(-0.175)`

if `tan()` expects radians (as in `R`), the following form may be used:

$$(5e) :$$ `vp = exp(-1 * abs(3.5 * tan(deg / 360 * 2 * pi) + 0.175)) / exp(-0.175)`

This was tested in QGIS. The built-in map calculator had issues, and I did not find a root cause but it may be a degree/radian mismatch. Instead, I switched to `White Box Tools` through `White Box Workflows (WBW)` plugin, using `WBW` built-in variables for $e$ and $\pi$. Slope raster was calculated in degrees:

$$(5f) :$$ `(e()^(-1 * abs(3.5 * tan('MAP'/360 *2 *pi()) + 0.175))) / (e()^(-0.175))`
## Conclusions and thoughts
This derivation is limited by computational accuracy for obvious reasons, but this should not pose a major issue in normal use. For example, on my relatively-recent Framework 13, a sample calculation of $(2)$ and $(5e)$ using `0:90`° in `R` has a mean absolute difference between $(2)$ and $(5e)$ of about $2.7\times 10^{-17}$. Given that Tobler's original work is derived from experimental observations of inherently "noisy" data (e.g., human actions), this amount of error seems reasonable.
