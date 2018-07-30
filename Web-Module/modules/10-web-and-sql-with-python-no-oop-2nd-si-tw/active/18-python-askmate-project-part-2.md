# Assignment: Python: AskMate project (part 2)

## Description

Last week you created a pretty good site from scratch. It already has some features but it's a bit difficult to maintain due to the fact that we store data in csv files and we also need some more features to make it more usable and more appealing to users.

## Specification

The management decided to move further as users requested new features like ability to comment on answers and tag questions (and here is the issue with csv files as well). There are several other feature requests which you can find in the user stories.

The management decided to put more ownership on the development team so now there is no compulsory stories. Of course the best case according to them if all of the stories are implemented but now it's more important that you, **the development team should choose the stories in order to maximize business values for the sprint**. So first, choose the stories and after that ask a mentor to validate it.

## Stories

**Business value** | 

**Feature**

| **Story**  
---|---|---  
2000 | use database | As a user I want to use the application fast even if there are lots of data in it, I want to reach data if another user uses it and I want the possibility to back up the data so if some data is lost then it is easily recoverable (hint: use PostgreSQL database instead of csv files; you don't have to implement backup now).   
600 | sort questions | The list of questions should be sortable according to: date, votes, number of views (both in ascending and descending order) ( **/list?time=asc &title=desc**,...) [If you did this user story in the previous sprint, now you only have to rewrite it to use SQL]  
800 | display latest questions | As a user, I want to see the latest 5 submitted questions on the main page ( **/** ). I want to see somewhere a link to all of the questions ( **/list** ).  
1100 | search questions | As a user I want to search in questions & answers. There should be a search box on the main page and a button. If I write something in the search box and press the button, I want to see a list of all questions (same data as in the list page) which title contains the text in the search box or which have answers which message contains the text in the search box. ( **/search?q= <search phrase>**)  
400 | fancy search results | As a user I want to see the search phrase highlighted in the search results. In addition, if the phrase is found in an answer, I also want to see not only the question, but below that the answer as well (slightly indented), in which I also want to see the search phrase highlighted.  
1200 | add comment to question | As a user I want to add comments to a question. There should be a link or button on the question page with which I can reach the new comment page ( **/question/ <question_id>/new-comment**). The comment should be visible on the question page.  
1100 | add comment to answer |  As a user I want to add comments to an answer. There should be a link or button on the question page next to or below the answer with which I can reach the new comment page ( **/answer/ <answer_id>/new-comment**). The comment should be visible on the question page together with its submission time.  
800 | edit comments | As a user I want to edit comments of a question or an answer ( **/comments/ <comment_id>/edit**). After editing there should be a text like "Edited <number of editions> times." next to or below the comment on the question page and the comment should show the updated text and the new submission time.  
800 | delete comments | As a user I want to delete comments of a question or an answer ( **/comments/ <comment_id>/delete**) by clicking a recycle bin icon next to the comment. After deletion the comment shouldn't be showed on the question/answer page.  
600 | tag question | As a user I want to add a tag to a question ( **/question/ <question_id>/new-tag**). On the new tag page I want to either choose from existing tags or define a new one. On the question page there should be a link or button which leads to the new tag page. The tags should be displayed on the question page as colored boxes next to each other.  
400 | delete tag | As a user I want to delete a tag from a question ( **/question/ <question_id>/tag/<tag_id>/delete**). On the question page there should be an X next to each tag, clicking that should delete the tag and reload the question page.  
  
## Data models

All data should be persisted in a PostgreSQL database in the following tables (you can ignore data in the not implemented fields):

![AskMate data model \(part 2\).png](media/Web%20with%20Python%20module%20resources/AskMate%20data%20model%20%28part%202%29.png)

### question table:

_id_ : A unique identifier for the question  
 _submisson_time_ : The date and time when the question was posted  
 _view_number_ : How many times this question was displayed in the single question view  
 _vote_number_ : The sum of votes this question has received  
 _title_ : The title of the question  
 _message_ : The question text  
 _image_ : the path to the image for this question

#### answer table:

_id_ : A unique identifier for the answer  
 _submisson_time_ : The date and time when the answer was posted  
 _vote_number_ : The sum of votes this answer has received  
 _question_id_ : The id of the question this answer belongs to  
 _message_ : The answer text  
 _image_ : The path to the image for this answer

#### tag table:

_id_ : A unique identifier for the tag  
 _name_ : The name of the tag

#### question_tag table:

_question_id_ : The id of the question the tag belongs to  
 _tag_id_ : The id of the tag belongs to the question

#### comment table:

_id_ : A unique identifier for the comment  
 _question_id_ : The id of the question this comment belongs to (if the comment belongs to an answer, the value of this field should be NULL)  
 _answer_id_ : The id of the answer this comment belongs to (if the comment belongs to a question, the value of this field should be NULL)  
 _message_ : The comment text  
 _submisson_time_ : The date and time the comment was posted or updated  
 _edited_number_ : How many times this comment was edited

#### Remarks

  * It's important that if the database table has a timestamp column then you cannot insert a UNIX timestamp value directly into that table, you should use:
    * either strings in the following format '1999-01-08 04:05:06',
    * or if you use psycopg2 and the datetime module, you can pass a datetime object to the SQL query as parameter in the following way:
        
                from datetime import datetime
        
        dt = datetime.now()  
        [...]
        cursor.execute('INSERT INTO some_table (somecol) VALUES (%s)', (dt,))

  * Pay attention on the order of inserting data into the tables, because you may violate foreign key constraints (that means e.g. if you insert data into the question_tag before you insert into the tag table the corresponding tag id you want to refer to then it won't exist yet)!

  * Some user stories may require to deal with CSS as well, but do not deal with CSS too much. It's more important that you write proper queries, have a working connection with psycopg2, have a clean Python code than create an amazingly beautiful web application (although if you have time, of course it's not forbidden to do so :) ).



### Sample data

To init the database we uploaded a sample data sql file (askmatepart2-sample-data.sql) into the sample_data directory in the very base repo: https://github.com/CodecoolBase/wswp-ask-mate.git

To have it in your repo, one member from your team should run the following commands from a clean/up-to-date repository:

1\. Add the new remote repo:

_git remote add codecoolbase https://github.com/CodecoolBase/wswp-ask-mate.git_

2\. Fetch the remote data (like branches) to use them:

_git fetch --all_

3\. Take the commit with the sql sample file:

_git cherry-pick 1f16087954f306eaf90c56b9d6369d4ce74ae45e_

4\. Push back to make it visible for the other team members:

_git push_

If you have created the database on your computer which you want to use then import the sample data file into psql with the \i command or run it via pgAdmin.




