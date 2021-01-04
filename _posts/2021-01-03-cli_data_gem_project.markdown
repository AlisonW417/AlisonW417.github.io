---
layout: post
title:      "CLI Data Gem Project"
date:       2021-01-03 19:38:49 -0500
permalink:  cli_data_gem_project
---


# Project Summary
Creating the CLI Data Gem Project marked the first milestone in my journey through the self-paced software engineering curriculum. I decided to scrape data from a recipe website, https://www.skinnytaste.com/. By using object oriented ruby, the user is presented with a list of recipe categories. The program then prompts the user through a sequence of selections to ultimately view a recipe's ingredient list and cooking instructions. 

My Skinnytaste Recipes project includes the below four classes:

**CLI Class** 

The CLI class is responsible for interacting with the user and displaying information about recipes from the Skinnytaste website.  The *#call* method in the CLI class brings the user through the entire cycle of the program. The user is first presented with a list of recipe categories. Once the user selects a category, they are presented with the option to choose a recipe. The user can then view the recipe's ingredient list and is given the option to view the instructions for the recipe. The user can either choose to continue selecting different categories and recipes, or they can exit the program.

**Scraper Class**

I chose to scrape data from three different sections on the Skinnytaste website. The first method of the scraper class (*.get_categories*) is responsible for scraping categories from the Skinnytaste recipe index and creating new instances of the Category class. The second method of the scraper class (*.get_recipes*) uses the url attribute for each category to scrape recipe information and create new instances of the recipe class. The final two methods of the scraper class (*.get_ingredients and .get_instructions*) use the url attribute for each recipe to scrape the ingredient and instruction lists and add them to corresponding arrays within the Recipe class. 

**Category Class**

Instances of the Category class are initialized with a name and url. A category has many recipes that can be accessed through the category's recipe attribute. The recipe attribute is set to an empty array upon initialization. Recipes can be added to a category by calling the *#find_recipes* method to access data scraped by the Scraper class. 
 
**Recipe Class**

Instances of the recipe class are initialized with a name, url, and category. Each instance of the recipe class is also initialized with ingredients and instructions attributes, which are set to empty arrays upon initialization. Recipes are added to their corresponding category at initialization via the *#add_to_category* method. This method checks to see if the category's recipe array already includes the recipe instance, and if it does not, it adds the instance to the category's recipes. The recipe class also includes methods that allow instances of the recipe class to *#find_ingredients* and *#find_instructions* by accessing data from the Scraper class. 

# Obstacles and Lessons Learned
My initial obstacle when beginning this project was selecting a suitable website for scraping information and creating an object oriented program. Watching the example live build videos provided in the CLI Project Planning Resources lesson was very helpful in overcoming this obstacle. While watching the videos, I was able to come up with the idea for my own project as well as begin building out my project's basic structure. 

Another obstacle I encountered was writing the code for the CLI class/controller while determining how the CLI class would interact with the program's other classes. To accomplish the ideal flow for my program, I used methods from my Category and Recipe classes to display data to the user. Some important considerations for coding the CLI class included verifying the validity of the user's input and ensuring that each step in the flow of the program was executed by calling the *#call* method in the program's executable file. Overall, building the CLI class reaffirmed the concept of using helper methods that allowed the program to run in the envisioned order. 

# Keeping it Simple

The advice I received from my educational coach regarding my first software engineering project was to "keep it simple." I was able to meet the project requirements and demonstrate my knowledge of object orientated ruby without creating an overly-complicated program. I am eager to continue my software engineering journey and create more complex programs in the future! 

