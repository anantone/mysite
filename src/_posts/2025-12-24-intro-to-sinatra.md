---
layout: post
title:  "Intro to Sinatra (the Ruby web framework) Episode 1"
date:   2025-12-24 17:12:03 +0100
categories: ruby-tools
---
Some time ago, I wanted to make a web application. I had been learning Python, my first programming language, for about 3 months. I had followed a course on [Django][django], but found it difficult to manage on my own. Looking for something easier, I found [Flask][flask], but still struggled with setting up my simple app. Then came [Bottle][bottle], which had the required simplicity for someone learning programming, http requests, and basic CRUD operations all at the same time. I am not unhappy with [the result][NINI].

Then my Python courses started talking about [object-oriented programming (OOP)][oop]. While researching the notion, I saw that this language called [Ruby][ruby] was exclusively built for OOP, and thought I'd give it a try. Six months later, I'm mostly picking Ruby over Python when I want to have fun, and I'm looking for a web framework, again. 

Have you heard about [Rails][rails]? It seems to have become so popular, some years ago, that people knew "Ruby on Rails" before Ruby itself. That was before my time, though. As a Ruby newbie, I'm looking for something as simple as Bottle was in Python, which does well enough the things I need to do. So here I am [trying Sinatra][sinatra].

The first thing I see, that's similar to bottle, is a simple way to define routes. In my main file, all I need to do is:

1) ```ruby
require 'sinatra'```

2) define my route such as:

  ```ruby
  get '/' do  
    'something'  
   end
   ```

This simple example states that for a GET request sent to the root URL, the string 'something' will be sent to the browser and rendered.

![something rendered](/images/something.png)

Equally simply, I can provide an [erb template][erb] and define the route as 
```ruby
get '/' do
    erb :menu
end
```
which ends up rendering my `menu.erb` template:

Template
![template](/images/menu-template.png)

Rendered page (including CSS file)

![example frontpage](/images/nini-frontpage.png)

So far, so good, Sinatra has really provided as straightforward an experience as Bottle. We've just rendered a template, though. In the next episode, we'll try to have some kind of computation happen toward our request.  

<!-- LINKS -->

[django]: https://www.djangoproject.com/
[flask]: https://flask.palletsprojects.com/en/stable/
[bottle]: https://bottlepy.org/docs/dev/
[NINI]: https://anbarto.pythonanywhere.com/
[oop]: https://en.wikipedia.org/wiki/Object-oriented_programming
[ruby]: https://www.ruby-lang.org/en/
[rails]: https://en.wikipedia.org/wiki/Ruby_on_Rails
[sinatra]: https://sinatrarb.com/
[erb]: https://github.com/ruby/erb