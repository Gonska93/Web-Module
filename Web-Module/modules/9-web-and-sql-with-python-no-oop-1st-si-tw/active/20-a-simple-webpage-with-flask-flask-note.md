# A simple webpage with Flask: Flask-Note

## Flask-Note

### Overview

In this tutorial, we will create a very simple "notebook". A notebook with only one functionality :)

This might be useful for you to keep some thoughts in one place. And to understand a Flask application.

### Step 1: Preparation

1\. Create a project folder. I'm gonna name it "flasknote":
    
    
    cd python-projects  // This is where I keep my projects  
    mkdir flasknote  
    cd flasknote

2\. Setup the magical virtualenv and activate it.

(virtualenv is a Python tool to allow installing libraries on a per-project basis.)  
To see the difference, we'll check the available Python packages before and after activating the virtualenv.

`pip freeze` (You shall see a lot of packages. These are your globally installed packages)  
`virtualenv venv` (This will create a **venv** folder with a lot of Python stuff included. Even Python itself)  
`source ./venv/bin/activate` (And this "activates" the virtualenv in your current terminal window)  
`pip freeze` (You should see no packages. Because you have none installed yet in the virtualenv)

After running the first `pip freeze` you saw the packages that are available to all of the applications on your computer. This could lead to different _(most commonly version mismatching)_ problems.

3\. Install Flask:
    
    
    pip install Flask

If you run `pip freeze` again, you should be some packages: _(the versions might differ by time)_
    
    
    click==6.7
    Flask==0.12.2
    itsdangerous==0.24
    Jinja2==2.9.6
    MarkupSafe==1.0
    Werkzeug==0.12.2

This is because Flask got installed into your virtualenv, and it requires 5 other libraries as dependencies.

If you want someone else to be able to collect exactly the same packages, you can write this list into a file (`pip freeze > requirements.txt`) and the other person can use this to install them (`pip install -r requirements.txt`)

### Step 2: Create the basic folder structure

Until we reach CSS and Javascript, we only have to create a folder for our HTML templates:
    
    
    mkdir templates

### Step 3: Creating a static HTML file a serving it on a route

1\. In your templates folder, create "index.html" with the following content:
    
    
    <!DOCTYPE html>  
    <html>  
        <head>  
            <meta charset="utf-8">  
            <title>Flask Note</title>  
        </head>  
        <body>  
            <h1>Flask Note</h1>  
            <p>This is gonna be my big note!</p>  
        </body>  
    </html>

1.1. Understand what this markup should do and try to explain it to someone!

  
2\. Create a Python file to run your server and name it "server.py":
    
    
    from flask import Flask, render_template  
      
    app = Flask(__name__)  
      
    @app.route('/')  # Register the 'http://localhost:5000 **/** ' route to this function.  
    def route_index():  # Just a normal function, I named it this way for cleaner code  
        return render_template('index.html')  # Okay, we render the index.html, then **return** it to the client.  
      
     if __name__ == "__main__":  
        app.run(  
            debug=True, # Allow verbose error reports  
            port=5000 # Set custom port  
        )

  
3\. Run your server:
    
    
    python server.py

3.1. Read what you got in the terminal. It's useful. Really.

  
4\. Open it up in a browser, check your site and be happy :)

### Step 4: Edit page

Okay, this site is pretty dumb. Let's add some actions to it!

1\. Create a new route, to handle the edit page. Add this code snippet under your previous route handling function in your "server.py":
    
    
      
    @app.route('/edit-note')  # Registering GET requests sent to 'http://localhost:5000 **/edit-note** ' to this function  
    def route_edit():  
        return render_template('edit.html')

2\. Now create this template. Create a new HTML file in your "templates" folder, called "edit.html" with this content:
    
    
    <!DOCTYPE html>  
    <html>  
        <head>  
            <meta charset="utf-8">  
            <title>Edit Flask Note</title>  
        </head>  
        <body>  
            <h1>Edit note</h1>  <!-- Page title -->  
            <form action="/edit-note" method="post">  <!-- This form will send it's data as a POST request to 'http://localhost:5000/edit-note' route when the user **submit** s the form-->  
                <label for="note-input">Note:</label>  <!-- Label for the textarea to help the user understand what is it for. -->  
                <textarea id="note-input" name="note" rows="8" cols="80"></textarea>  
                <button type="submit">Save note!</button>  <!-- Let's allow the user to **submit** the form. -- >  
            </form>  
        </body>  
    </html>

