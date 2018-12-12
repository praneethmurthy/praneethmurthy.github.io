---
layout: post
title: "Eigenvector Computation"
comments: true
date: 2018-12-11 22:18:00 +0530
tags: SVD, EVD
---

In this post, I will discuss a few ways in which eigenvalues and eigenvectors are computed in practice. As a disclaimer, I mention at the outset that this is not the way most numerical libraries perform the computation, rather, this is a beginner level article to understand some elementary methods. 

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
 


