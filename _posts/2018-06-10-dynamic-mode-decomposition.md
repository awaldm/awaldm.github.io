---
layout: post
title: Dynamic Mode Decomposition
date: 2018-06-10 11:12:00-0400
description: DMD overview
tags: modal fluids
categories: methods
---
Dynamic mode decomposition (DMD) has been all the rage among modal analysis methods in fluid dynamics for years now. I have been using both it and proper orthogonal decomposition (POD), as they are really useful tools for the analysis of unsteady turbulent wake flows. DMD hase spawned a huge number of flavors and different approaches. The basic variant is centered around obtaining a singular value decomposition of the dataset $$X$$, which consists of $M$ spatial points and $N$ temporal snapshots:

\begin{equation}
X = U \Sigma W
\end{equation}

$$U$$, $$\Sigma$$ and $$W$$ are used to perform some matrix gymnastics later, at the end of which we obtain a representation for the low order linear model of the system's dynamics. The system here being the evolution of the flow field from time $$t_0$$ to $$t_1$$ and so on. The complex eigenvalues $$\mu_i$$ and eigenvectors $$y_i$$ of this representation can be converted to real-values eigenvalues:

\begin{equation}
\lambda_i = log(\mu_i) / \Delta t,
\end{equation}

which are a convenient way to obtain a modal spectrum of the decomposition. Each mode $$i$$ has a corresponding eigenvalue and an eigenvector. The mode shapes can be obtained via

\begin{equation}
\Phi_i = U y_i,
\end{equation}

There is a lot of literature out there describing this in more detail. The above symbols are simply necessary to communicate what we are talking about.

What's cool about this is that we obtain a very informative decomposition of flow features. Consider a transonic airfoil in 2D buffet conditions, with a shock moving upstream and downstream with intermittent separation. This is a whole area of research in and of itself, but the main gist is that we have a (relatively) slowly oscillating shock and a turbulent separation downstream. The shock has a low frequency compared to the turbulent flow in the separated region.
