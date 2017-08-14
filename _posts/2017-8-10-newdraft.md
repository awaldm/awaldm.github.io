---
layout: post
title: Signal statistics using bootstrap
draft: true
---
{% include mathjax.html %}
As someone who runs many large-ish unsteady flow simulations, I am often confronted with the question of statistical convergence and simulation runtime. For spectral analysis of temporal signals we have simple and handy criteria for the sampling rate and the signal length:
* What is the highest frequency we want to resolve? The Nyquist criterion is the way to go here, simply stating that our sampling frequency $$f_s$$ should be at least twice the desired highest resolvable frequency

* What is the lowest frequency we want to resolve? For an FFT-based analysis, the width of the frequency bins will be $$f_s/N$$, where $$N$$ is the number of samples. This also determines the lowest resolvable frequency.

Apart from this, the question whether one's simulation runtime is sufficiently long pops up regularly. In terms of frequency resolution there is no such thing as "too long" - but this, obviously, becomes a rather expensive endeavor pretty quickly. There are lots of best practices and lots of statistics publications, but it is rather telling that most of the latter focus on experimental measurement practices.

So recently I dove into these things. 

# Effective samples
Most statistics classes focus on populations and samples from these populations, with the latter typically assumed to be statistically independent. If that were fulfilled we could skip a lot of headache. In general, though, it is not; especially not in case of highly resolved CFD simulations. These results constitute time series, which are typically self-correlated to some degree. Correlated data points can be thought of as worth less than uncorrelated data points in a statistical sense, as they hold less information about the process.

Consider the standard error of the sample mean, $$\sigma / \sqrt{N}$$. Using a very high $$N$$, this converges to very low values rather quickly. A low SE 

In time series, this is not necessarily the case - if you measure some kind of physical signal it often exhibits some kind of memory, in other words correlation.

![_config.yml]({{ site.baseurl }}/images/config.png)

