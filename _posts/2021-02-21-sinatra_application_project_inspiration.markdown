---
layout: post
title:      "Sinatra Application Project Inspiration"
date:       2021-02-21 22:28:56 +0000
permalink:  sinatra_application_project_inspiration
---


Over the past few years, cycling has become an important aspect of my life. I enjoy cycling for exercise, stress relief, outdoor adventure, and as a means of connecting with other cyclists. Cycling, as a low impact exercise, is accessible to people of all fitness levels and age groups. Bringing community members together through outdoor activity and exercise was the inspiration for my Sinatra application project. 

I decided to create an application which allows cyclists, who are local to a certain area, to post planned rides. Other application users have the ability to view posted rides and potentially meet for a "group ride". Users have the ability to sign up, log in, and log out of the application. Users can create their own rides as well as edit and delete them. Users cannot edit or delete rides created by other users, but they are able to view them. 

Establishing helper methods in my ApplicationController for identifying the current user and for redirecting users who are not logged in was essential in order to ensure that users were only able to edit and delete their own rides. 


```
helpers do 
    def current_user 
      User.find_by(id: session[:user_id])
    end 

    def redirect_if_not_logged_in 
      if !current_user 
        flash[:error] = "You must be logged in to perform that action."
        redirect '/login'
      end 
    end 
 end 
```

I used the above helper methods in my controller routes for both users and rides. The *#current_user* method is used in the UsersController to verify whether the user is already logged in to the application so they can be redirected accordingly. Both the *#current_user* method and the *#redirect_if_not_logged_in* method are used in the RidesController routes. Since the users are unable to view any ride information if they are not logged in, the *#redirect_if_not_logged_in* method proved extremely useful for each route in the RidesController.  The *#current_user* method is also used to ensure that the app’s current user is only able to edit their own rides as shown in the below code snippet.

```
    get '/rides/:id/edit' do
        redirect_if_not_logged_in
        @ride = Ride.find_by(id: params[:id])
        if @ride.user == current_user 
            erb :'rides/edit'
        else 
            flash[:error] = "You cannot edit another user's ride."
            redirect '/rides'
        end 
    end 
```
	
Creating a simple, yet functional Content Management System has been an exciting experience, and I plan to use it to connect with other cyclists in my area. I hope to continue adding functionality to this project as I learn more throughout the Flatiron Software Engineering Program.

	
