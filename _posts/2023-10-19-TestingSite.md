---
toc: true
comments: false
layout: post
title: Testing
description: 
type: hacks
courses: { compsci: {week: 9} }
---


<html>
<head>
    <title>Recipe Details</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
        }
        .container {
            text-align: center;
            margin-top: 50px;
        }
        .recipe-details {
            border: 2px solid #ccc;
            border-radius: 5px;
            padding: 10px;
            margin: 10px;
        }
        .recipe-details img {
            display: block;
            margin: 0 auto;
            max-width: 100%;
        }
        .recipe-details h2 {
            color: #FF5733; /* Change the color as desired */
        }
        .recipe-details h3 {
            color: #666; /* Subheading color */
        }
        .recipe-details ul {
            list-style-type: disc;
            padding-left: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Recipe Details</h1>
        <div class="search-box">
            <input type="text" id="recipeIdInput" class="search-input" placeholder="Enter Recipe ID">
            <button id="searchButton" class="search-button">Search</button>
        </div>
        <div id="recipeDetails"></div>
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", () => {
            const recipeIdInput = document.getElementById("recipeIdInput");
            const searchButton = document.getElementById("searchButton");
            const recipeDetails = document.getElementById("recipeDetails");

            // Event listener for the search button
            searchButton.addEventListener("click", () => {
                const recipeId = recipeIdInput.value;
                if (recipeId) {
                    // Clear previous recipe details
                    recipeDetails.innerHTML = "Loading...";

                    // API URL for a specific recipe
                    const apiUrl = `https://backendrocketmain.stu.nighthawkcodingsociety.com/api/recipe/recipedetails?id=${recipeId}`;

                    // Fetch data from the API based on the user's input
                    fetch(apiUrl)
                        .then(response => {
                            if (!response.ok) {
                                throw new Error(`Network response was not ok: ${response.status}`);
                            }
                            return response.json();
                        })
                        .then(data => {
                            // Display recipe details
                            displayRecipeDetails(data, recipeId);
                        })
                        .catch(error => {
                            console.error("There was a problem fetching the data:", error);
                        });
                }
            });

            // Function to display recipe details
            function displayRecipeDetails(recipe, recipeId) {
                // Clear previous recipe details
                recipeDetails.innerHTML = "";

                // Create an HTML element for the recipe
                const recipeElement = document.createElement("div");
                recipeElement.classList.add("recipe-details");

                // Display subheading with ID number
                const subheadingElement = document.createElement("h3");
                subheadingElement.textContent = `Recipe ID: ${recipeId}`;
                recipeElement.appendChild(subheadingElement);

                // Display picture
                const imgElement = document.createElement("img");
                imgElement.src = recipe.image;
                imgElement.alt = recipe.name;
                recipeElement.appendChild(imgElement);

                // Display name
                const nameElement = document.createElement("h2");
                nameElement.textContent = recipe.name;
                recipeElement.appendChild(nameElement);

                // Display ingredients as an unordered list
                const ingredientsElement = document.createElement("ul");
                const ingredients = recipe.ingredients.split("\n");
                ingredients.forEach(ingredient => {
                    const li = document.createElement("li");
                    li.textContent = ingredient;
                    ingredientsElement.appendChild(li);
                });
                recipeElement.appendChild(ingredientsElement);

                // Display instructions as an unordered list
                const instructionsElement = document.createElement("ul");
                const instructions = recipe.instructions.split("\n");
                instructions.forEach(instruction => {
                    const li = document.createElement("li");
                    li.textContent = instruction;
                    instructionsElement.appendChild(li);
                });
                recipeElement.appendChild(instructionsElement);

                // Add the recipe details to the page
                recipeDetails.appendChild(recipeElement);
            }
        });
    </script>
</body>
</html>
