---
title: Provable Guarantees for Dynamic Robust PCA
layout: page
tags: PCA, SVD, robust PCA, dynamics
permalink: /research/DynRPCA.html
---

The problem we study here is a natural extension of two problems, (i) Subspace Tracking and (ii) Robust PCA. Both these problems are well studied and there exists a vast body of literature that analyze the statistical and algorithmic aspects of this problem. In this work, we build upon the ReProCS framework to show that under very mild conditions we are able to provably solve the dynamic RPCA problem. 

This question has been an open problem for quite a while now, and thus, we simplify the problem a little bit. In the first approach, we assume that only certain directions of the underlying subspace changes. In particular, we assume that an instance of the subspace change looks as below. 

![Alt](/assets/ss_change.png "Figure taken from our work")

This allows a simplification in the analysis of the algorithm. AS a consequence, we are able to design a provably fast, memory-efficient, and ``online'' algorithm. 

In The second part of the work, we eliminate this restriction, through a minor modification in the algorithm, and show that even in the general case, we are able to solve the problem. 

![Alt](/assets/srpca_vid.png "Figure taken from our work")

#### List of Selected Publications: ####

1. Provable Dynamic Robust PCA and Robust Subspace Tracking, \\
**Praneeth Narayanamurthy** and Namrata Vaswani, \\
_IEEE Transactions on Information Theory_, May 2019.

1. Nearly Optimal Robust Subspace Tracking, \\
**Praneeth Narayanamurthy** and Namrata Vaswani, \\
_International Conference on Machine Learning_, 2018.
