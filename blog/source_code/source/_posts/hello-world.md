title: Hexo排公式的小问题
tags: Hexo
categories: Hexo
author: Shixiang
date: 2018-04-28 11:42:00
mathjax: true
---

Hexo挺好玩儿，排出来的页面很漂亮。兴奋之余，首先要排个公式看看。

$$\xi_t(i,j) = \frac{\alpha_t(i) a_{ij} b_j(o_{t+1})\beta_{t+1}(j)}{\sum_{p=1}^m \sum_{q=1}^m \alpha_t(p) a_{pq} b_q(o_{t+1})\beta_{t+1}(q)}$$

然后发现，似乎Hexo上的MathJax排公式比较严格：不允许出现双大括号`{% raw %}{{}}{% endraw %}`。这我就好奇了，比如`${% raw %}\sqrt{{X}}{% endraw %}$`渲染时会报错, `$\sqrt{X}$`则没有问题。查询一番发现是Vue.js的问题： **Vue.js 中的双大括号{{ Mustache }}与 Nunjucks 解析相冲突**（相关链接： https://github.com/hexojs/hexo/issues/1930）。

遗憾的是，目前这仍然是个令人头疼的问题。简单的解决方案有两个：
 1. 使用如同`{% raw %}{{message}}{% endraw %}`的写法包裹有双大括号的情形；
 2. 将双大括号`{% raw %}{{}}{% endraw %}`拆分成`{ {} }`。



