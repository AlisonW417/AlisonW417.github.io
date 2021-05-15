---
layout: post
title:      "Meal Planner App"
date:       2021-05-15 11:35:10 -0400
permalink:  meal_planner_app
---

## Building a single page application with HTML / CSS / JavaScript frontend and Rails API backend

Using JavaScript to create a single page “Meal Planner” application was the goal of this project build. The final application allows a user to plan and log recipes and create daily menus. Users are able to plan and prep their meals ahead of time as well as simplify and limit trips to the grocery store. 

I focused on building the project vertically, feature by feature, in order to reach the end result I envisioned. The main features I planned to implement for users were the ability to:

1. Read meal information and view associated ingredients (GET ‘/meals’)
2. Create new meals (POST ‘/meals’)
3. Add additional ingredients to meals (POST ‘/ingredients’)

As a supplementary feature, users can choose to select days and make a weekly meal plan. I found this weekly meal plan feature to be both challenging and exciting to execute. When a user selects a meal to view, a form with days of the week is rendered with an option to “add to meal plan.” When a user clicks this button, the renderMealPlan() function is invoked. The function is invoked with two arguments, the currently selected meal and the form itself. 

Inside the function, I first used the form data to determine which days the user selected. 
```
    // create a variable and set it equal to an empty array
    let days = [];
    // select the checkbox elements using their class name attribute
    let checkboxes = document.getElementsByClassName('form-check-input');
    // iterate through the form checkboxes to determine which days are checked
    // add each checked value (day) to the days array
    for (let i=0; i < checkboxes.length; i++) {
        if(checkboxes[i].checked){
            days.push(checkboxes[i].value);
        }
    }
```
Next, I iterated through the selected days and found the corresponding “menu” element to append the meal name to the appropriate day.
```
    days.forEach(day => {
        // use interpolation to select the current meal's div by category
        let mealDiv = document.getElementById(`${day}-${currentMeal.category.toLowerCase()}`);
        // create elements to display the meal's name and to remove the meal, if needed
        let mealName = document.createElement('p');
        mealName.setAttribute('class', 'card-text');
        let removeButton = document.createElement('button');
        removeButton.setAttribute('class', 'btn btn-danger')
        removeButton.innerText = "x";
        // add an event listener for the option to remove the meal from the menu
        removeButton.addEventListener('click', removeMealFromPlan);
        // reset the name to prevent duplicates during selection
        mealName.innerText = "";
        // add the current meal's name and the remove button to the selected div
        mealName.innerText = `${currentMeal.name}`;
        mealDiv.appendChild(mealName);
        mealName.appendChild(removeButton);
        // reset the form
        form.reset();
    })
```
I was happy to successfully add this functionality to my application as I feel it enhances the user’s experience and the overall usefulness of the application. A user who likes to plan meals ahead and prep ingredients in advance will find this feature particularly helpful. JavaScript allows the user to test out different meal combinations and explore different types of meals and ingredients while remaining on a single page.  

While working on this application, I learned a lot by simply testing out functions and using the console to debug any issues that arose. I hope to further hone my JavaScript skills through additional practice. 

