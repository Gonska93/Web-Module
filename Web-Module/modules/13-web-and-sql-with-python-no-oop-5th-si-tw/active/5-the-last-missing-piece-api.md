# The last missing piece: API

## Application Programming Interface

Yes, I know you already googled it. This is what API stands for, and you might have a guess what we call an API.

If no, let us help you:

[![Play on YouTube](https://img.youtube.com/vi/s7wmiS2mSXY/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=s7wmiS2mSXY "Play on YouTube")

In other words, we can say: An API is a gate (interface) in a software, that allows connectivity for the outside word. Usually one API endpoint lets you interact with one certain part of the given software.

## Why is it good for me?

Today we usually don't write one huge application for a specific purpose, but we build a system. (Which probably uses already existing components or systems) Mainly because of re-usability, scalability and maintainability. And if we write smaller parts, they has to communicate with each other.

Think about a simple example, a very basic Flask webserver. You just have to create an instance of the Flask class, and call the **run** method on it, and it fires up. However, even if you don't realize it, you use the API, that the system of Flask provides: By using the Flask class and using a method on the newly created instance of it. The connection is available because Python creates an interface to use another module (Flask in this case).

Another kind of API, is the API what the video talks about. It is not reachable in the file-system or application level, but on a networking level » but it's still a very similar API.

To answer the header question, knowing how an API works is important for a developer, because [s]he will use all different kind of APIs every day. (...[s]he already does that...)

## Lets try it out!

To fire up an HTTP request, you can use lot of different tools. To make a request from the Terminal, you can use [curl](https://curl.haxx.se/docs/manpage.html). For a nice GUI, we recommend [Insomnia](https://insomnia.rest/) or [Postman](https://www.getpostman.com/), intuitive clients for this purpose. (For this "tutorial", I used Postman, so if you'd like to try out curl, please look around online.)

  1. Install Postman (if you have trouble on Ubuntu, here's a [guide](https://blog.bluematador.com/posts/postman-how-to-install-on-ubuntu-1604)).
  2. Open up Postman (you can skip signing up and skip directly to the program).
  3. Set the url to: "<https://api.github.com>" (the root access point of GitHub)
  4. Press Send.
  5. As we expected, the API doesn't return an HTML page. See the result JSON that the GitHub API sent back and try to understand it. ... (yeah, a lot of urls. cool) Now try out some real stuff:
  6. Set the url to: "<https://api.github.com/repos/twbs/bootstrap>"  
This is the API endpoint for a specific repository, Twitter's Bootstrap in this case. See, how many ~useful information we got. To read more about this endpoint: <https://developer.github.com/v3/repos/#get>
  7. Set the url of one of your repos (e.g. "https://api.github.com/repos/<username>/<reponame>") and see the same info of your repository.



Okay, now put this into programming. The quest is the following: **Please print out the number of people who starred Atom's repository!**

With Python, you can write something like this, to call this API endpoint:
    
    
    import json  
    import urllib.request  
    webURL = urllib.request.urlopen("https://api.github.com/repos/atom/atom")  
    data = webURL.read()  
    encoding = webURL.info().get_content_charset('utf-8')  
    response_data = json.loads(data.decode(encoding))  
    print(response_data['stargazers_count'])

Or an even simpler code, if you install the requests pip package:
    
    
    import requests  
    response = requests.get('https://api.github.com/repos/atom/atom').json()  
    print(response['stargazers_count'])

That's it. As the **requests.get** method returns a Response object, which has a json() method, which returns a dictionary, we can use it to print out a specific part this way.

With [Vanilla JavaScript](http://vanilla-js.com/) (native Javascript without any libraries used):
    
    
    function reqListener () {  
        if (request.status < 400) { // successful response  
            let responseData = JSON.parse(this.response);  
            console.log(responseData.stargazers_count);  
        }  
    }  
    var request = new XMLHttpRequest();  
    request.addEventListener('load', reqListener);  
    request.open('GET', 'https://api.github.com/repos/atom/atom');  
    request.send();

With Javascript (using the jQuery library):
    
    
    $.getJSON('https://api.github.com/repos/atom/atom', function(response){  
        console.log(response['stargazers_count'])  
    });

Which is a shorthand to the following jQuery method:
    
    
    $.ajax({
        dataType: "json",
        url: 'https://api.github.com/repos/atom/atom',
        success: function(response) {
            console.log(response['stargazers_count'])
        }
    });
    

Did you wanted to know how to AJAX? This is how you do AJAX... :)

## How does it actually works?

Before we move on, and see what API stands for, we should clear up some thoughts about different buzz-words.

### What is AJAX?

When we talk about an API that is reachable through a network, it's important to know what AJAX is. Check this video about it (the first 3 minutes is strongly advised to watch, the later parts contains some interesting but advanced topics so they are optional):

[![Play on YouTube](https://img.youtube.com/vi/3l13qGLTgNw/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=3l13qGLTgNw "Play on YouTube")

### What is XHR? And why is XML is mentioned so many times?

XHR stands for XMLHttpRequest, a default Javascript object.

This is the object responsible for creating HTTP requests from JS. If we forget about jQuery for a little bit, we can see what it hides from us in the background: <http://blog.garstasio.com/you-dont-need-jquery/ajax/>. Actually this codeblock is what we should know about XHR, what it builds up.

Today we use JSON format to work with data between the client and the server instead of XML. But we don't call it AJAJ because it sounds stupid.

Okay, now you can go back to jQuery. ;)
