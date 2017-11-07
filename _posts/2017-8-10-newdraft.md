---
layout: post
title: Accuracy of statistics from CFD simulations
draft: true
---
{% include mathjax.html %}
As someone who runs many large-ish unsteady flow simulations, I am often confronted with the question of statistical convergence and simulation runtime. How long do I need to run a complex turbulent simulation for? I typically want to infer something from the temporal statistics such as mean or variance, how realiable are those if I have simulated a certain physical time period? For spectral analysis of temporal signals we have simple and handy criteria for the sampling rate and the signal length:
* What is the highest frequency we want to resolve? The Nyquist criterion sets the bounds here, simply stating that our sampling frequency $$f_s$$ should be at least twice the desired highest resolvable frequency

* What is the lowest frequency we want to resolve? For an FFT-based analysis, the width of the frequency bins will be $$f_s/N$$, where $$N$$ is the number of samples. This also determines the lowest resolvable frequency.

So, in terms of frequency resolution there is no such thing as a too long simulation run. Increasing the length becomes a rather expensive endeavor pretty quickly. There are lots of best practices and quite a few publications focusing on statistics convergence, but it is rather telling that so many of the latter focus on experimental data. So I was wondering: how accurate are statistics from my high $$f_s$$, probably-too-short CFD simulations?


# Estimation of statistic accuracy
Any sample statistic from a measurement or simulation, be it mean, variance or any higher order statistic, can be considered an estimate of a population statistic. The expected value for that statistic is usually unknown, since the entirety of the population is unknown. For instance, if we are interested in a mean we take a sample of size $$N$$ and compute its artithmetic average. No matter the distribution of the population, if we take many samples of size $$N$$ their means will be normally distributed. In order to quantify the reliability of that estimate we could compute the standard error of that estimate, which is $$SE = \sigma / \sqrt{N}$$. The sample distribution will have a certain mean and standard deviation, which means we can define a confidence interval - a very useful construct in this case.

The width of the confidence interval is proportional to SE. If we want to improve the quality of our estimate we should aim to reduce SE, and with that the width of the CI. Intuitively, we could take a larger sample from the population for a larger $$N$$

# Effective samples
Most statistics classes focus on populations and samples from these populations, with the latter typically assumed to be statistically independent. If that were fulfilled we could skip a lot of headache. In general, though, it is not; especially not in case of highly resolved CFD simulations. These results constitute time series, which are typically self-correlated to some degree. Correlated data points can be thought of as worth less than uncorrelated data points in a statistical sense, as they hold less information about the process.

Consider the standard error of the sample mean, $$\sigma / \sqrt{N}$$. Using a very high $$N$$, this converges to very low values rather quickly. A low SE 

In time series, this is not necessarily the case - if you measure some kind of physical signal it often exhibits some kind of memory, in other words correlation.

![_config.yml]({{ site.baseurl }}/images/config.png)

