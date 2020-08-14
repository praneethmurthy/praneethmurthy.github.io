---
layout: post
title: "Dimensionality Reduction"
comments: true
date: 2017-12-29 23:55:00 +0530
tags: pca, svd, johnson, lindenstrauss
---

The machine learning community has experimented with various "pre-processing" steps before performing any analysis on data. Two natural techniques (assuming that the data is "clean" and "usable by a program") are (i) Blowing up the dimensionality of data and (ii) reducing the dimension of the data. Both these approaches are known to perform exceptionally well in certain circumstances. For example, what Support Vector Machines essentially do is blow up the dimensionality of the data (and if the kernel used is a Gaussian kernel, the dimension is actually increased to infinity!) followed by learning a decition boundary in the "lifted space" whereas, for example in the k Nearest Neighbour problem, in most applications the first step involves a dimensionality reduction. In this article I will explain some of the intuition of two very popular methods for dimensionality reduction: Principal Components' Analysis and Random Projections. 



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
                            
