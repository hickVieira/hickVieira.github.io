---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
lastmod: {{ .Date }}
description: "Example article description"
categories:
  - "Category 1"
  - "Category 2"
tags:
  - "Tag 1"
  - "Tag 2"

comments: true # Enable/disable Disqus comments for specific page
authorbox: true # Enable/disable Authorbox for specific page
toc: true # Enable/disable Table of Contents for specific page
tocOpen: true # Open Table of Contents block for specific page
mathjax: true # Enable/disable MathJax for specific page
related: true # Enable/disable Related content for specific page
meta:
  - date
  - categories
  - tags

featured:
  url: images/image.jpg # relative path of the image
  alt: image description # alternate text for the image
  caption: image caption # image caption
  credit: credits # image credit
  previewOnly: false # show only preview image (true/false)
---