---
layout: left-menu
title: Periodogram
tagline: technical documentation for JDemetra+ using GitHub Pages
description: Basics
---

For any given frequency $\omega$ the sample periodogram is the sample
analog of the sample spectrum. In general, the periodogram is used to
identify the periodic components of unknown frequency in the time
series. X-13ARIMA-SEATS and TRAMO/SEATS use this tool for detecting
seasonality in raw time series and seasonally adjusted series. Apart
from this it is applied for checking randomness of the residuals from
the ARIMA model.

To define the periodogram, first consider the vector of complex
numbers[^71]:

  $$\mathbf{x} = \begin{bmatrix}      
  x_{1} \\                             
  x_{2} \\                             
  . \\                                 
  . \\                                 
  . \\                                 
  x_{n} \\                             
  \end{bmatrix} \in \mathbb{C}^{n}$$   


where $\mathbb{C}^{n}$ is the set of all column vectors with
complex-valued components.

The Fourier frequencies associated with the sample size $\text{n\ }$are
defined as a set of values $\text{\ ω}_{j} = \frac{2\pi j}{n}$,
$j = - \left\lbrack \frac{n - 1}{2} \right\rbrack,\ldots,\left\lbrack \frac{n}{2} \right\rbrack$,
${- \pi < \omega}_{j} \leq \ \pi$, $j \in F_{n}$, where
$\left\lbrack h \right\rbrack$ denotes the largest integer less than or
equal to $h$. The Fourier frequencies, which are called harmonics, are
given by integer multiples of the fundamental frequency
$\ \frac{2\pi}{n}$.

