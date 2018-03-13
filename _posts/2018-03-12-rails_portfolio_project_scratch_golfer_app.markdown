---
layout: post
title:      "Rails Portfolio Project: Scratch Golfer App"
date:       2018-03-13 02:02:22 +0000
permalink:  rails_portfolio_project_scratch_golfer_app
---


After building my first fully functioning web application using the Sinatra framework, it was exciting to experience the power of using Ruby on Rails. I'm an avid golfer so I thought it would be cool to build an app that allows me to track my scores, courses I've played, and ultimately keep record of my handicap. For those who don't know, a handicap allows you to compare your talent level against the others you are playing with in order to make every round of golf competitive regardless of the spread of skill level across a group. 

**The Setup**

I knew my app would have to have models for users, courses, and rounds, so I began by setting up my migrations to address these different components of the app. A user would have a name, hometown, and handicap. A course would have a name, location, course rating, and slope rating. The course and slope rating are metrics that are used to compare how difficult one course is compared to another and are critical components of the formula that calculates a user's handicap. Each round would have a course_id because a round has to be played at a certain course, a time the course was entered, a score, and number of putts (a key metric for many golfers to track). The associations work as follows:

 - A user has many rounds and has many courses through rounds.
 - A course has many rounds and many users through rounds.
 - A round belongs to a user and belongs to a course.

Once I had this structure setup, I was ready to begin building my app.

**Satisfying the Project Requirements**

This portfolio project had several specific requirements, which were challenging to satisfy at times, but allowed me to more deeply understand the ins and outs of using the Ruby on Rails framework for application development. Below, I will outline the requirements and the steps I took to satisfy them, one by one.

1. **Use the Ruby on Rails framework.** Check.

2. **Incorporate a has_many, belongs_to, and has_many through association model.** Check - as outlined above between users, courses, and rounds.

3. **Include reasonable validations for simple attributes.**  Check - I made sure users have a name, rounds have a score and putts count, and courses have a name, city, state, slope, and rating. These are all simple validations, but are the most critical ones to ensure that my application functions appropriately.

4. **Include at least one class level ActiveRecord scope method.**  I added a scope method to the Round object model that allows for scoping down the round by user. Throug inclusion of this scope method, I am now able to call "lowest round by user" on the golfer's profile page so that when a user logs in they can be immediately reminded of their lowest round (and why they keep coming back for more golf despite the perpetual frustration it causes).

5. **Nested form that writes to an associated model through a custom attribute writer.** When a user goes in to the application to add a new round they've played, there are times when the course they played may not be in the database. In this event, the user needs to have the functionality to create a course and add their round at the same time. So, on the new round page, I've incorporated the ability for a user to add a course simultaneously which meets the requirement for a form writing to an associated model through a custom attribute writer.

6. **Standard user authentication system.** I incorporated the devise gem to ensure that my application had a standard signup and logout system. Since I'm incorporating Facebook as a login interface, the signup and sign-in process are essentially one and the same as long as the user has a Facebook profile.

7. **Allow login from some other service (e.g. Facebook).** As mentioned above, I incorporated the Facebook login service into my application. This was one of the more frustrating components of building my application as the local rails server address changes each time I launch the application in the Learn IDE which is why I'm looking forward to shifting to a local server after the completion/submission of this project. It was a great feeling to get my Facebook login working properly however.

8. **Make use of nested resources with the appropriate URLs.** I have a few different sets of nested resources in this application. For example, I have a users/#id/rounds route, a users/#id/courses route, a courses/#id/users route, and a courses/#id/rounds route. These are all the routes that naturally make sense for a user to want to navigate to. These allow a user to see all the rounds they or another user has played, all the courses they or another user has played, as well as all the users that have played a course and all the rounds that have been played at a course. The simplicity with which routes can be created and updated in a Rails application made this part of the project a smooth endeavor. The only tricky part is making sure my application's controllers and views responded correctly when navigating to these routes.

9. **Display validation errors on your forms.** When entering a new round or creating a new course, a validation error will pop up if any of the required fields are not entered by a user. An error would also display if a user's name was not entered upon signup/sign-in, but this should never happen due to the application having login functionality through Facebook, where a name is also required to sign up or login.

10. **App should be, within reason, DRY.**  At all times, I did my best to not repeat code unnecessarily. For example, I implemented partials for forms and information within each view sub-folder. I also created application wide methods such as a "current_user" method that allows the application to access the user_id of the active user. This is helpful when restricting access to certain functionality such as if a user were to try to add a round to a different user's profile. I am looking forward to continuing to refactor my code to make this application as DRY as possible as I continue to build it out beyond the submission of this project.

11. **Don't use scaffolding to build your project.** Check.

This was the most in-depth application I've built to date, but I thoroughly enjoyed the process. I learned a ton, and was able to build something that I would actually use in real life. I'm excited to continue building this out with additional functionality that would hopefully make this application useful for others as well. For example, I'd like to seed the application with all golf courses in the United States, build in functionality for users to book tee times online at the various courses, and even begin tailoring online lessons to users based on their current handicap. I think the opportunities for this application are endless for those who love golf which is why I enjoyed building this project so much.
