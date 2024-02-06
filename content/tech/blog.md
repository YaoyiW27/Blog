---
title: "Why I chose Hugo as the framework for blog?"
date: 2024-02-03T01:42:03-08:00
draft: false
---

### Dynamic Blog or Static Blog

#### Dynamic Blog
A dynamic blog is a blog program that runs on a server. The most famous dynamic blog program is WordPress, and other commonly used ones include Halo and Typecho, among others. Compared to static blogs, the advantages of dynamic blogs are that they are dynamically updated, have a backend, an online editor, and are relatively closer to the traditional habit of 'publishing articles on a website.' However, setting up requires purchasing hosting, and it is said that maintenance can be somewhat troublesome.

#### Static Blog
Essentially, it consists of a series of static HTML pages. The advantages are fast access, no need to purchase hosting, and since all files are local, even if it is left idle for a long time or encounters any issues, the article data will not be lost. However, setting up a static blog requires a certain level of technical expertise.

##### Common frameworks for static blogs:
[Gridea](https://gridea.dev/) is a static blog writing client that helps you build and manage blogs or any static site more easily. However, the author's maintenance of this project is not very active, and it is probably going to be abandoned.


[Jekyll](https://jekyllrb.com/) is a simple form of a blog-like static site generator and is recommended by GitHub for deploying on GitHub Pages. It can be considered the official recommendation.

[Hexo](https://hexo.io/index.html) is a fast, concise, and efficient static blog framework based on Node.js. Hexo supports Markdown parsing of articles and can generate static web pages with attractive themes in a matter of seconds.

[Hugo](https://gohugo.io/) is a fast, modern static website generator written in Go. It's simple, easy to use, efficient, easily extensible, and deploys quickly.

#### Back to the main topic
Due to the advantages of static blogs, such as focusing on content writing, fewer ads, and mostly minimalist themes, I chose a static blog.
Also, I wanted to learn Go language, and Hugo's installation is relatively straightforward, I chose Hugo as my blog framework.