# Assignment: Application process - Basic SQL

Handling the application process at Codecool has always been a tedious task. Finally the HR department figured out that using only Python and long lists is a no-brainer if they want to get information quickly. To improve on data management, they collaborate with you to test out something they just heard about: "databases".

## The exercise

Luckily they managed to assemble a database, which can be described by the Entity-Relationship Diagram below:

![application process assignment.png](media/Web%20with%20Python%20module%20resources/application%20process%20assignment.png)

They need your help to to write a simple console application which runs and prints quieries on this database (you can use your local PostgreSQL database as they provided sample data but you should only turn in your program's git repository url - as before - because they just change the credentials and use the program on their central database).

## Preparation

You can find the sql file with the sample data in the git repo linked below. Clone it, switch to that folder in terminal and start psql in that folder with the command:
    
    
    [terminal]  
    psql

If you gave the same name for your PostgreSQL role as your linux user login name, there is no need to write in passwords or anything, psql just starts and you can interact with your database.

To put the data into your database type the following into the psql prompt:
    
    
    [psql]  
    \i application_process_sample_data.sql

## The queries

The HR department wants answers to the following questions:

  1. Write a query that returns the 2 name columns of the mentors table.  
 _columns: first_name, last_name_
  2. Write a query that returns the nick_name-s of all mentors working at Miskolc.  
 _column: nick_name_
  3. We had interview with an applicant, some Carol. We don't remember her name, but she left her hat at the school. We want to call her to give her back her hat. To look professional, we also need her full name when she answers the phone (for her full_name, you want to include a concatenation into your query, to get her full_name, like: "Carol Something" instead of having her name in 2 different columns in the result. This columns should be called: full_name).  
 _columns: full_name, phone_number_
  4. We called Carol, and she said it's not her hat. It belongs to another girl, who went to the famous Adipiscingenimmi University.  
You should write a query to get the same informations like with Carol, but for this other girl.  
The only thing we know about her is her school e-mail address ending: '@adipiscingenimmi.edu'.  
 _columns: full_name, phone_number_
  5. After we returned the hat, a new applicant appeared at the school, and he wants to get into the application process.  
His name is Markus Schaffarzyk, has a number: 003620/725-2666 and e-mail address: djnovus@groovecoverage.com  
Our generator gave him the following application code: 54823

After INSERTing the data, write a SELECT query, that returns with all the columns of this applicant! (use the unique application code for your condition!)

  6. Jemima Foreman, an applicant called us, that her phone number changed to: 003670/223-7459  
Write an UPDATE query, that changes this data in the database for this applicant.  
Also, write a SELECT query, that checks the phone_number column of this applicant.  
Use both of her name parts in the conditions!
  7. Arsenio, an applicant called us, that he and his friend applied to Codecool.  
They both want to cancel the process, because they got an investor for the site they run: mauriseu.net

Write DELETE query to remove all the applicants, who applied with emails for this domain (e-mail address has this domain after the @ sign).




**You need to create a console application with some simple menu, where each menu point answers one question (or does what the question asks) from the above list.** If the question is to print out some table, please print it out in some readable way (e.g. different rows on separate lines, no unnecessary parenthesis around values etc.), but don't mess a lot with formatting.

Hint: use the _psycopg2_ library to connect to the database and execute SQL statements.

## GitHub classroom

GitHub classroom link: <https://classroom.github.com/a/T7PR365X>

Please accept the classroom invitation and submit the link of your repo in the end.




