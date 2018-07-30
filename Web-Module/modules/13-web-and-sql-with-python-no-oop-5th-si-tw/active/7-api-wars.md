# Assignment: API Wars 

## Description

Yes, we are near to the end of the **Web and SQL with Python** module! Because you are so awesome, a golden humanoid droid want to meet you in the nearest Kantina....

[Watch this intro!](https://brorlandi.github.io/StarWarsIntroCreator/#!/AKm_o10u6I9E57lJU7AJ)

## The Project

Your task is to create a little web application which shows data about the Star Wars universe, store visitor preferences with cookies and handle user login with sessions. It is advised to create the application in the following steps:

  1. Create a Flask based webserver. This should render an HTML file containing a **table with all the Planets in the Star Wars** universe with these data:  

    1. name
    2. diameter in km
    3. climate
    4. terrain
    5. surface water percentage
    6. population in formatted way
  2. Make a button in each row (in a new column) if the planet has **residents**. These buttons should open a modal, populated its data with AJAX, containing the list of residents with more detailed information: 
    1. name
    2. height (in meters)
    3. mass (in kg)
    4. skin color
    5. hair color
    6. eye color
    7. birth year
    8. gender
  3. Create a **simple user login system** with the following parts (use session for that): 
    1. a registration page accessible from the main page through which visitors can create a user-password pair in the database (you are advised to use salted password hashing with [these helper functions](http://werkzeug.pocoo.org/docs/0.12/utils/#security-helpers)),
    2. a login page accessible from the main page where the user can log in,
    3. display username and logout link in the header.
  4. [OPTIONAL TASK] If the user is logged in, display a button in each row (in a new column) with which the logged in user can **vote on a planet** (she can vote to unlimited number of planets). Save this vote in a database with AJAX and inform a user somehow that the vote has been saved.
  5. [OPTIONAL TASK] Create a new modal window accessible from the main page where you **display the statistics** about voted planets. Display a table with each voted planet and the number of vote the planet received. Use data from the database, receiving it with AJAX in JSON format.



### The Data

Every Star Wars related information can be fetched from <https://swapi.co/>'s API, use the API to get the data. This site provides an endpoint with no authentication needed.

For the login and voting functionality, you can use a database with one table like this:

#### users table

_id_ : serial, primary key  
 _username_ : unique name for users - varchar  
 _password_ : hashed password - varchar

#### planet-votes table

___id_ : serial, primary key  
 _planet_id_ : integer (id from SWAPI data)  
 _planet_name_ : varchar  
 _user_id_ : integer, foreign_key  
 _submission_time_ : datetime

## UI Plan

The index page should look like this:

![starwars_screenshot_01.png](media/Web%20with%20Python%20module%20resources/starwars_screenshot_01.png)

When you click the "x residents" button, a modal should show up. In the moment of click it should gather information about the residents of the planet and format this data into a table, like this:

![starwars_screenshot_02.png](media/Web%20with%20Python%20module%20resources/starwars_screenshot_02.png)

When you click on "Voting statistics", a modal like this should show up:

![starwars_screenshot_03.png](media/Web%20with%20Python%20module%20resources/starwars_screenshot_03.png)

Hints:

  * Use Bootstrap, if you don't want to spend too much time with design
  * Use a H1 tag for the page heading
  * Add buttons for navigating between chunks of data (loading all planets would take too much resources, so SWAPI implements a pagination. Just look into it's response, it has a "next" and a "previous" attribute)
  * Use a bordered table to display the needed informations
  * You are not required to use AJAX for the base page data. If you like, you can use Python for parts of the data processing (like the planet list), BUT the modal windows **must** load by calling an API with AJAX. This API can be SWAPI directly, or you can write a proxy in your Flask app.  
For this, the "[Varying modal content based on trigger button](https://getbootstrap.com/docs/4.0/components/modal/#via-javascript)" section of the Bootstrap documentation might help a lot.
  * For session usage there is an example on the Web storage mechanisms page, you can use that.
  * For storing voted_planets information you can use the [jQuery.post()](https://api.jquery.com/jquery.post/) method on the client side and you should create and appropriate endpoint on the server side.
  * For displaying the voted planet statistics on the server side, you can use Flask's [jsonify](http://flask.pocoo.org/docs/0.12/api/#flask.json.jsonify) function to return a JSON and process it on the client side.



## Guide for Peer Review

The following issue list is intent to help you evaluate your peers solution. 

3 [ **negligible** ] issues count as 1 [ **minor** ] issue  
3 [ **minor** ] issues count as 1 [ **major** ] issue

Please also count the valuable [ **extra** ] tags. These count as positive [ **negligible** ] issues. IF, and only if there is at least 2 [ **extra** ] tags left at the end of the review for the specific ascpect/rubric, then you can give a 12 grade.

Note:  
Grade 10 means less then 1 major or equivalent issue(s);   
Grade 7 means max. 1 major or equivalent issue(s);   
Grade 4 means max. 2 major or equivalent issue(s);   
Grade 2 means max. 3 major or equivalent issue(s);   
Grade 0 means more then 3 major or equivalent issue(s);

### Comfort to requirements

  * [ **failing** ] Server is not starting
  * [ **failing** ] Page is not loading recognisable content
  * [ **major** ] Page navigation is not working (You can't move foward and back between the planet lists)
  * [ **major** ] Resident modal is not opening/working by clicking the residents button.
  * [ **major** ] Page shows a server error, anytime during the review.
  * [ **major** ] After opening a residents modal, by opening another one, the page shows the content of the previous modal.
  * [ **major** ] Can not close the residents modal
  * [ **major** ] User registration is not completly implemented, or it isn't using a Database
  * [ **major** ] User login is not completly implemented
  * [ **minor** ] Planet table is not using <table> HTML element.
  * [ **minor** ] Not exactly 10 planets are shown on the first page.
  * [ **minor** ] The surface water percentage value is not clearly stating unknown value or showing an extra "%" sign. (Ex. for Coruscant)
  * [ **minor** ] The population value is not clearly stating unknown value or showing an extra "people" suffix. (Ex. for Hoth)
  * [ **minor** ] Residents button is there for planets where there is no known resident.
  * [ **minor** ] By double clicking the navigation buttons on the planet list, the next page's content gets loaded twice.
  * [ **minor** ] Vote button is visible when the user is not logged in (or the login feature is not implemented)
  * [ **minor** ] Logged in user's name is not appearing in the header
  * [ **minor** ] There is no Logout button, or the functionality does not work.
  * [ **minor** ] The users DB table differ from the plan. (and the 4th exercise was considered implemented)
  * [ **minor** ] The planet-votes DB table differ from the plan. (and the 4th exercise was considered implemented
  * [ **negligible** ] No "km" suffix after the planet's diameter value. MNB
  * [ **negligible** ] No "%" suffix after the planet's surface water percentage value.
  * [ **negligible** ] No "people" suffix after the planet's population value.
  * [ **negligible** ] Residents button column is not clearly stating there are no known residents, but writing similar to "0 know residents".
  * [ **negligible** ] The Previous button is clickable on the first page, and/or the Next button is clickable on the last page
  * [ **negligible** ] By clicking/double clicking the navigation buttons on the planet list, the page's content blinks.
  * [ **negligible** ] Stored passwords are not hashed
  * [ **negligible** ] 4th exercise is defined "done" but the user does not get a feedback when [s]he votes.
  * [ **extra** ] Planet list is not reloading data which was once already loaded
  * [ **extra** ] Planet list is showing a loading indicator while the content is loading
  * [ **extra** ] Planet list navigation gets disabled while the requested data is loading
  * [ **extra** ] Residents modal is not reloading data which was once already loaded
  * [ **extra** ] Residents modal is not showing the table's header until the content is loaded
  * [ **extra** ] Residents modal is showing a loading indicator while the content is loading
  * [ **extra** ] A nice background image is used, that fits nicely to the site and does not draw you attention out from actual content.
  * [ **extra** ] Bootstrap is used with non-default colors is used (custom build, or a bootswatch theme)
  * [ **extra** ] Stored passwords are salted
  * [ **extra** ] 4th exercise is finished
  * [ **extra** ] 5th exercise is finished



### Javascript

TBD...

## Submission

Start with this empty repository: <https://classroom.github.com/a/gPiqeWlm>

Submit your link to the git repository!



