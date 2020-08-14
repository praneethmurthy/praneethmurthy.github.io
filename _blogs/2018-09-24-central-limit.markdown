---
layout: post
title: "Central Limit Theorem and Weak Law of Large Numbers"
comments: true
date: 2018-09-24 22:45:00 -0500
tags: probability, characterisitic function, central limit theorem
---

Hello!

After a (_really_) long hiatus, I have resolved to start writing these posts more freqently. The first actual post I attempted (which is still incomplete) turned out to be a lot more effort than I initially fathomed. Thus, in this post, I decided to set more realistic goals. At the outset, I do not claim any of the below material to be my own, but rather the culmination of effort to _restart_ the habit of reading and writing more frequently. Secondly, although the title of this post is a comprehensive topic (indeed, there is a mind-boggling number of books written on the subject, also feel free to check out the [excellent post by Terence Tao](https://terrytao.wordpress.com/2008/06/18/the-strong-law-of-large-numbers/)) I will focus on two specific aspects. (i) I will introduce the Central Limit Theorem (CLT) and the Weak Law of Large Numbers (WLLN), and prove these results using the idea of Characteristic Functions; and (ii) I will provide a numerical experiment that shows the CLT in action. 

**Central Limit Theorem and Weak Law of Large Numbers**

Many of you might have noticed that most Machine Learning theoreticians (definitely in most engineering fields) often assume that the underlying probability distribution for _any_ problem make the assumption of Gaussianity, i.e., they assume that the true/natural data obeys a Gaussian distribution. This may seem contrived at the first glance because: why does nature have to obey Gaussian distribution? Well, a part of the justification might arise from the implications of the Central Limit Theorem. Said simply, it states that if you draw $$n$$ independent, and identically distributed (i.i.d.) samples, $$X_1, X_2, \cdots, X_n$$ from _any_ probability distribtion $$\mathcal{D}$$ with mean $$\mu$$ and variance $$\sigma^2$$, then CLT states the following: 
\begin{equation}
\sqrt{n}\left(\frac{X_1 + X_2 + \cdots + X_n}{n} - \mu\right) \overset{d}{\to} \mathcal{N}(0, \sigma^2)
\end{equation}
where the symbol $$\overset{d}{\to}$$ denotes that the random variable on the left "converges in distribution" to the distribution on the right as $$n \to \infty$$. Qualitatively, what that means is that if one were to draw multiple copies of the r.v. on the left and "plot their histrogram", it would look more and more like a Gaussian density as you increase the value of $$n$$.

The next result is the Weak Law of Large numbers. Consider, the same set of $$n$$ i.i.d. samples from the same distribution $$\mathcal{D}$$ as before. WLLS states that 
\begin{equation}
\frac{1}{n}(X_1 + X_2 + \cdots + X_n) \overset{p}{\to} \mu 
\end{equation}
where the symbol $$\overset{p}{\to}$$ means that the r.v. on the left "converges in probability" to the value on the right as $$n \to \infty$$. Qualitatively, this means that if you give my _any_ deviation, $$\epsilon$$ (from the mean) I can give you a large enough value of $$n$$ such that with probability $$1$$ the r.v. belongs to the interval $$[\mu-\epsilon, \mu + \epsilon]$$. The more precise statment for the above is
\begin{equation}
\lim_{n \to \infty} \mathbb{P}\left( \left|\frac{1}{n}(X_1 + X_2 + \cdots + X_n) - \mu \right| > \epsilon\right) = 0
\end{equation}

**Proof of Central Limit Theorem:**
There are multiple ways in which one can prove the CLT but I will focus on using the Characteristic Function (CF) (since I major in Signal Processing) approach. Recall that the CFof a r.v. $$X$$ is the expectation of the Fourier Transform, i.e., $$\psi_X(t) = \mathbb{E}[e^{itX}]$$. We will use these important properties of the CF (i) for independent r.v.'s $$X,Y$$, $$\psi_{X+Y}(t) = \psi_X(t) \psi_Y(t)$$; (ii) $$\psi_{aX}(t) = \psi_{X}(at)$$ for a positive scalar $$a$$; and (ii) the CF completely defines a r.v., and that the CF of a Gaussian r.v. is the density itself. 
Now, we expand the l.h.s. of the CLT equation and define the following r.v.'s to make the ideas easy to follow. 
\begin{equation}
\sqrt{n}\left(\frac{X_1 + X_2 + \cdots + X_n}{n} - \mu\right) = \sqrt{n} \cdot \frac{\sum_{i=1}^n (X_i - \mu)}{n} =  \frac{\sum_{i=1}^n (X_i - \mu)}{\sqrt{n}} 
\end{equation}
Also, notice that if we let $$Z_i = \frac{X_i - \mu}{\sigma}$$, the r.v.'s $$Z_i$$ are zero-mean, unit variance and still i.i.d. Next define $$Y_n = \frac{1}{\sqrt{n}}\sum_{i=1}^n Z_i$$ and consider its CF. Since $$Z_i$$ are i.i.d., we will drop the subscript and use $$Z$$ to mean any of the identical copies
\begin{align}
\psi_{Y_n}(t) &= \psi_{Z_1}\left(\frac{t}{\sqrt{n}}\right) \cdot \psi_{Z_2}\left(\frac{t}{\sqrt{n}}\right) \cdots \psi_{Z_n}\left(\frac{t}{\sqrt{n}}\right)  \\\
&= \left(\psi_Z\left(\frac{t}{\sqrt{n}}\right)\right)^n =  \left(\mathbb{E}\left[e^{\frac{itZ}{\sqrt{n}}} \right]\right)^n
\end{align}
now, from the Taylor series expansion of $$e^x$$, it is easy to see that 
\begin{align}
\mathbb{E}\left[e^{\frac{itZ}{\sqrt{n}}} \right] &= \mathbb{E}\left[1 + \frac{itZ}{\sqrt{n}} -  \frac{t^2 Z^2}{2n} -  \frac{it^3 Z^3}{3! n^{3/2}} + \cdots \right] \\\
&= 1 + 0 -  \frac{t^2}{2n} -  \frac{it^3 \mathbb{E}[Z^3]}{3! n^{3/2}} + \cdots 
\end{align} 
the important point to observe here is that all higher powers ($$ \geq 3$$) become infinitesimally small as $$n \to \infty$$ and thus
\begin{equation}
\psi_Z(t) = 1 - \frac{t^2}{2n} + r\left(\frac{t}{\sqrt{n}}\right)
\end{equation}
where $$r(\cdot)$$ is the "infinitesimal residual". Now, pluggin that value into the CF of $$Y_n$$, we obtain
\begin{align}
\psi_{Y_n}(t) = \left(1 -\frac{t^2}{2n} + r\left(\frac{t}{\sqrt{n}}\right)  \right)^n =  \left(\left(1 -\frac{t^2}{2n} + r\left(\frac{t}{\sqrt{n}}\right)  \right)^{-2n/t^2}\right) ^{\frac{-t^2}{2}} \to e^{\frac{-t^2}{2}}
\end{align}
as $$n \to \infty$$. This proves that the distribution of  $$Y_n$$ tends to become closer the the standard Gaussian distribution with increasing values of $$n$$. Finally, applying a rescaling of $$Y_n \to \sigma Y_n$$, we obtain the simplification of the l.h.s. of the main theorem. This proves CLT.  $$\boxtimes$$

**Proof of Weak Law of Large Numbers:**
Again, here there are multiple methods to prove the WLLN but I will focus on using CF. Again, since the r.v.'s $$X_i$$ are i.i.d., we will often drop the subscript and use $$X$$ to denote any of the identical copies. First, we define $$Y_n = \frac{\sum_{i=1}^n X_1 + X_2 + \cdots + X_n}{n}$$ and now consider the CF of $$Y_n$$. Recalling the two basic properties of CF from the previous section we obtain  
\begin{align}
\psi_{Y_n}(t) &= \psi_{X_1/n}(t) \cdot \psi_{X_2/n}(t) \cdots \psi_{X_n/n}(t) \\\
&= (\psi_{X/n}(t))^n = \left(\psi_X \left(\frac{t}{n}\right) \right)^n
\end{align}
now, using the same ideas as before: defintion of CF, linearity of expectation, and the Taylor series expansion of $$e^x$$, it follows that
\begin{align}
\psi_{Y_n}(t) &= \left( 1 +  \frac{it\mu}{n} - \frac{t^2 \mathbb{E}[X^2]}{2! n^2} - \frac{it^3 \mathbb{E}[X^3]}{3! n^3} +  \cdots \right)^n \\\
&= \left( 1 +  \frac{it\mu}{n} +  r\left(\frac{t}{n}\right) \right)^n \\\
&= \left( \left( 1 +  \frac{it\mu}{n} +  r\left(\frac{t}{n}\right) \right)^{\frac{n}{it \mu}}\right)^{i t \mu} \to e^{it\mu} \ \  \text{as} \ \  n \to \infty
\end{align}
and the "residual", $$r(t/n) \to 0$$ as $$n \to \infty$$. Finally, recall that due to the fact that the CF is the Fourier Transform of the density function, the Delta dirac, at $$\mu$$ has the CF $$e^{it\mu}$$ which means that $$Y_n \overset{d}{\to} \mu$$ and since $$\mu$$ is a constant, it implies that $$Y_n \overset{p}{\to} \mu$$ which proves WLLN. $$\boxtimes$$

**Numerical Verification of Central Limit Theorem:**
Here, I show using a simple numerical example to show CLT in practice. The exercise I performed here is the following. I generated $$n \approx 45000$$ samples ($$X_i$$) from the uniform random distribution, $$\mathcal{U}(0,1)$$ which denotes that all entries are between $$0$$ and $$1$$. The mean is $$\mu = 0.5$$ and the variance is $$\sigma^2 = 1/12$$ for this particular distribution. Next, for varying values of $$N \in [10, n]$$, I computed the "empirical density" of $$\sqrt{N} \left(\frac{\sum_{i} X_i}{N} - \mu\right)$$. I also plotted the "true density", $$\mathcal{N}(0, \sigma^2)$$. It is very interesting to see that as $$N \to n$$ (since we cannot really use the upper bound of $$\infty$$) the histogram converges very closely to match the Gaussian density, thus confirming claim of CLT. Furthermore, notice that here I show the figures at a logarithmic scale in $$N$$ and in some sense, the empirical histogram converges "linearly" to the true density. I might make a another post detailing the convergence rates of CLT in the near future. 
 
![alt text](https://media.giphy.com/media/BMIl5HB2ukMnCCchUw/giphy.gif) 

Here is the code snippet used to create the above animation. 

```
#!/usr/bin/env/ python

#import libraries
import numpy as np
import matplotlib.pyplot as plt


#generate samples using uniform random distribution

nrange = range(0, 50000);
S = np.zeros([50000,1]);

for n in nrange:
    Y = np.random.uniform(0, 1, n+1);
    S[n] = (np.mean(Y) - 0.5) * np.sqrt(n+1);

fig = plt.figure();
ax = plt.subplot(111);

Nrange = np.logspace(np.log10(10), np.log10(50000), 100);

for N in Nrange:
    plt.hist(S[0 : int(N) : 1], bins = 50, range=[-1.5, 1.5], normed=True, color="skyblue");
    t = np.linspace(np.min(S), np.max(S), 10000);
    mu = np.mean(S)
    sig = float(1)/np.sqrt(12);
    gaussian = 1 / np.sqrt(2 * np.pi * sig **2 )* np.exp(-(t ** 2)/(2 * sig **2));
    plt.plot(t, gaussian, linewidth=2, color='r')
    plt.ylim([0,2.5])
    plt.title('N = {}'.format(int(N)))
    plt.pause(.1);
    plt.clf();
```

And, that's all folks!!







<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = praneethmurthy.github.io;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = ; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://praneethmurthy-github-io.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
 


