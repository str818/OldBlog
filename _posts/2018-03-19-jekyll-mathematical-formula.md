---
layout: post
title: 基于Jekyll的博客支持LaTeX数学公式
categories: [Jekyll]
tags: Jekyll
---

　　找到博客页面的模板文件(一般路径为_layouts/default.html)，在其中加入下面的代码：
```javascript
<script type="text/javascript"
src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
```
　　之后将默认的Markdown引擎改为kramdown，编辑_config.yml:
```
markdown:kramdown
```

