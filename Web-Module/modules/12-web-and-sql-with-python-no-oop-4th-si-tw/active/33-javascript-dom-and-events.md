# JavaScript, DOM and Events

## Let's go deeper in JS!

On the last SI week, you worked with basic JS scripts and learnt the syntax. Let's go deeper, and learn to use it in real situations.

## If you would like to test (yes, you want :))

To test some features you may need HTML code and javascript which manipulates it.

I suggest to always separate javascript code from your HTML files into a file with js extension. Not just avoid script tags with js code inside but avoid usage of event attributes (like onclick, ...) in HTML tags.

But how to import js file in your HTML? I suggest you to [read this answer](https://stackoverflow.com/a/24070373) and use script tags in the head section with defer attribute accordingly.

## And the new topics to learn

  * Please do these parts from the intermediate part of the **htmldog** tutorial: 
    * The DOM: <http://htmldog.com/guides/javascript/intermediate/thedom/>
    * Events and callbacks: <http://htmldog.com/guides/javascript/intermediate/events/>
    * JSON: <http://htmldog.com/guides/javascript/intermediate/json/>
    * Scope: <http://htmldog.com/guides/javascript/intermediate/scope/>
  * And these ones from the advanced part: 
    * Create/remove DOM elements: 
      * In several cases the usage of the innerHTML property is the easiest: <https://www.w3schools.com/jsref/prop_html_innerhtml.asp>
      * Another way: <http://htmldog.com/guides/javascript/advanced/creatingelements/>
    * Local storage: <http://htmldog.com/guides/javascript/advanced/localstorage/>
    * Errors and exceptions: <http://htmldog.com/guides/javascript/advanced/errors/>
  * In some point you will ask: "What is the nice way to pass data from HTML (if it is Python generated then from Python) to a javascript file". Please use data attributes then: <https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes>



## Some sweet candies from ECMA6

Good to know that this update added significant new syntax to javascript:

<https://en.wikipedia.org/wiki/ECMAScript#6th_Edition_-_ECMAScript_2015>

On the [http://es6-features.org](http://es6-features.org/#Constants) site please check the following ones from the new features:

  * Const (to define constants which are not changable): <http://es6-features.org/#Constants>
  * Let (block scoped variables instead of function scoped): <http://es6-features.org/#BlockScopedVariables>
  * Arrow functions (like python lambdas): <http://es6-features.org/#ExpressionBodies>
  * Template literals (multiline string with variables inside): <http://es6-features.org/#StringInterpolation>
    * Yes, you are right, it is a nice and readable way to manipulate DOM by defining HTML elements in a js string that you add to as an innerHTML property of a HTML element:  

        
                var ulIdComesFromSomewhereElse = 'id';  
        var divToHaveTheList = document.getElementById('divToHaveUl');  
          
        var ulText = `  
            <ul id="${ulIdComesFromSomewhereElse}">  
                <li>First</li>  
                <li>Second</li>  
                <li>Third</li>  
            </ul>  
        `;  
          
        console.log(ulText);  
        divToHaveTheList.innerHTML = ulText;




**Plase make sure that the two main topics of the week, the DOM manipulation and the event handling are clear to you.**

You can test it by creating HTML page with some tags and try to change one of them when another is clicked.

## You can be sure you learnt the intermediate level, if you can answer these questions:

  * What is the place to put javascript code if you have an HTML page?
  * What does DOM stand for?
  * How to select elements from the DOM with javascript
  * What is an event?
  * What is an event handler and what is a callback. Is there any difference?
  * How to run a javascript function when a button is clicked which has id 'button-id'?
  * How to run a javascript function when any of some buttons are clicked which have class 'button-class'?
  * What is JSON?
  * How to convert an object to/from JSON formatted string?
  * What is the difference between the scope of a variable in javascript and in python?
  * How to change the DOM (= DOM manipulation) with javascript?
  * What are the functions to put/take data to/from localStorage
  * How to catch an exception in javascript?
  * How to raise an exception in javascript?
  * Can you explain an elegant way to pass data from Python to a js file?
  * How to create a javascript element which you cannot change later
  * What to do if you want to make a loop variable not visible outside the loop?
  * How can you write a function without the function keyword?
  * What's the difference between the **var** and the **let** keywords?
  * Why can it be better to use ` than " or ' for creating strings?


