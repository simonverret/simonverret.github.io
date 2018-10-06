---
layout: post
title:  "Website creation"
categories: jekyll website
comments: true
---

I built this website using <a href="https://jekyllrb.com/">Jekyll</a>, as suggested when using <a href="https://pages.github.com/">Github pages hosting</a>. The theme is a variation on minima, the default Jekyll them, in which I implemented some customization inspired, or directly taken from the <a href="https://github.com/bogoli/-folio">folio</a> theme (found on the Jekyll 
<a href="https://jekyllthemes.io/free">free themes browser</a>).
<!-- , as well as from my friends <a href="https://sdufourbeausejour.github.io/">Sophie</a> and <a href= "https://www.jgyoung.ca/">Jean-Gabriel</a> personal pages. -->
All the source code for these websites are available on Github.

I created the initial website following 
<a href="https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/">Github's instruction</a>. A reminder to myself: I can run multiple local sites simultaneously (useful for comparing codes and output) with:
{% highlight bash %}
$ bundle exec jekyll serve --port 4001
{% endhighlight %}

By default, the code of the theme is implicitly called by Jekyll. To put it explicitly in the site's repository, I downloaded the <a href="https://github.com/jekyll/minima">actual source code</a>. This allowed me to experiment. In order to truly be independent from the theme, however, I had to follow <a href='https://jekyllrb.com/docs/themes/#converting-gem-based-themes-to-regular-themes'>Jekyll's instructions to regular themes</a>

In order to add mathematical expressions, I <a href="http://sgeos.github.io/github/jekyll/2016/08/21/adding_mathjax_to_a_jekyll_github_pages_blog.html">use mathjax</a>, with a few custom <a href="http://docs.mathjax.org/en/latest/tex.html">latex macros</a>.
