# Web storage mechanisms

## Introduction

You've already heard of [localStorage](http://htmldog.com/guides/javascript/advanced/localstorage/), a storage mechanism with you can store data on the client's computer instead of storing it on server side in database, for example.

However, there are other means of web storage mechanisms as well and we should speak about them in order to clarify the differences and use cases.

Http is **stateless protocol** , that means that it doesn't store anything on client or server side about the connection (whether we send a request or waiting for something) so normally we don't know anything about any previous requests when we do a request to a web server. That also means that everything what we need on the server side (authentication, target and source of the request etc.) have to travel in one message.

However, sometimes (actually quite often) we need to preserve state, that means we want to know something that happened before our current http request. The simplest example is the user login mechanisms of various sites. If you have no state, that means the user must sign in on _every_ page load (since we don't know anything about her). But if we can somehow store something about the user then we shouldn't ask her to log in every time.

There are different storage mechanisms that developed through the history of web development and they have different capabilities and use cases. Let's see them one by one with example as well and on the bottom of the page you will find a comparison between them.

## Cookie

Cookies exists since the early era of web development (they were invented in 1994 by Netscape Communications).

_Using the Set-Cookie header field, an HTTP server can pass name/value pairs and associated metadata (called cookies) to a user agent. When the user agent makes subsequent requests to the server, the user agent uses the metadata and other information to determine whether to return the name/value pairs in the Cookie header._

_\-- IETF:[RFC6265](https://tools.ietf.org/html/rfc6265)_

So cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing. Since it is stored on the client side, it can be deleted or modified by the user or the user can disable the whole cookie feature in her browser.

Cookies belongs to a certain domain. For obvious security reasons, cookies can only be set on the current resource's top domain and its sub domains, and not for another domain and its sub domains. For example, the website _example.org_ cannot set a cookie that has a domain of _foo.com_ because this would allow the _example.org_ website to control the cookies of _foo.com_.

This is an example response sent by a server setting two cookies in the client's browser. The first one is a _session cookie_ , it will be deleted when the browser closes, the second one is a _persistent cookie_ , because it has the _Expires_ attribute set which instructs the browser to delete the cookie at a specific date and time.
    
    
     HTTP/1.0 200 OK
    Content-type: text/html
    Set-Cookie: theme=light
    Set-Cookie: sessionToken=abc123; Expires=Wed, 09 Jun 2021 10:18:14 GMT
    …

Next time when the browser makes a request to this website, it sends the cookie as well with the _Cookie_ header:
    
    
     GET /spec.html HTTP/1.1
    Host: www.example.org
    Cookie: theme=light; sessionToken=abc123
    …
    

Cookies are supported by all browsers, can expire, but have a limitations of storing only around 4KB of data.

Cookies are mainly used for simple data that shouldn't be trusted (since the user can tamper with it), mainly for preferences settings on a site (but cookies are used for e.g. showing you personalized ads as well).

So cookies are stored on client side, but should be set on server side. Here's a really simple Flask example, how to set a cookie:
    
    
    @app.route('/set_cookie')
    def cookie_insertion():
        redirect_to_index = redirect('/index')
        response = current_app.make_response(redirect_to_index)  
        response.set_cookie('cookie_name',value='values')
        return response

If something is not clear you can find further informations on <http://www.allaboutcookies.org/> and on [Wikipedia](https://en.wikipedia.org/wiki/HTTP_cookie), and of course in the above mentioned [RFC document](https://tools.ietf.org/html/rfc6265).

## localStorage and sessionStorage

localStorage and sessionStorage are also client side storage mechanisms. They are relatively new concepts and became available with the HTML5 standard (although they have put in a separate specification later), so they are not supported by legacy browsers (e.g. Internet Explorer 7).

As they are client side storage, they can be deleted or modified by the user, just like cookies. One of the main difference is the size. As we saw, within a cookie we can store only around 4KB of data, localStorage and sessionStorage can store much more (around 5MB, depending on the browser).

Another difference from cookies that they do not travel with request and response, so they are only accessible on the client side. These storage objects are just properties of the Javascript _window_ object.

But what's the difference between localStorage and sessionStorage?

  * window.localStorage - stores data with no expiration date
  * window.sessionStorage - stores data for one session (data is lost when the browser tab is closed)



localStorage is per origin (per domain and protocol). All pages, from one origin, can store and access the same data. sessionStorage is per browser session.

These can be used for also for data that shouldn't be trusted but we can store more data than in cookies. For example we can use them for caching API responses, preserving form states etc.

Some example (sessionStorage can be set and get the same way):
    
    
    // Store  
    localStorage.setItem("lastname", "Smith");  
    // Retrieve  
    document.getElementById("result").innerHTML = localStorage.getItem("lastname");

## Server side session

The above were client side storage mechanism, but what if we want to store some data about the user and we don't want the user modifying it or we want the data to be accessible by the server?

The solution is to store data on the server side, so cannot be reached by the user, we can store data that can be trusted. We can store big amount of data according to the server's memory (but be careful, because if you have a huge amount of users then you have to store that data for every user and it can be a lot of data).

But still, we should know something about the client to know which data on the server corresponds with which user. Normally we use cookies for that, so we authenticate user with a cookie and based on that we can show the data from the server's data source. Here's a nice sequence-like diagram, which may help understand how sessions are implemented with cookies.

![session-with-cookie.png](media/Web%20with%20Python%20module%20resources/session-with-cookie.png)

Luckily most framework does this whole thing for us, so we don't have to manually set cookies.

For example, in Flask (example code from [Flask documentation](http://flask.pocoo.org/docs/0.12/quickstart/#sessions), please read the explanation there if something is not clear):
    
    
    from flask import Flask, session, redirect, url_for, escape, request
    
    app = Flask(__name__)
    
    @app.route('/')
    def index():
        if 'username' in session:
            return 'Logged in as %s' % escape(session['username'])
        return 'You are not logged in'
    
    @app.route('/login', methods=['GET', 'POST'])
    def login():
        if request.method == 'POST':
            session['username'] = request.form['username']
            return redirect(url_for('index'))
        return '''
            <form method="post">
                <p><input type=text name=username>
                <p><input type=submit value=Login>
            </form>
        '''
    
    @app.route('/logout')
    def logout():
        # remove the username from the session if it's there
        session.pop('username', None)
        return redirect(url_for('index'))
    
    # set the secret key.  keep this really secret:
    app.secret_key = 'A0Zr98j/3yX R~XHH!jmN]LWX/,?RT'

You can read more about sessions in [this article](http://machinesaredigging.com/2013/10/29/how-does-a-web-session-work/).

## Comparison

| **Cookie** | **localStorage** | **sessionStorage** | **Server side session**  
---|---|---|---|---  
**Can be trusted?** |  No | No | No | Yes  
**Data travels between server and client** |  Yes | No | No | Just the cookie  
**Data size limit** |  Small (~4KB) | Large (~5MB) | Large (~5MB) | Large (server memory)  
**Separation** |  Per domain | Per origin | Per browser session | Per session ID
