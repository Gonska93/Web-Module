# Assignment: Web with Python - ProMan

## BREAKING NEWS!

You won't believe it, but the previous team project has been closed!!! You did your best, delivered awesome results, and made the customer really happy, but he ran out of funds, and went seeking for an investor to raise some money for the project.

We all know, you are a little bit sad now, but life doesn't stop... A new customer came in today, with a totally new project idea. He doesn't have much money, but the project isn't that big either.

## Your job

Our business analysts and project managers sat down with the customer, and created a product backlog for the new project. Today everyone wants to create a new project management tool, and this customer is no exception either. He'd like to implement something similar to [Trello](https://trello.com), so that he can say he has his own tool (called ProMan)!

But life is never easy, the customer has it's favourite backend team, so he only gave our company the project's frontend side (at least the more interesting part). But the other team isn't ready with starting this project, so in the first sprint instead of integrating the frontend with the backend, you have to implement the persistency layer with JavaScript's local storage. Hopefully by next week, the backend team will be ready, but we'd like to be prepared to switch local storage to their solution easily.

## Product backlog

Please find the project's product backlog here:

<https://docs.google.com/spreadsheets/d/1rXNSIYEAqELlkHFP4ybq1Bd3WKn0eRCKz-c1G5Pbf5w>

### Technical requirements

#### Why do I need an application server for coding JS?

So this week you're mainly going to code in JavaScript, but things get scary and weird when doing that on a local html file running on your machine (what you access with file:// in your browser). Please read the following short article about the reasons behind here - and set aside for a sec it's about game development in JS, the problem is the same:

<http://phaser.io/tutorials/getting-started>

That's why you'll see a user story about setting up an application server (Flask will do the job as always), and now you know the reasons behind.

Please try to do your best, and implement all data persistency implementation (saving/retrieving data from local storage), so that it will be easier to change the local storage implementation to using a backend system for storing all our data in the next sprint.

#### Data handling

Please make sure that the data reading and writing functionality is separated into functions which can be used later if the backend part is replaced.

You can find _sample_data.json_ in the repository what shows an example how your data structure in localStorage should look like and also you can use it for testing in your local environment.

### Design requirements

As you have gained some knowledge in the previous assignments and SI week about user interface design, the [customer would love](http://binsbox.com/images/a-joke-on-customer-satisfaction/a-joke-on-customer-satisfaction0.jpg) to get an application which is easy to use at first glance, functionality is straightforward and looks nice on different screen sizes if possible.

They imagine the app as a 'one pager' where all the boards are shown and when one is clicked/opened then the corresponding cards are shown. Their screen plan is not too sophisticated but seems a good base for the work:

![proman_screen_plan.png](media/Web%20with%20Python%20module%20resources/proman_screen_plan.png)

[LINK](modules/12-web-and-sql-with-python-no-oop-4th-si-tw/active/media//Web%20with%20Python%20module%20resources/proman_screen_plan.png)

## GitHub Classroom project

Please find the relevant Classroom project here:

<https://classroom.github.com/g/1BeZaY8D>



