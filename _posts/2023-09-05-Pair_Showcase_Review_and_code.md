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

<h3>Wikipedia Search Summary Code Explained<h3><br>

***HTML**
1. HTML Head

- Sets up important settings and the title for the web page.

2. HTML Body

- Holds the content, like the search box and area to show Wikipedia summaries.


<h3>CSS<h3>

1. Global Styles

Makes the whole page and buttons look nice.

2. Specific Styles

Makes the summary area and its text look nice.

<h3>JavaScript<h3>

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

