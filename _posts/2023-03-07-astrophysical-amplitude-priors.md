---
layout: distill
title: Astrophysical Amplitude Priors
description: Coming up with priors for how many gravitational waves we should expect to see at of a given amplitude
date: 2023-03-07

authors:
  - name: Asad Hussain
    affiliations:
      name: UT Austin
toc:
  - name: Event position distribution
  - name: Event Amplitude distribution at source
  - name: Amplitude at Detector
  - name: Event Amplitude Ratio
---

# Astrophysical Prior Analysis

Let's try and set up the distribution for the prior on the ringdown amplitude at the detector. We will do so by considering the distribution of events in space and put some assumptions on the distribution on the source amplitude. 

### Event position distribution

What we really want is that we have space with a uniform scattering of black hole collisions. We will consider the position to be uniform inside a 3-D ball $\mathcal{B}_L$.


$$
\vec{\begin{bmatrix}\textrm{Position of}\\\textrm{given event}\end{bmatrix}} = \vec{x} = \lim_{L\to\infty} \vec{U}_{\mathcal{B}_{L}}
$$


In polar coordinates this transforms as:


$$
\mathcal{P} = dx\wedge dy\wedge dz = r^2 \sin \theta dr\wedge d\theta \wedge d\phi = d(\frac{r^3}{3})\wedge d^2\Omega
$$


Which gives us that the $r^3$ random variable is uniform. Hence:


$$
\vec{\begin{bmatrix}\textrm{Position of}\\\textrm{given event}\end{bmatrix}} = [r^3 \sim U_{[0,L^3]}, \theta \sim U_{[-\pi,\pi]}, \phi \sim U_{[0,2\pi]}]
$$



### Event amplitude distribution at the source

Let us assume that each event choses it's amplitude completely uniformly. Each collision can have ANY amplitude from 0 to some big number like $A_{\max}$. 


$$
\begin{bmatrix}\textrm{Amplitude of a given}\\\textrm{event at the source}\end{bmatrix} = A_0 \sim U_{[0,A_{\max}]}
$$


Now ofcourse, we can make this amplitude depend on the masses, spins and other variables intrinsic of the merger event. However, since we're constructing a prior, we will just leave it as independent and uninformative. 

### Amplitude at Detector

Using the amplitude distribution of the events at source, and the event position distribution we can find the Amplitude distribution at the detector. We know that the amplitude of gravitational wave event falls off as $1/r$. Hence:


$$
A_{\textrm{det}} = \frac{A_{0}}{r} = \frac{A_{0}}{|\vec{x}|}
$$




$$
A_{det}^2 \propto \frac{A_{0}^2}{r^2}\\
\textrm{with }r^3 \sim  U_{[0,L^3]} \textrm{ and } A_0 \sim U_{[0,A_{max}]}
$$



Now we can compute the result here and find that:


$$
P(A^{\textrm{det}} = a) = \frac{3}{4a_0} \begin{cases} 
      1 & a <  a_0 \\
      (\frac{a}{a_0})^{-4} & a \geq a_0
   \end{cases}
   \\
   \textrm{where } a_0 = \frac{A_{\max}}{L}
$$


Which we can plot for specific cases.  For $A_{\max} = 10,000$ and $L = 10,000$ (measured in units of some reference distance where we detect $A_0$ for each event) we get:

{% include figure.html path="assets/img/SNR-distribution-5121189.svg" class="img-fluid rounded z-depth-1" zoomable=true %}

In most astrophysical cases, the amplitudes are small enough, and the universe large enough that we are in the regime where $p(\rho) \propto \rho^{-4}$

### Event amplitude ratio

We can allow the amplitude ratio to be any number between 0 and 2. This amplitude ratio can and does change the calculation of the SNR. We will set this ratio to be uniform for now:


$$
\alpha \sim U_{[0,2]}
$$


The SNR depends on the detector amplitude as:
$$
\begin{align}
\rho^2 &= \langle h_0| h_0 \rangle + 2 \alpha \langle h_0| h_1 \rangle + \alpha^2 \langle h_1| h_1 \rangle
\end{align}
$$




$$
\rho^2 \propto A_{\textrm{det}}^2(C_0 + C_1\alpha + C_2 \alpha^2)
$$


In general the constants above depend on the polarization parameters and frequencies of the two modes, as well as the covariance matrix of the noise used to do the inner product:


$$
C_i = C_i\bigg(\begin{bmatrix}\epsilon_1 \\ \epsilon_2\end{bmatrix}, \begin{bmatrix}\theta_1 \\ \theta_2\end{bmatrix},\begin{bmatrix}\phi_1 \\ \phi_2\end{bmatrix}, \begin{bmatrix}\omega_1 \\ \omega_2\end{bmatrix}, \begin{bmatrix}\tau_1 \\ \tau_2\end{bmatrix}, \Sigma\bigg)
$$
