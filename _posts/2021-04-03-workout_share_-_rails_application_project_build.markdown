---
layout: post
title:      "Workout Share - Rails Application Project Build"
date:       2021-04-03 10:18:01 -0400
permalink:  workout_share_-_rails_application_project_build
---


The ability to stay active and get exercise is a means of stress relief and an important aspect of maintaining both physical and mental health. After a year of elevated stress levels for many, due to the Covid-19 pandemic, I decided to create a Rails application that can allow users to track their progress as well as stay motivated through the ability to send and receive comments. A few aspects of creating this application proved challenging. 

### Challenge 1: Establish model relationships to meet the project requirements
The project required at least one has_many, at least one belongs_to, and at least two has_many :through relationships. At a minimum, I knew my application would include a User model and a Workout model. In order to meet the model relationship project requirements, I incorporated a Comment model to include a join table and establish two has_many :through relationships. My model relationships are set up as follows:

```
class User < ApplicationRecord
    has_many :workouts #workouts completed by user
    has_many :comments #comments given by user
    has_many :commented_workouts, through: :comments, source: :workout #workouts commented on by user
```
```
class Workout < ApplicationRecord
  belongs_to :user #user who created the workout
  has_many :comments #comments on a the workout
  has_many :users, through: :comments #users who commented on the workout
```
```
class Comment < ApplicationRecord
  belongs_to :user
  belongs_to :workout
```

### Challenge 2: Determine keys aspects of the user experience
Prior to building any views for my application, I needed to give some thought to how a user would interact with the final product. I wanted the user to be able to easily see their own progress through their personal summary page (*users#show*) and also be able to easily access all of the workouts posted by other users (*workouts#index*). Access to a workouts feed allows users to gain motivation and inspiration as well as leave comments. I also decided that users should be able to easily access a feed of all recent comments. 

### Challenge 3: Incorporate some style components
After building out the basic structure and functionality of the application, I incorporated some minor styling changes to elevate the appearance of the application. I came across several blog posts about incorporating CSS into Rails applications using the [materialize ruby gem](https://rubygems.org/gems/materialize-sass/versions/0.96.1) and decided to give it a try. By following some of the suggestions made in the blog posts, I was able to update my navigation bar and a few other elements of the application. The materialize gem provided a quick fix for incorporating basic styling. 

Using Rails to build this project from ideation to a fully functioning application required me to apply everything I learned in the curriculum thus far. It was gratifying to see all of the information put to use in creating a project of my own. I enjoyed creating my first Rails application and look forward to working on more Rails projects in the future.

