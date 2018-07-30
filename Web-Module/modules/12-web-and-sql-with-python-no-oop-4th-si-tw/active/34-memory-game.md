# Assignment: Memory game

## Description

The goal is to create a page, a bit similar to this: <https://codepen.io/natewiley/pen/HBrbL>

You cannot use code from the above example as this week we work yet with plain javascript.

## Submission

Use this link: <https://classroom.github.com/a/M2sgDeXD>

## How to start?

To make it work you will need some base knowledge in:

  1. Adding/changing elements to/of your HTML page from javascript
  2. Usage of event handlers in javascript (like do something when an element is clicked)



## Detailed description

First page:

  * Show a Flask generated html page.
  * It should show two dropdowns, one with numbers 1-8, other with 2, 4, 6, 8, with default value "please select a number" and a submit button
  * When both numbers (x, y) are selected and submit is clicked then we visit the server and generate out the second page



Second page:

  * Show a table (not necessarily a html table) with size x * y. Show the same image in all cell which will work as the back side of the "memory cards". Additionally [import ](https://stackoverflow.com/questions/436411/where-should-i-put-script-tags-in-html-markup/24070373#24070373)your javascript file on the page.
  * To show "images", please use the Font Awesome icon set because it is awesome (can be sized and colored like fonts. Why? Because they are fonts) 
    * You can get the link to the css file here: <https://www.bootstrapcdn.com/fontawesome/> (one version is <https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css>)
    * Import the css file in the head section of your HTML file
    * After it you can just put out icons using special classes on DOM elements. Example: <http://fontawesome.io/examples/>
    * Example icons: <http://fontawesome.io/icons/#web-application>
    * Summarizing: this way you can change the "image" by simply removing a font awesome class from a HTML element and put another font awesome class on it instead. Write a test and try to change the class from the developer toolbar of your browser



And here comes the fun (=write javascript code in your js file) part:

  * Randomize images to all cards which will be shown when they turn up. For example if you have a 5 * 4 cards, that means 20 cells and then you need 10 different images (2 pieces from each). Possible solution for 20 cards:
    * You can have an array with lots of images (image = string like "fa-camera-retro" which represents a font-awesome class)
    * You can fill up an array with 10 different images 
    * You can create an array which is like the first array two times after each other
    * You can shuffle the second array
  * When the user clicks one "back side" image then it should show the underlying real image ([changing classes](https://www.w3schools.com/jsref/prop_element_classlist.asp)).
  * If the user turns up the same two images consecutively then they stay turned up, otherwise they are turned back. Hints:
    * If user clicks an image which is already turned up then do nothing 
    * If unflipped card is clicked: You can have a variable to save if it is an odd click or an even. If it is odd then just turn up the card, if it is even then check if they are the same
      * You can use the array with the image classes (let's call imagesArray) to check the image of a card
      * So when a card is clicked then it can call the cardTurner function with its id and the function can find the corresponding image class in cardTurner
      * How can the button send its index? It is a bit tricky, you can read this page about the trap: <https://stackoverflow.com/questions/750486/javascript-closure-inside-loops-simple-practical-example>
        * Let me summarize: please use the **let** keyword instead of **var** in loops
    * When they are different then wait for 1-2 seconds before you turn them back
      * Check out setTimeout function of javascript
  * When all images are turned up then write out in a popup: "Congratulation :)"
    * for this you can have a counter which you increase when a pair is found and if all pairs are turned up then the games finishes



