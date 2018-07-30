# Assignment: simple Flask Dojo

## Description

This 0 points Assignment is a list of exercises for practicing Flask.

## Steps

You can find multiple sections which you can accomplish separately after the Preparation part. Do not forget to commit after you completed a part.

### Preparation

  1. First you should setup a completely new GitHub project for this Assignment.
  2. Make sure you have Flask installed.
  3. Create an empty Flask application which you can use to implement the different features.
  4. [Install curl](https://www.howtoinstall.co/en/ubuntu/xenial/curl "Install curl").



### Root route

  1. Make a GET-Request button that sends a GET request to the **/request-counter** route.
  2. Make a POST-Request button that sends a POST request to the **/request-counter** route.
  3. Make a Statistics link that navigates to the **/statistics** route.



HINT: take care about the two button need to fire different methods.

### Request counter

  1. Create a route called **/request-counter**. Every time someone makes a request to this route, increment a number (starting from zero) 
    1. Store the value in a global variable named **counts**
    2. Redirect back to the root route
  2. Extend this feature to store different methods count in a global dict named **counts** where the keys are the method names: _GET, POST, PUT, DELETE_.
  3. Extend this feature to store the request count data in a text file named **request_counts.txt** instead of global variable. The file should be located next to your python file. (Take care when you open the file HINT: <http://stackoverflow.com/a/5137509>)  
The **request_counts.txt's** content should look something like this:  
 _"GET: 5_  
 _POST: 3  
_ _DELETE: 1  
PUT: 0"_



_HINT: to test DELETE/PUT request you can use curl after install it via apt get:<https://www.garron.me/en/bits/curl-delete-request.html> _

### Statistics

  1. Create a route called **/statistics**.
  2. Make a table that shows the **request_counts.txt** file's content.  
Method | Count  
---|---  
GET | 5  
POST | 3  
DELETE | 1  
PUT | 0  
  3. Make a link that navigates back to the root route.



