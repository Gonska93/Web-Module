# A web-framework for Python: Flask

## Web? Framework?

A web [application] **framework** is a software **framework** that is designed to support the development of web applications including web servers, webpages and web APIs. Web **frameworks** aim to alleviate the overhead associated with common activities performed in web development.

So frameworks are some kind of software helping developing another software. They usually help by creating a structure and providing help through this structure, which can be folder structure, code structure or logical structure.

### Remember: How a basic HTTP request-response circle looks like?

![LSBAWS_HTTP_request_response.png](media/Web%20with%20Python%20module%20resources/LSBAWS_HTTP_request_response.png)

  1. User does stuff
  2. Browser translates it to an HTTP request
  3. Aaaand the server...



Yes, what does the server do? How can we catch this request? How can we run something when the user reaches our application? How-how-how?

This is the place where a Framework comes handy. It handles all the logic to listen on a specific port, trigger logic on request and translates the HTTP details into Python variables. With the help of the framework, the magic is mostly done, we just have to do our part (4.) and send back a ~"response". Not a real HTTP response, because the framework needs to do some work on it too. 

  5. The server sends back the response
  6. The user's browser formats the response and shows it to the user.
  7. The user is happy. _(usually)_



## Decorators in Python

Decorators are an advanced feature of Python, that most web frameworks make use of. They usually appear as a line beginning with the "@" symbol above functions, for example:
    
    
    @this_is_a_decorator   
    def my_function():   
        print("No, I am your function!")

Please read this page to get familiar with them: [Decorators in Python](%24WIKI_REFERENCE%24/pages/decorators-in-python "Decorators in Python")

## Flask

Flask is a micro web framework written in Python. It provides an easy way to create webpages, has a very good documentation and does not depend on many other libraries. It uses [decorators](%24WIKI_REFERENCE%24/pages/decorators-in-python "Decorators in Python") for routing (to determine what to display if the user goes to a sub-page, like mysite.com/my_sub_page)

### Installation

Flask may already installed on your machine but you can run this one to be sure:
    
    
    pip3 install Flask

And don't forget to update it:
    
    
    sudo pip3 install --upgrade Flask

The "Hello World" application with Flask looks as simple as this:
    
    
    from flask import Flask
    app = Flask(__name__)
    
    @app.route('/')
    def hello_world():  
        # Return this to the user who visited this page. The browser will render it.
        return 'Hello World!'
    
    if __name__ == '__main__':
        app.run()

**Try it!** Just save this code to a file (for example hello.py) and run it with your IDE or in terminal with the good old
    
    
    python hello.py

It will tell you where to look but by default it will create a page with this address:

<http://127.0.0.1:5000/>

Don't stop the program, just visit this address and see that wonderful 'hello world!' in your browser. Just to know: 127.0.0.1 is a special network address, it represents your own computer. So it's really Home, sweet home.

Note: Do not try to run you app more than one instance at a time. If you do so you will get a _Address already in use_ Error. **Advanced question** : Try to figure out what this error means.

## If you learn more from action

... we recommend the following video series:

  1. [Basic App](https://www.youtube.com/watch?v=ZVGwqnjOKjk)
  2. [Routing](https://www.youtube.com/watch?v=27Fjrlx4s-o)
  3. [HTTP Methods](https://www.youtube.com/watch?v=PWF_WyvgKqY)
  4. [HTML templates](https://www.youtube.com/watch?v=t3yHNZhSXLE)
  5. [Static files](https://www.youtube.com/watch?v=WxgYYGxoPwY)
  6. [Mapping multiple URLs](https://www.youtube.com/watch?v=t24ZOk06wa8)
  7. [Passing Objects into Templates](https://www.youtube.com/watch?v=AOboS0RESt4)



## Why do we learn Flask?

There are dozens of frameworks for every language, and Python is not an exception. Flask is good for beginners with it's developer friendly system and useful for experienced programmers because.. well, because the same reason. And it also has a great documentation. 

## What next?

The application above is not so sophisticated. Let's create something more useful with our Tutorial: [A simple webpage with Flask: Flask-Note](%24WIKI_REFERENCE%24/pages/a-simple-webpage-with-flask-flask-note "A simple webpage with Flask: Flask-Note")
