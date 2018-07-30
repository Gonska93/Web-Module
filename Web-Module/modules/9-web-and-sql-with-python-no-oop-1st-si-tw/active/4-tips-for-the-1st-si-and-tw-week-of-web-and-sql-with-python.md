# Tips for the 1st SI and TW week of Web and SQL with Python

## Overview

On this page, we tried to collected FAQs and common misunderstandings to help you, the future generation ;)

## HTML

### When to use a form and when a link?

When you need information from the user, then you will need a <form>. When you want to redirect the user to another route, you will need an <a> tag » a link. 

Redirecting the user means that you want the user to call another route, let your server do it's work and give the user another or the same page content than before.

### How to make the browser to pass back data? (not the user input way)

#### With a variable rules

Since Flask supports [variable rules](http://flask.pocoo.org/docs/0.12/quickstart/#variable-rules), you have an easy job. With this feature, you can pass even multiple data in a nice way.

#### With query parameters

The other way to pass something in the URL is the good'old [query parameter](https://en.wikipedia.org/wiki/Query_string).

You can find examples in this tutorial: <https://github.com/datademofun/flask-data-querystrings/blob/master/lesson-01.md>

#### With a hidden input

When you need to store some data on the client side, but you don't what him/her to see it or edit it, you can use a hidden input: <https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/hidden>

This might be useful on your TW week, to store the previously creation time as a timestamp and return it to the saving route.

### Input text or textarea?

It's a common question, when to use which. Our recommendation is to try to use `<input type="text">` tags for use input where it's possible. So try to avoid the `<textarea>`, and use it only when you want to allow the user to enter multiple lines of data.

### How to use an image as a link?

Our recommendation is simple: Put an image into a link:
    
    
    <a href="{{ url_for('delete_post', post_id=post.id) }}">  
        <img href="{{ url_for('static', filename='images/logo.png') }}">  
    </a>

In this example, you can also see the usage of the `url_for` function for a route with a variable and for a static file, stored in **static/image/logo.png**.

A usual antipattern is the usage of a `<form>` and an `<input type="image" src="..">` element within. You would get a similar behavior, but we do not recommend it. It leads to unfollowable and hard to undestand code, since this image type is actually behaving like a submit button. But it's not written anywhere... crazy... Also, read the first quest, why we don't recommend usage of a `<form>` for this purpose. Please use a link :)

## Jinja

### How to pass a variable and use it in a template?

When you have a route function like this:
    
    
    def route_index():  
        navigation = [{  
            'href': '/',  
            'caption': 'Home'  
        },{  
            'href': '/contact',  
            'caption': 'Contact us'  
        }]  
      
        return render_template('index.html', navigation=navigation, a_variable=42)  # Meaning of life

You can show the passed values like this:
    
    
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <title>My Webpage</title>
    </head>
    <body>
        <ul id="navigation">
            {% for item in navigation %}
                <li>  
                    <a href="{{ item.href }}">{{ item.caption }}</a>  
                </li>
            {% endfor %}
        </ul>
    
        <h1>My Webpage</h1>
        {{ a_variable }}
    
        {# a comment #}
    </body>
    </html>

Template source: [The Jinja documentation](http://jinja.pocoo.org/docs/2.9/templates/)

### How to reach the iteration counter in loops?

Jinja provides some variables for you to use in a loop. You can find them in the documentation: <http://jinja.pocoo.org/docs/2.9/templates/#for>

### Select the "selected" <option> in a <select>

The nicest way to handle a <select> tag it generating it's content from a list of values. Ex.:
    
    
    <select name="country" id="country_selector">
        {% for country in countries %}
            <option value="{{country}}" {{'selected' if selected_country==country else ''}}>{{country}}</option>
        {% endfor %}
     </select>

To make this work, you'll need a route like this:
    
    
    def route_edit():  
        countries = ['Hungary', 'Poland', 'Germany', 'Italy']  
        current = magic.get_selected_country()  # One of the options  
      
        return render_template('edit.html', countries=countries, selected_country=current)

### Ternary operators in Jinja

It is possible to use inline if expressions. These are useful in some situations. For example, you can use this to show a different title if a variable is defined, otherwise from the default title:
    
    
    <h1>{{ 'Edit ' + item_title if item_title is defined else 'Add new item' }}</h1>
    

The general syntax is `<do something> if <something is true> else <dosomething else>`.

The else part is optional. If not provided, the else block implicitly evaluates into an undefined object:
    
    
    {{ 'Magic!' if is_magic_happened }}

## Flask & Python

### How to handle POST and GET requests with the same route?

It is possible to set the same route for different methods in 2 ways:

#### One route function + condition
    
    
    @app.route('/edit-note', methods=['GET', 'POST'])

### Handling id values when working with a .csv file

### How to structure a Flask application?
