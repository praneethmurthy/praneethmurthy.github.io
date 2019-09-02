---
title: PCA under generic noise models
layout: page
tags: PCA, SVD, sub Gaussian, bounded, non-isotropic, data-dependent
permalink: /research/PCALimits.html
---



Although Principal Component Analysis (PCA) is a problem that has been studied for over a century, it is surprising that most ''guarantees'' for it are asymptotic in nature. While the asymptotic regime is higly insightful, in practice it is required to know how good an approximation we can obtain from a finte number of samples. The seminal paper by [Nadler][1] was one of the first papers to analyse this problem in detail and the author derives precise characterization of the errors incurred as a funciton of the number of samples used. However, the analysis is performed only in the case of Isotropic noise. This is a valid assumption in many scenarios but oftentimes, the noise is non-isotropic, and sometimes even data-dependent. This project aimed at developing finite sample guarantees or establish fundamental limits on what can be expected under a more generic class of noise models.

We extend this in [our work][2] and obtain finite sample guarantees for the case when the noise is dependent on the data. 

![Alt](/assets/pca_phasetrans.png "Figure taken from our work")

[1]: https://projecteuclid.org/euclid.aos/1231165185.
[2]: https://arxiv.org/abs/1709.06255

#### List of Publications: ####


1. Finite sample guarantees for PCA in non-isotropic and data-dependent noise, \\
Namrata Vaswani and **Praneeth Narayanamurthy**, \\
_Allerton Conference on Computation, Communication and Control, 2017_.

1. PCA in Sparse Data-Dependent Noise, \\
Namrata Vaswani and **Praneeth Narayanamurthy**, \\
_IEEE International Symposium on Information Theory 2018_. 
 
 
