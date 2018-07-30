# Assignment: Python: AskMate project

## Description

Its time to put your newly acquired Flask skills to use! Your next big task will be to implement a crowdsourced Q&A site, like Stack Overflow.

## Specification

The initial version of the site should be able to handle questions and answers, there is no need for other functionality like user management or comments for questions/answers.

The management was very interested in the agile development methodologies that you learned about recently, thus they are handing out stories this time instead of a fixed specification. **Your main goal is to implement all stories with 1000 business value** , if your team has still time left you can pick freely from the other stories. 

## Stories

**Business value** | 

**Feature**

| **Story**  
---|---|---  
**1000** |  ask a question | There should be a page where I can ask a question ( **/new-question** ). The question must be at least 10 characters long. After the question is posted it should be displayed.  
**1000** |  list questions | There should be a page which can display every asked question ( **/,** the root of the app and **/list** ). They are sorted by time (most recently asked one at the top). Also you should display an "ask a question" link here.  
**1000** |  display a question | There should be a page that displays a single question, all its data and all its answers ( **/question/ <question_id>**).  
600 | sort questions | The list of questions should be sortable according to: date, votes, number of views (both in ascending and descending order) ( **/list?time=asc;title=desc** ,...)  
400 | edit a question | There should be an "edit" button when displaying a question. Clicking this will allow the user to edit the question. ( **/question/ <question_id>/edit**)  
600 | delete question | There should be a "delete" button for each question. This deletes the question and all its answers (if any), and then displays the list of questions.( **/question/ <question_id>/delete**).  
**1000** |  post an answer | There should be a page where I can post an answer to an existing question. The answer must be at least 10 characters long. ( **/question/ <question_id>/new-answer**). There should be a link at each question detail page that leads to this page.  
400 | delete an answer | The site should allow to delete posted answers. ( **/answer/ <answer_id>/delete**)  
700 | vote | There should be a "vote up" and a "vote down" button besides each question and answer. Each one increases/decreases the vote count for them respectively. After sending a vote the page should reload to display the updated vote count. ( **/question/ <question_id>/vote-up **and **vote-down** )  
500 | add image | it should be possible to add a single image to a question or an answer. This must be deleted if the question/answer is deleted.  
  
## Data models

All data should be persisted to .csv files. You will need one for storing all questions, one for storing all answers. These look the following (you can ignore data in the not implemented fields):

### Question.csv:

_id_ : A unique identifier for the question  
 _submisson_time_ : The UNIX timestamp when the question was posted  
 _view_number_ : How many times this question was displayed in the single question view  
 _vote_number_ : The sum of votes this question has received  
 _title_ : The title of the question encoded in BASE64  
 _message_ : The question text encoded in BASE64  
 _image_ : the path to the image for this question encoded in BASE64

#### Answer.csv:

_id_ : A unique identifier for the answer  
 _submisson_time_ : The UNIX timestamp when the answer was posted  
 _vote_number_ : The sum of votes this answer has received  
 _question_id_ : The id of the question this answer belongs to.  
 _message_ : The answer text encoded in BASE64  
 _image_ : the path to the image for this answer encoded in BASE64

Note: You can easily google how you can BASE64 encode an image and what the UNIX timestamp is.

### Project structure

We recommend, that you split the code into modules according to clean code principles: Do not put more than 100-150 lines of code into a single file, files should contain logically the same things, etc.

For example, you could split it up to these 3+1 parts:

**Layer** | **Example filename** | **What should it do/contain?**  
---|---|---  
Routing layer | server.py | Flask stuff (server, routes, request handling, session, etc.)  
This layer should only consist of logic that is hardly related to Flask.  
Business logic layer | logic.py | Connection layer between the routes and the CSV handling layer. It should have functions which can be called from the routing layer, and they should call persistence layer functions.  
Persistence layer | persistence.py | The layer that have access to any kind of long term data storage. In this case, we use CSV files, but later on we'll change this to SQL database. So in the future, we only need to change in this layer.  
Utility "layer" | util.py | Helper functions which can be called from any other layer. (but mainly from the business logic layer)  
  
This is just one way to structure your code, you don't have to follow it [strictly].

### Repository

Please use the following link to start your repository: <https://classroom.github.com/g/cXcXous6>

It only contains a .gitignore file and some sample data. 



