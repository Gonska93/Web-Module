# Understanding the web

## Welcome to the Web

Today, almost everyone uses the Internet. The huge network, where you can get and post information. To develop applications that are using the web, it's necessary to understand how the internet works (in a nutshell)

### The Internet

The 2 following video will explain, who the internet works:

[![Play on YouTube](https://img.youtube.com/vi/7_LPdttKXPc/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=7_LPdttKXPc "Play on YouTube")

(The video stops at 3:54, because the content after that time is invalid)

[![Play on YouTube](https://img.youtube.com/vi/oj7A2YDgIWE/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=oj7A2YDgIWE "Play on YouTube")

Please make sure to look after these keywords **(don't skip this part)** :

  * IP address
  * DNS
  * ISP
  * Router
  * HTTP
  * HTTP request



### From the developers side

"Okay, these videos are cute, and even my grandma can understand them, but I'm a DEVELOPER!"

Watch this video to see how HTTP works, and how a website gets loaded. 

[![Play on YouTube](https://img.youtube.com/vi/e4S8zfLdLgQ/0.jpg):arrow_forward:](https://www.youtube.com/watch?v=e4S8zfLdLgQ "Play on YouTube")

Cool! Now, that you saw how it looks in the background, see it for yourself!

Go to **github.com** and **python.org** and see what traffic is coming-going with a "simple" site. 

New terms to look up (and don't skip this either :) ):

  * Port
  * Browser
  * URL
  * Web server
  * HTML
  * CSS
  * JavaScript
  * Cookies
  * UserAgent (concept)



## Python as a Web Server

How does Python comes to all this? Well, you can write a web server in almost any programming language. Python has a default library, called `http`, what you can use to create a simple webserver in a folder. To try it out, follow these steps:

  1. Download any template from [HTML5 UP!](https://html5up.net) site.
  2. Unpack the content into a folder.
  3. Navigate to this folder from the terminal.
  4. Run the following:  
`python -m http.server 9876`
  5. With your browser, navigate to: <http://localhost:9876>
  6. Think through what just happened! ;)
  7. In the terminal, run **ifconfig**.
  8. Find your IP address in the output, and replace 'localhost' in the previous URL.
  9. You should see the same page like before.
  10. If it's possible, try this address from other devices connected the same network you are connected to. It must be the same home router (WiFi access) and probably it won't work using mobile-internet.
  11. WooHoo! You just created a web server! Congrats!



We won't do anything with this later, the point of this exercise is to see how you can reach your small server from your local machines.
