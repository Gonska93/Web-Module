# Assignment: Python: AskMate project (part 3)

## Description

Last week you made a very good progress to improve your web application. We need some more features to make it more usable and more appealing to users.

## Specification

Users requested new features like ability to manage users according to questions and answers. There are a few other feature requests which you can find in the user stories.

The management would like to separate the already working features from the upcoming ones so your development team need to **start use branching workflow and open new branches for the features you start in this sprint**. As last week the ownership is in your hand so there is no compulsory stories but of course the best case according to them if all of the stories are implemented. Choose the stories in order to maximize business values for the sprint. So first, choose the stories and after that ask a mentor to validate it.

Another change that the management would like to see in your workflow to choose one dedicated person in your team who takes the SCRUM master role and keep in touch with the product owner during the sprint. About the different roles and responsibilities here you can find a description.  
[Roles and responsibilities in SCRUM teams](https://drive.google.com/open?id=0B1kZCTq9w1f7QUxhRGpvU2plVGc "Roles and responsibilities in SCRUM teams")

## Stories

**Business value** | 

**Feature**

| **Story**  
---|---|---  
1000 | simple user registration | As a user I would like to have the possibility to register a new user into the system. ( **/registration** ). A user only has a username and the date of the registration.  
1000 | list users | There should be a page where I can list all the registered users with all their attributes except their id.  
500 | bind questions to user | As a user I would like to have the possibility in the new question page to select the user who creates the new question.  
500 | bind answer to user | As a user I would like to have the possibility on the answer page to select the user who give the answer.  
500 | bind the comment to user | As a user I would like to have the possibility in the comment section to select the user who add the comment.  
1000 | user page | There should be a page where the user can list all his/her activities. ( **/user/ <user_id>**) On this page there should be seen which are the questions he asked, which answers he gave to questions and what comments he added before. All those (questions, answers, comments) need to be shown in separated tables where the question title is a link to the related question.  
500 | accepted answer | As a user I would like to have the possibility to mark an answer as accepted.  
1000 | gain reputation | As a user I would like to see a reputation system to strengthen the community. Reputation is a rough measurement of how much the community trusts in each other.   


**A user gains reputation when:**

  * her/his question is voted up: +5
  * her/his answer is voted up: +10
  * her/his answer is marked “accepted”: +15



**Prerequisites: User related features are implemented.**  
  
1000 | lose reputation | 

As a user I would like control not just the positive attitude but punish the wrong ones. Reputation system should be extended with the rules below:

**A user loses reputation when:**

  * her/his question is voted down: −2
  * her/his answer is voted down: −2



**Prerequisites: User related features are implemented.**  
  
800 | tag page | There should be a page where I can list all the existing tags and that how many questions are marked with the given tags. ( **/tags** ) **Prerequisites: Tag related features are implemented.**  
  
## Data models

As you have became familiar with the CREATE statement the management hasn't prepared the data model. They trust in you and they are certain about you can design this small extension for the current database. To change the already existing tables you will need to use the ALTER TABLE statement. For this you can find some help [here](https://www.w3schools.com/sql/sql_alter.asp "ALTER TABLE"). (Do not forget to setup the foreign keys if those are necessary)

### Remarks

  * It's important that if the database table has a timestamp column then you cannot insert a UNIX timestamp value directly into that table, you should use:
    * either strings in the following format '1999-01-08 04:05:06',
    * or if you use psycopg2 and the datetime module, you can pass a datetime object to the SQL query as parameter in the following way:
        
                from datetime import datetime
        
        dt = datetime.now()  
        [...]
        cursor.execute('INSERT INTO some_table (somecol) VALUES (%s)', (dt,))

  * Pay attention on the order of inserting data into the tables, because you may violate foreign key constraints (that means e.g. if you insert data into the question_tag before you insert into the tag table the corresponding tag id you want to refer to then it won't exist yet)! Especially it is important after you change the database structure with new foreign keys. Maybe it's worth to modify the sample data based on your changes. 

  * Some user stories may require to deal with CSS as well, but do not deal with CSS too much. It's more important that you write proper queries, have a working connection with psycopg2, have a clean Python code than create an amazingly beautiful web application (although if you have time, of course it's not forbidden to do so :) ).
  * Because you have learnt about how to write complex queries and join multiple tables in one select maybe you should spend some time to optimize your previously created queries where it's applicable.
  * Take care about some user stories have prerequisites!



