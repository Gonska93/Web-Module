# Assignment: Application process - SQL - level 2

## The exercises

We continue practicing with native SQL statements, but now you have 6 exercises for JOINing and GROUPing data tables!

The database you need to work on looks like this:

![application process assignment part 2.png](media/Web%20with%20Python%20module%20resources/application%20process%20assignment%20part%202.png)

## Preparation

First download the sample data from here: [application_process_sample_data_2.sql](modules/11-web-and-sql-with-python-no-oop-3rd-si-tw/active/media//Web%20with%20Python%20module%20resources/application_process_sample_data_2.sql "application_process_sample_data_2.sql"). You can find an .sql file on this link, please save it to your computer, switch to that folder with terminal and start psql in that folder with the command:
    
    
    [terminal]  
    psql

If you gave the same name for your PostgreSQL role as your linux user login name, there is no need to write in passwords or anything, psql just starts and you can interact with your database.

To put the data into your database type the following into the psql prompt:
    
    
    [psql]  
    \i application_process_sample_data_2.sql

**You need to improve your already started console application and upgrade it to a fully functional Flask application.** So you can work on the previously started github repository.

### Requirements

#### Root root [/]:

It shows a list of links which are pointing to specific roots. See the roots below. 

  1. Mentors and schools page [/mentors]  
On this page you should show the result of a query that returns the name of the mentors plus the name and country of the school (joining with the schools table) ordered by the mentors id column ( _columns: mentors.first_name, mentors.last_name, schools.name, schools.country_ ). 

  2. All school page [/all-school]  
On this page you should show the result of a query that returns the name of the mentors plus the name and country of the school (joining with the schools table) ordered by the mentors id column.  
BUT include all the schools, even if there's no mentor yet (in that cell, "No data" should be displayed)!  
 _columns: mentors.first_name, mentors.last_name, schools.name, schools.country  
_

  3. Mentors by country page [/mentors-by-country]  
On this page you should show the result of a query that returns the number of the mentors per country ordered by the name of the countries  
 _columns: country, count_

  4. Contacts page [/contacts]  
On this page you should show the result of a query that returns the name of the school plus the name of contact person at the school (from the mentors table) ordered by the name of the school  
 _columns: schools.name, mentors.first_name, mentors.last_name_

  5. Applicants page [ _/applicants_ ]  
On this page you should show the result of a query that returns the first name and the code of the applicants plus the creation_date of the application (joining with the applicants_mentors table) ordered by the creation_date in descending order  
 **BUT** only for applications later than 2016-01-01  
 _columns: applicants.first_name, applicants.application_code, applicants_mentors.creation_date_

  6. Applicants and mentors page [ _/applicants-and-mentors_ ]  
On this page you should show the result of a query that returns the first name and the code of the applicants plus the name of the assigned mentor (joining through the applicants_mentors table) ordered by the applicants id column  
Show all the applicants, even if they have no assigned mentor in the database!  
In this case use the string "No data" instead of the mentor name.  
 _columns: applicants.first_name, applicants.application_code, mentors.first_name, mentors.last_name_




Use proper HTML elements to represent the data on the query related pages.

Do not forget to commit frequently after you finish a certain feature e.g.: a whole page.

## Submission

Push your modifications into the previously created git repository on github and submit url of that repo (without the .git on the end, so for example <https://github.com/myusername/myreponame>).



