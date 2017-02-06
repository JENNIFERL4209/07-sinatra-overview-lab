# Sinatra Overview

## Overview

Now that you understand the MVC structure in general, let's get acquainted with one specific example: Sinatra.  We'll make sure Sinatra is installed and then run a simple web application with it. 

## Objectives

1. Understand what routes are.
2. Describe Sinatra.
3. Distinguish between Sinatra and Rails
4. Install Sinatra on your computer
5. Run a basic Sinatra application


## Routes
Throughout this reading, you will see the word **route**.  Similar to how Google Maps might give you a route from point A to point B, as developers of a full-stack web applications, you need to make routes that describe exactly what happens when a user goes somewhere.  It can be split up into two categories: **GET** and **POST**.

In short, a route that includes a `get` request means the user is trying to access a specific URL, i.e. "get"ting something.

This is going to be slightly different than a route involving a `post` request, where the user typically submits a form in order to move on to another page.

Either way, there might be backend stuff that needs to happen in between **the user trying to get somewhere** and **where they actually end up**.  For example, when a user signs into a webpage, they type in their information and press 'Sign in' (which is a `post` request), and a specific **route** (in the Controller) takes their information and uses the Model(s) in the backend to decide which View to load and help inject the custom information.  Like Google Maps, all of those step-by-step directions are called a 'route'.  Sometimes they are simple, and sometimes they are complex.  It just depends on what you want to do.

## What is Sinatra?

Sinatra is a **D**omain **S**pecific **L**anguage (`rspec` is another example of a DSL) implemented in Ruby that's used for writing web applications. Created by [Blake Mizerany](https://github.com/bmizerany),  Sinatra is Rack-based, which means it can fit into any Rack-based application stack, including Rails. It's used by companies such as Apple, BBC, GitHub, LinkedIn, and more.

Essentially, Sinatra is nothing more than some pre-written methods that we can include in our applications to turn them into Ruby web applications.  In a way, it is similar to how Bootstrap is nothing more than some pre-written CSS classes that you can include in your HTML.

Unlike Ruby on Rails, which is a Full Stack Web Development Framework that provides everything needed from front to back, Sinatra is designed to be lightweight and flexible.  Sinatra is designed to provide you with the bare minimum requirements and abstractions for building simple and dynamic Ruby web applications.

In addition to being a great tool for certain projects, Sinatra is a great way to get started in web application development with Ruby and will prepare you for learning other larger frameworks, including Rails.

## Why Sinatra Before Rails

Maybe you've heard of "Ruby on Rails" and how powerful it is. You can build impressive web applications in mere hours! How amazing. Most people, when they learn Rails for the first time, literally say "It's like magic!". But we're developers, and we know that magic isn't real and that other smart developers just built an impressive framework.

That means it's important to understand the basic concepts of Rails before diving into Rails itself. **Enter Sinatra.**


Sinatra is considered a _light weight_ framework where the responsibility of app structure and communication falls solely on the developer. Sinatra doesn't give you a lot to get started with. There is no way to auto-generate files and directories, no way for the app to make assumptions about routes, or "Sinatra magic".

Because of this, working with Sinatra allows you to dive in deep with the major concepts of MVC, a system for building web applications that governs 90% of the worlds' apps. You are required to manually set up routes and connect them to other pieces of your application. Without this manual setup, your application does not automatically know how to communicate with your database or what HTML files to load in the browser. And even more importantly, without a manual setup, you lose connection to the major components of a web application, and in particular, all the moving pieces of MVC.

So introduce yourself to Sinatra. Get to know it, and know it well. The better your foundation, the more you'll be able to know (and like) Rails.

## The Sinatra DSL

Any application that requires the `sinatra` library will get access to methods like: `get` and `post`. These methods provide the ability to instantly transform a Ruby application into an application that can respond to HTTP requests.

## Basic Sinatra Applications

First, make sure Sinatra is installed by running `gem install sinatra` in your terminal.

Here is the simplest Sinatra application we could write:

File: `app.rb`
```ruby
require 'sinatra'

get '/' do
  "Hello, World!"
end
```

Typically, you could start this web application by running `ruby app.rb`. 

>NOTE: In cloud9, you need to include two more pieces of information: the **port** and the **IP** address using the `-p` and `-o` flags, respectively.  For cloud9, the numbers are dynamic and are stored in the variables `$PORT` and `$IP`.  So to correctly run in the app in cloud9, you should type `ruby app.rb -p $PORT -o $IP`

You'll see something similar to:

```
$ ruby app.rb -p $PORT -o $IP
[2017-02-02 20:52:31] INFO  WEBrick 1.3.1
[2017-02-02 20:52:31] INFO  ruby 2.3.0 (2015-12-25) [x86_64-linux]
== Sinatra (v1.4.8) has taken the stage on 8080 for development with backup from WEBrick
[2017-02-02 20:52:31] INFO  WEBrick::HTTPServer#start: pid=3199 port=8080 
```


This is telling us that Sinatra has started a web application running on your computer listening to HTTP requests at port `8080`. If you start this application and navigate to `https://ruby-YOURUSERNAME.c9users.io/` (shown in the green bubble) you'll see "Hello, World!" in your browser. 

So what does the code mean?
* `require 'sinatra'` is utilizing the sinatra gem that we just installed.
* `get '/'` is setting up a route that handles `get` requests to `/`.  When a user loads `https://ruby-YOURUSERNAME.c9users.io/` in a new tab, they are essentially requesting to **get** something from the server running at `ruby-YOURUSERNAME.c9users.io`, and the path to where they want to go is simply the `/` at the end.  
* Inside of the `do`/`end`, here is where we specify the actual steps to be taken.  In the future, we will have multiple steps, usually ending in loading a **view**, but this example simply loads the string "Hello World".

Go back to your terminal running the Sinatra application and stop it by typing `CTRL+C`. You should see:

```
^C== Sinatra has ended his set (crowd applauds)
[2017-02-02 20:54:16] INFO  going to shutdown ...
[2017-02-02 20:54:16] INFO  WEBrick::HTTPServer#start done.
$
```

WHOA!  We just ran our first web application!  See, wasn't that easy?

This is the most basic Sinatra application structure and is actually pretty uncommon. More commonly, Sinatra is used in a modular style encapsulated by Controller Classes and booted via the `config.ru` Rack convention.  More on that later.

## Resources

* [Blake Mizerany - Ruby Learning Interview](http://rubylearning.com/blog/2009/08/11/blake-mizerany-how-do-i-learn-and-master-sinatra/)
* [Companies Using Sinatra](http://www.sinatrarb.com/wild.html)