Now the $n$ vectors
${\ e}_{j} = n^{- \frac{1}{2}}\left( e^{- i\omega_{j}},\ e^{- i{2\omega}_{j}},{\ldots,e}^{- i\text{nω}_{j}} \right)^{'}$
can be defined. Vectors $e_{1},\ldots e_{n}$ are orthonormal in the
sense that:

 $${\mathbf{e}_{j}^{*}\mathbf{e}}_{k} = n^{- 1}\sum_{r = 1}^{n}e^{ir(\omega_{j} - \omega_{k})} = \left\{ \begin{matrix}   \[7.103\]
  1,\ if\ j = k \\                                                                                                         
  0,\ if\ j \neq k \\                                                                                                      
  \end{matrix} \right.\ $$                                                                                                 

where $\mathbf{e}_{j}^{*}$ denotes the row vector, which $k^{\text{th}}$
component is the complex conjugate of the $k^{\text{th}}$ component of
$\mathbf{e}_{j}$.[^72] These vectors are a basis of $F_{n}$, so that any
$\mathbf{x \in}\mathbb{C}^{n}$ can be expressed as a sum of $n$
components:

 $$\mathbf{x} = \sum_{j = - \lbrack\frac{n - 1}{2}\rbrack}^{\lbrack\frac{n}{2}\rbrack}{a_{j}\mathbf{e}_{j}}$$   \[7.104\]

where the coefficients
$a_{j} = \mathbf{e}_{j}^{*}{\mathbf{x =}n}^{- \frac{1}{2}}\sum_{t = 1}^{n}x_{t}e^{- it\omega_{j}}$
are derived from \[7.104\] by multiplying the equation on the left by
$\mathbf{e}_{j}^{*}$ and using \[7.102\].

The sequence of $\left\{ a_{j},j \in F_{n} \right\}$ is referred as a
discrete Fourier transform of $\mathbf{x}\mathbb{\in C}^{n}$ and the
periodogram $I(\omega_{j})$ of $\mathbf{x}$ at Fourier frequency
$\omega_{j} = \frac{2\pi j}{n}$ is defined as the square of the Fourier
transform $\left\{ a_{j} \right\}$ of $\mathbf{x}$:

 $${I\left( \omega_{j} \right)\mathbf{=}{\left| a_{j} \right|^{2}}_{\ } = n^{- \ 1}\left| \sum_{t = 1}^{n}x_{t}e^{- it\omega_{j}} \right|^{2}}_{\mathbf{\ }}$$   \[7.105\]

From \[7.103\] and \[7.104\] it can be shown that in fact the
periodogram decoposes the total sum of squares
$\sum_{t = 1}^{n}\left| x_{t} \right|^{2}$ into a sums of components
associated with the Fourier frequencies$\text{\ ω}_{j}$:


  $$\sum_{t = 1}^{n}\left| x_{t} \right|^{2} = \sum_{j = - \lbrack\frac{n - 1}{2}\rbrack}^{\lbrack\frac{n}{2}\rbrack}\left| a_{j} \right|^{2} = \sum_{j = - \lbrack\frac{n - 1}{2}\rbrack}^{\lbrack\frac{n}{2}\rbrack}{I\left( \omega_{j} \right)}$$   \[7.106\]

If$\ \mathbf{x\  \in}\ \mathbb{R}^{n}$, $\omega_{j}$ and
${- \omega}_{j}$ are both in
$\left( - \pi, \right.\ \left. \ \  - \pi \right\rbrack\ $and $a_{j}$ is
presented in its polar form
(i.e.$\text{\ a}_{j} = r_{j}\exp\left( i\theta_{j} \right)$), where
$r_{j}$ is the modulus of$\text{\ a}_{j}$, then \[7.104\] can be
rewritten in the form:


 $$\text{\ \ }\mathbf{x} = a_{0}\mathbf{e}_{0} + \sum_{j = 1}^{\lbrack\frac{n - 1}{2}\rbrack}{ {2^{1/2}r}_{j}{(\mathbf{c}}_{j}\cos\theta_{j}{- \mathbf{s}}_{j}\sin\theta_{j}) + a_{n/2}\mathbf{e}_{n/2}}\ $$   \[7.107\]

The orthonormal basis for $\mathbb{R}^{n}$ is
$\{\mathbf{e}_{0},\ \mathbf{c}_{1},\mathbf{s}_{1},\ldots,\mathbf{c}_{\lbrack\frac{n - 1}{2}\rbrack},\mathbf{s}_{\lbrack\frac{n - 1}{2}\rbrack},\ \mathbf{e}_{\frac{n}{2}\ (excluded\ if\ n\ is\ odd)}\}$,
where:

$\mathbf{e}_{0}$ is a vector composed of n elements equal to
$n^{- 1/2}$, which implies that
$a_{0}\mathbf{e}_{0} = {(n^{- 1}\sum_{t = 1}^{n}x_{t},\ldots,n^{- 1}\sum_{t = 1}^{n}x_{t})}^{'}$;

$\mathbf{c}_{j} = \ \left( \frac{n}{2} \right)^{- 1/2}{(\cos\omega_{j},\cos{2\omega}_{j},\ldots,\cos{n\omega_{j}})}^{'},\ \text{for}\ 1 \leq j \leq \left\lbrack \frac{(n - 1)}{2} \right\rbrack$;

$\mathbf{s}_{j} = {\left( \frac{n}{2} \right)^{- 1/2}(\sin\omega_{j},\sin{2\omega}_{j},\ldots,\sin{n\omega_{j}})}^{'},\ for\ 1 \leq j \leq \left\lbrack \frac{(n - 1)}{2} \right\rbrack$;

$\mathbf{e}_{n/2} = {( - (n^{- \frac{1}{2}}),\text{\ n}^{- \frac{1}{2}},\ldots,{- (n}^{- \frac{1}{2}}),\ \text{\ n}^{- \frac{1}{2}})}^{'}$.

Equation \[7.107\] can be seen as an OLS regression of $x_{t}\ $on a
constant and the trigonometric terms. As the vector of explanatory
variables includes $\text{n\ }$elements, the number of explanatory
variables in \[7.107\] is equal to the number of observations. HAMILTON,
J.D. (1994) shows that the explanatory variables are linearly
independent, which implies that an OLS regression yields a perfect fit
(i.e. without an error term). The coefficients have the form of a simple
OLS projection of the data on the orthonormal basis:

  $${\widehat{a}}_{0}\ \ \ \  = \frac{1}{\sqrt{n}}\sum_{t = 1}^{n}x_{t}$$                                                                                                                                             \[7.108\]
  $${\widehat{a}}_{n/2} = \frac{1}{\sqrt{n}}\sum_{t = 1}^{n}{ {( - 1)}^{t}x}_{t}\left( \text{only\ when\ }\text{n\ }\text{is\ even} \right)$$                                                                          \[7.109\]
  $${\widehat{a}}_{0}\ \ \ \  = \frac{1}{\sqrt{n}}\sum_{t = 1}^{n}x_{t}$$                                                                                                                                             \[7.110\]
  ${\widehat{\alpha}}_{j} = \ 2^{1/2}r_{j}\cos\theta_{j} = \left( \frac{n}{2} \right)^{- 1/2}\sum_{t = 1}^{n}{x_{t}\cos{\left( {t\frac{2\pi j}{n}}_{\ } \right)\ }}$,$\ j = 1,\ldots,\lbrack\frac{n - 1}{2}\rbrack$   \[7.111\]
  ${ {\widehat{\beta}}_{j} = 2^{1/2}r}_{j}\sin\theta_{j} = \left( \frac{n}{2} \right)^{- 1/2}\sum_{t = 1}^{n}{x_{t}\sin\left( t\frac{2\pi j}{n} \right)_{\ }}$, $j = 1,\ldots,\lbrack\frac{n - 1}{2}\rbrack$           \[7.112\]

With \[7.107\] the total sum of squares
$\sum_{t = 1}^{n}\left| x_{t} \right|^{2}$ can be decomposed into
$2 \times \lbrack\frac{n - 1}{2}\rbrack\ $components corresponding to
$\mathbf{c}_{j}\ $ and$\ \mathbf{s}_{j}$, which are grouped to produce
the "frequency$\text{\ ω}_{j}\ $" component for 1 ≥$\ j$
≥$\lbrack\frac{n - 1}{2}\rbrack$. As it is shown in the Table 7.13, the
value of the periodogram at the frequency $\omega_{j}$ is the
contribution of the$\ j^{\text{th}}\ $harmonic to the total sum of
squares $\sum_{t = 1}^{n}\left| x_{t} \right|^{2}$.

**Decomposition of sum of squares into components
corresponding to the harmonics**

{: .table .table-style}
  |**Frequency**                                   |**Degrees of freedom**   |**Sum of squares decomposition**|
  |----------------------------------------------- |------------------------ |-------------------------------------------------------------------------------------------|
  |$\omega_{0}$(mean)                              |1                        |${a_{0}^{2}}_{\ } = n^{- 1}\left( \sum_{t = 1}^{n}x_{t} \right)^{2} = I\left( 0 \right)$|
  |$$\omega_{1}$$                                  |2                        |$${2r_{1}^{2}}_{\ } = 2{|a_{1}|}^{2} = 2I\left( \omega_{1} \right)$$|
  |$$\vdots$$                                      |$$\vdots$$               |$$\vdots$$|
  |$$\omega_{k}$$                                  |2                        |$${2r_{k}^{2}}_{\ } = 2{|a_{k}|}^{2} = 2I\left( \omega_{k} \right)$$|
  |$$\vdots$$                                      |$$\vdots$$               |$$\vdots$$|
  |$\omega_{n/2} = \pi$ (excluded if $n$ is odd)   |1                        |$$a_{n/2}^{2} = I\left( \pi \right)$$|
  |**Total**                                       |$$\mathbf{n}$$           |$\sum_{\mathbf{t = 1}}^{\mathbf{n}}\mathbf{x}_{\mathbf{t}}^{\mathbf{2}}$$|

Source: DE ANTONIO, D., and PALATE, J. (2015).

Obviously, if series were random then each component
$I\left( \omega_{j} \right)\ $would have the same expectation. On the
contrary, when the series contains a systematic sine component having a
frequency $j$ and amplitude $A$ then the sum of squares
$I\left( \omega_{j} \right)$ increases with $A$. In practice, it is
unlikely that the frequency $j$ of an unknown systematic sine component
would exacly match any of the frequencies, for which peridogram have
been calcuated. Therefore, the periodogram would show an increase in
intensities in the immediate vicinity of $j$.[^73]

Note that in JDemetra+ the periodogram object corresponds exactly to the
contribution to the sum of squares of the standardised data, since the
series are divided by their standard deviation for computational
reasons.

Using the decomposition presented in Table 7.13 the periodogram can be
expressed as:

 $I\left( \omega_{j} \right)\mathbf{=}\begin{matrix}                                                                                                                                                                                                                        \[7.113\]
  \text{\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ } \\                                                                                                                         
  r_{j}^{2} = \frac{1}{2}{(\alpha}_{j}^{2} + \beta_{j}^{2}) = \ {\frac{1}{n}\left( \sum_{t = 1}^{n}{x_{t}\cos{\left( {t\frac{2\pi j}{n}}_{\ } \right)\ }} \right)}^{2} + \frac{1}{n}\left( \sum_{t = 1}^{n}{x_{t}\sin\left( t\frac{2\pi j}{n} \right)_{\ }} \right)^{2} \\   
  \text{\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ } \\                                                                                                                                                                                                                           
  \end{matrix}$,                                                                                                                                                                                                                                                             

where $j = 0,\ldots,\left\lbrack \frac{n}{2} \right\rbrack$*.*

Since $\mathbf{x} - \overline{\mathbf{x}}$ are generated by an
orthonormal basis, and
$\overline{\mathbf{x}}\mathbf{=}a_{0}\mathbf{e}_{0}$ \[7.106\] can be
rearranged to show that the sum of squares is equal to the sum of the
squared coefficients:

 $\mathbf{x} - a_{0}\mathbf{e}_{0} = \sum_{j = 1}^{\lbrack(n - 1)/2\rbrack}{({\alpha_{j}}_{\ }\mathbf{c}_{j}\ {+ \ \beta_{j}\mathbf{s}}_{j}) + a_{n/2}\mathbf{e}_{n/2}}$.   \[7.114\]

Thus the sample variance of $x_{t}^{\ }$ can be expressed as:

 $n^{- 1}\sum_{t = 1}^{n}{ { {(x}_{t}^{\ } - \overline{x})}^{2} =}n^{- 1}\left( \sum_{k = 1}^{\lbrack(n - 1)/2\rbrack}{2\text{\ r}_{j}^{2} + a_{n/2}^{2}} \right)\ $,   \[7.115\]

where $a_{n/2}^{2}$ is excluded if $n$ is odd.

The term $2\text{\ r}_{j}^{2}$ in \[7.115\] is then the contribution of
the $j^{\text{th}}$ harmonic to the variance and \[7.115\] shows then
how the total variance is partitioned.

The periodogram ordinate $I\left( \omega_{j} \right)$ and the
autocovariance coefficient $\gamma(k)$ are both quadratic forms of
$\left\{ x_{t} \right\}.$ It can be shown that the periodogram and
autocovarinace function are related and the periodogram can be written
in terms of the sample autocovariance function for any non-zero Fourier
frequency$\text{\ ω}_{j}$:[^74]


  $$I\left( \omega_{j} \right) = \sum_{\left| k \right| < n}^{\ }{\widehat{\gamma}\left( k \right)}_{\ }e^{- ik\omega_{j}} = {\widehat{\gamma}\left( 0 \right)}_{\ } + 2\sum_{k = 1}^{n - 1}{\widehat{\gamma}\left( k \right)\cos{(k\omega_{j})}}_{\ }$$   \[7.116\]

and for the zero frequency
$\ I\left( 0 \right) = n\left| \overline{x} \right|^{2}$.

Once comparing \[7.116\] with an expression for the spectral density of
a stationary process:

 
  $$f\left( \omega_{\ } \right) = \frac{1}{2\pi}\sum_{k < - \infty}^{\infty}{\gamma\left( k \right)}_{\ }e^{- ik\omega_{\ }} = \frac{1}{2\pi}\left\lbrack {\gamma\left( 0 \right)}_{\ } + 2\left( \sum_{k = 1}^{\infty}{\gamma\left( k \right)\cos{(k\omega_{\ })}} \right) \right\rbrack$$   \[7.117\]

it can be noticed that the periodogram is a sample analog of the
population spectrum. In fact, it can be shown that the periodogram is
asymptotically unbiased but inconsistent estimator of the population
spectum $f(\omega)$.[^75] Therefore, the periodogram is a wildly
fluctuatating, with high variance, estimate of the spectrum. However,
the consistent estimator can be achieved by applying the different
linear smoothing filters to the periodogram, called lag-window
estimators. The lag-window estimators implemented in JDemetra+ includes
square, Welch, Tukey, Barlett, Hanning and Parzen. They are described in
DE ANTONIO, D., and PALATE, J. (2015). Alternatively, the model-based
consistent estimation procedure, resulting in autoregressive spectrum
estimator, can be applied.