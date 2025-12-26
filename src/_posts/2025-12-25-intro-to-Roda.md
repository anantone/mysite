---
layout: post
title:  "Intro to Roda (a Ruby web framework) Episode 1"
date:   2025-12-25 06:12:03 +0100
categories: ruby-tools
---
Roda is a [routing tree web toolkit][roda] which, if you've read [my post about Sinatra][sinatra-post], seems to provide the same simplicity to write routes for a web application, with the added advantage of a tree structure to avoid repetitions (more on that later, if/when it applies to my project).

For now, I thought that a similar "Intro do Roda" post was in order, as this may be the framework that I use in the future, and learn more about, and complete more episodes about on this site.

Starting with Roda is as simple as requiring it and adding blocks with your routes. Here is the example from the website (very pretty and clear, compare to the docs for Sequel, also a gem by Jeremy Evans):

![basic roda routes example](/images/roda-basic.png)

And here is my first route:

![author's first roda route](/images/my-first-roda-route.png)

You will notice two additions:

- first, the `render` plugin, which allows easy rendering of an erb template (you just have to place it in a `views` folder). You then use `render("menu")` to render a `menu.erb` template located in that folder. Or, if you also have a `layout.erb` template within which you wish your pages rendered, you use the command `view("menu")` as I have in this example. I can then have a `navbar.erb`partial in the same folder, and call it in my `layout.erb` by adding `render('navbar')` just above the `yield` call.

![navbar and yield example](/images/navbar-yield.png)

- second the `public` pluging simply allows you to place a CSS file in a `public/css` folder, and by just adding `r.public` to your route block, your CSS will get picked up. Again, quite simple to recreate my home page:

![NINI home page with Roda](/images/nini-homepage-roda.png)

Now, same as with Sinatra in the previous post, it's time to add more complex features... in Episode 2!

[roda]: https://roda.jeremyevans.net/
[sinatra-post]: /ruby-tools/2025/12/24/intro-to-sinatra/