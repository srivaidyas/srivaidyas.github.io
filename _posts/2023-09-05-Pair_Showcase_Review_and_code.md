---
toc: True
comments: False
layout: post
title: Pair Showcase Code Explanation and Links
description: The code used for making the movie search box and the wikipedia search box are being explined below here. Each line defines each different function that was used including the pull and push factor and the ones used for the pull API data.
type: plans
courses: {'compsci': {'week': 3}}
---

#### JS Itunes API, JS Input, JS Output w/jquery, JS Output w/API.

***JS Grade Average Calculator (JS Input)***<br>
Explaining Functions and what they do!

- newInputLine(index): This function creates a new input box for scores, labels it, and sets it up to receive numeric input. It also handles setting the focus on the new input.
- calculator(event): This function calculates the total, count, and average of entered scores when the "Tab" or "Enter" key is pressed. It updates the webpage with these values and adds a new input box if all previous scores are valid numeric values.
- window.onload: This event ensures the first input box is created when the webpage loads, allowing users to start entering scores.

Link to calculator
[Javascript Average Calculator](https://srivaidyas.github.io/student//2023/08/30/JS_Calculator.html)<br>

***Colleges with fees table (JS Output w/jquery)***

Colleges Data Table

This Markdown code snippet represents an HTML table used to display information about the top 13 colleges. Here's a breakdown of its structure:

- The <table> tag starts the table.
- Inside, there's a <thead> section for column headers defined using <th> tags.
- The </thead> tag closes the header section.
- The <tbody> section contains data rows with each row enclosed in <tr> tags.
- In each data row, you use <td> tags for actual data cells.
- Finally, the </tbody> and </table> tags close the table.
- This format helps organize and to present colleges and data neatly on a blog like mine.<br>

Link to table
[Colleges Data Table](https://srivaidyas.github.io/student//2023/09/01/JS-Interactive-table-myversion_IPYNB_2_.html)

<br>

***JS Output with API***
<br>
Javascript Wikipedia Search with API

<h3>Wikipedia Search Summary Code Explained</h3><br>

***HTML**
1. HTML Head

- Sets up important settings and the title for the web page.

2. HTML Body

- Holds the content, like the search box and area to show Wikipedia summaries.


<h3>CSS</h3>

1. Global Styles

Makes the whole page and buttons look nice.

2. Specific Styles

Makes the summary area and its text look nice.

<h3>JavaScript</h3>

1. searchWikipedia() Function

- Runs when you click the "Search" button to get Wikipedia info.

2. Get Search Term

- Grabs what you typed in the search box.

3. Get Summary Area

- Finds the area where the summary will show up.

4. Clear Old Summary

- Removes any old summary so the new one can show.

5. Make API URL

- Puts together the web address to get Wikipedia data.

6. Fetch Data

- Goes to Wikipedia to get the summary.

7. Turn Into JSON

- Makes the fetched data easy to work with.

8. Show Summary

- Takes the Wikipedia summary and puts it on the web page.

9. Catch Errors

- If something goes wrong, it shows an error message.

[Wikipedia Search Bar](https://srivaidyas.github.io/student//2023/09/05/Wikipedia-Search_Bar.html)

<br><br>

***Python IO Input and Output Quiz***

Custom Quiz About Simple Python Functions
Quiz project in python
How to build your own quiz in python
<br>
In python there are a variety of ways to code a quiz. You can use basic print statements and input functions or you can use for loops to make the same quiz more concise.
<br>
The provided code is a basic quiz program that interacts with users. Here are the elements that make up most of the code:<br>

- import getpass, sys: This imports the modules.

- def question_with_answers(prompt): This defines a function that prints a question, collects user input as an answer, and stores the answer

- questions = 3: This is the total number of questions in the quiz.

- correct_answers = 0: This variable keeps track of the amout of correct answers.

- question_list: This list contains the questions for the quiz.

- ans_list: This list holds the correct answers corresponding to the questions.<br>

The for loop iterates over each question:

- rsp = question_with_answers(question_list[i]): This line asks the user a question and stores their response into a variable

- if ans_list[i] == rsp:: This checks if the user's response matches the correct answer.

- If the answer is correct, correct_answers added by one, and a success message is displayed.

- If the answer is incorrect, an print message is shown to help them know they got the question wrong<br>

At the end code displays a completion message for the quiz and calculates the user's percentage score.

<br>

Link to the Quiz<br>
[Python IO QUiz](http://127.0.0.1:4200/student//2023/08/25/quiz.py_IPYNB_2_.html)

<h3>JS API Movie Search Box</h3>

<br>

This search box uses JavaScript API so extract details from The Movie Database using an API created at that website. It then formats it to produce 8 major details, the name, the movie/series's poster, overview, rating, release date, genre, Mpaa rating aswell as using the input from the dynamic script and using it to search for trailers about the movie across youtube. Most of the code was done using the air of helpful tools such as my family, friends and chat, but I've done the code of the CSS formatting, genre and Mpaa maping.

<h4> Parts of the code </h4>


1. <b>fetchMovieData(searchTerm)</b> :This function is responsible for fetching and displaying movie/TV series data based on the search term entered by the user.<br><br>

2. <b>getGenre(genreIds)</b>: This function takes an array of genre IDs and returns a string containing the corresponding genre names. It's used to map genre IDs to their names.<br><br>

3. <b>getMPAARating(contentRatings)</b>: This function takes content ratings data and returns the MPAA rating in a user-friendly format. It maps MPAA ratings from codes to their full names.<br><br>

4. <b>getOriginalLanguage(languageCode)</b>: This function takes a language code and returns the full name of the language. It's used to display the original language of the movie/TV series.<br><br>

5. <b>formatDate(dateString)</b>: This function formats a date string (release date) in the "month/day/year" format. It's used to format the release date for display.<br><br>

6. <b>getYouTubeTrailerLink(searchTerm)</b>: This function constructs a YouTube trailer search link based on the search term entered by the user. It's used to provide a link to search for the movie's trailer on YouTube.<br><br>


<h4> Different mapping used in this code</h4>

<br>

1. Genre mapping <br>
            28: "Action", <br>
            12: "Adventure",<br>
            16: "Animation",<br>
            35: "Comedy",<br>
            80: "Crime",<br>
            99: "Documentary",<br>
            18: "Drama",<br>
            10751: "Family",<br>
            14: "Fantasy",<br>
            36: "History",<br>
            27: "Horror",<br>
            10402: "Music",<br>
            9648: "Mystery",<br>
            10749: "Romance",<br>
            878: "Science Fiction",<br>
            10770: "TV Movie",<br>
            53: "Thriller",<br>
            10752: "War",<br>
            37: "Western",<br>
<br>

2. Language Mapping <br>
            "en": "English",<br>
            "es": "Spanish",<br>
            "fr": "French",<br>
            "de": "German",<br>
            "el": "Greek",<br>
            "ga": "Irish",<br>
            "hi": "Hindi",<br>
            "ru": "Russian",<br>
            "ta": "Tamil",<br>
            "zh": "Chinese",<br>
            "ko": "Korean",<br>

<br>

3. MPAA rating mapping<br>
            "G": "General Audiences",<br>
            "PG": "Parental Guidance Suggested",<br>
            "PG-13": "Parents Strongly Cautioned",<br>
            "TV-14": "For TV Shows above 14",<br>
            "R": "Restricted",<br>
            "NC-17": "Adults Only",<br>
            "NR": "Not Rated",<br>
            "Unrated": "Unrated",<br>

<br>

Link to the movie search bar<br>
[Movie Search Bar](https://srivaidyas.github.io/student//2023/09/04/Movie_Search_Box.html)