It's just a page with a form. The form includes a huge textarea and a submit button. Pay attention on the **form** tag and its attributes! This form _(on clicking the submit button)_ will send it's data to the "http://localhost:5000/edit-note" route in a **POST** request.

**Note:** don't include the whole URL in your links and action parameters, because it might change. Simply use "/edit-route" to let the browser figure out the domain name and port number.

3\. Now, we shall add a link to this edit page in the index page. Add the following snippet into your "index.html" after the closing **p** tag (" </p>"):
    
    
    <a href="/edit-note">Edit note</a>

4\. Let's test it!

  * Make sure your server is running, and open up the [index page](http://localhost:5000/).
  * You shall see the default text and the blue "Edit note" link.
  * Click it!
  * Now you should see the large textarea with the submit button.
  * If you try to submit your form now, you should get an error page: " **Not Found** ". Let's fix this:



5\. We will create a 3rd route to handle the form submission. In your "server.py" add "redirect, request, session" to the Flask imports. The first line should look like this now:
    
    
    from flask import Flask, render_template, redirect, request, session

  * redirect: helps us to jump back to the index page later, after we processed the form data.
  * request: holds the received form data in a dictionary
  * session: holds data stored in session. (more info later)



And add the following route:
    
    
    @app.route('/edit-note', methods=['POST'])  
    def route_save():  
         print('POST request received!')  
         return redirect('/')

This new route will only accept **POST** requests, so if you try to reach it via entering its address, you gonna get an the edit page template. :)  
  


6\. Save the new note:

In the previous step, we imported the **session** function from Flask. This will help us saving informations across page loads of the user. This means, the user can refresh the page, and data stored in the session will be kept for him/her.

To be able to work with sessions, we need some small magic. :) We need to add a secret key for the application that must reserve its value between restarts. Extend the last part of the **server.py** file as the following:
    
    
    if __name__ == "__main__":  
      app.secret_key = 'secret_key_change_this_please'  # Change the content of this string  
      app.run(  
          debug=True,  # Allow verbose error reports  
          port=5000  # Set custom port  
      )

_Please change the content of the **secret_key** string once you copied it into your codebase._

Let's add the following line before the **return** in the **route_save** function:
    
    
    session['note'] = request.form['note']

This will save our note for long term.

7\. Show the saved note in the index page. Update your **route_index** function to look like this:
    
    
    @app.route('/')  
     def route_index():  
        note_text = None  
        if 'note' in session:  
            note_text = session['note']  
        return render_template('index.html', note=note_text)

The modified code will read the note stored in the **session** if possible and forward it to the template.

Until now, we used static HTML files. However Flask supports templating engines to help including dynamic content in our templates. The default templating engine is [Jinja](http://jinja.pocoo.org/). For now, we only need a fraction of it's knowledge.

Let's remove the **< p>** tag entirely from **index.html** and replace it with the following snippet:
    
    
    <p>  
        {% if note is not none %}   
            {{ note }}  
        {% else %}  
            There is no saved notes.  
        {% endif %}  
    </p>

This way we can see an info text, if there is no saved note. And of course the note, if you saved one.

8\. Use the previously saved note on the edit page.

To make the site more useful, it would be nice to allow updating the old text, instead of always saving a new one. Read out the session in the **route_edit** function, the same way as in the **route_index**. It should look like this:
    
    
    @app.route('/edit-note')  
     def route_edit():  
        note_text = None  
        if 'note' in session:  # If we something already stored, then use that  
            note_text = session['note']  
        return render_template('edit.html', note=note_text)  # forward None or the stored note

And include the forwarded "note" template variable in the template. To "print" it into the html file, add "`{{ note }}`" (without the quotes) inside the <textarea> tag. Like this:
    
    
    <textarea id="note-input" name="note" rows="8" cols="80">{{ note }}</textarea>

When you call the `render_template` function, it will process this code "`{{ note }}`" to include the content of the `note` variable, passed to the `render_template`.

### Done ;)

That's it! You can now use this application like a notebook :)
