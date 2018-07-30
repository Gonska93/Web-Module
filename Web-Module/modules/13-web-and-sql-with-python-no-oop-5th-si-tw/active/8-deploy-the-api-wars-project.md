# Assignment: Deploy the API Wars project

## Deploy your Star Wars project

### What deployment means?

_Software deployment is all of the activities that make a software system available for use. The general deployment process consists of several interrelated activities with possible transitions between them._

In this case, we deploy our Flask application to Heroku, a PaaS (platform as a service) service that you can use for free. Follow this tutorial to deploy your app to Heroku:

<https://marcellban.github.io/heroku-flask/> (Thanks for one of the Codecoolers, Marcell Bán for this tutorial.)

## Hints

\- make a **runtime.txt** with one line in it which is your python version (like python-3.5.2 - check <https://devcenter.heroku.com/articles/python-runtimes> what runtimes are available on Heroku)

\- be careful with **requirements.txt**. Don't just write the whole _pip freeze_ into it. First go through that tutorial and make that basic flask app run. It only needs those things what are screenshot in the tutorial ( _flask, gunicorn,[itsdangerous](http://www.fictorians.com/wp-content/uploads/2017/03/its-dangerous-to-go-alone-take-this.jpg), jinja2.._ ). If your app needs more modules, put them into the _requirements.txt_ but only if it is needed!

## Submission

Submit your app's Heroku link, and don't forget to keep it running!

## Grading

As this assignment is focusing on the deployment, not the development of the main project, the following options can occur:

**Case** |  **Grade**  
 **on Expected behaviour**  
---|---  
  
The project is available on Heroku and the link works.

The user sees the same, as the submission for the [API Wars](%24CANVAS_OBJECT_REFERENCE%24/assignments/i0d3d7af49d471bb23169b9a635473290 "API Wars ") assignment

| 10  
  
The project is available on Heroku and the link works.

The user sees different than the submission for the [API Wars ](%24CANVAS_OBJECT_REFERENCE%24/assignments/i0d3d7af49d471bb23169b9a635473290 "API Wars ") assignment  
(including if the site shows an Exception or debug informations)

| 4  
The project is not available / The link doesn't work | 0  
No submission | -3  
  


