---
title: Provable Online Matrix Completion and Robust Matrix Completion
layout: page
tags: matrix completion, robust matrix completion, dynamics
permalink: /research/DynRMC.html
---

The problem we study here is a natural extension of two problems, (i) Subspace Tracking and (ii) (Robust) Matrix Completion. These problem have been extensively studied in the batch setting, but there is a lack of provable online algorithms. We study this problem, and in fact, interpret is as a simplification of the [Dynamic RPCA](DynRPCA.html) problem. 

First, we study the case of subsace tracking from missing data, which can be interpreted as a online version of the matrix completion problem when the subspace changes slowly (we in fact prove that this is necessary). The results for these are shown here. 

![Alt](/assets/vid_mc.png "Figure taken from our work")

Next, as a simple modification, we also study the case when the low-rank data is also corrupted by sparse, arbitrary noise, in addition to missing data. The results for this problem are as follows. 

![Alt](/assets/vid_rmc.png "Figure taken from our work")

#### List of Selected Publications: ####

1. Provable Subspace Tracking from Missing Data and Matrix Completion, \\
**Praneeth Narayanamurthy**, Vahid Daneshpajooh, and Namrata Vaswani, \\
_IEEE Transactions on Signal Processing_, June 2019. \\
(A part of this paper was the **finalist of the best student paper award** at SPARS 2019).

