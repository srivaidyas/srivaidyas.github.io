---
toc: True
comments: False
layout: post
title: Wikipedia Search Box
description: This is a search box that uses Wikipedia's API to give the user a summary of what ever they have typed in to the box. The summary includes the main points as well as a togo reading for the user.
type: hacks
courses: {'compsci': {'week': 3}}
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wikipedia Search</title>
    <style>
        body {
            background-color: #1a1a1a;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        h1 {
            background-color: #333333;
            color: #ffffff;
            text-align: center;
            padding: 10px;
        }

        input[type="text"], button {
            padding: 10px;
            margin: 10px;
            font-size: 16px;
            background-color: #333333;
            color: #ffffff;
            border: none;
            border-radius: 5px;
        }

        input[type="text"]::placeholder {
            color: #999999;
        }

        button:hover {
            cursor: pointer;
            background-color: #555555;
        }

        #summary {
            margin: 20px;
            padding: 20px;
            background-color: #333333;
            border-radius: 5px;
        }

        h2 {
            color: #ffcc00;
        }

        p {
            color: #ffffff;
        }
    </style>
</head>
<body>
    <h1>Wikipedia Summary</h1>
    <input type="text" id="searchInput" placeholder="Enter a search term">
    <button onclick="searchWikipedia()">Search</button>
    <div id="summary"></div>

    <script>
        function searchWikipedia() {
            const searchInput = document.getElementById('searchInput').value;
            const summaryContainer = document.getElementById('summary');

            // Clear previous summary
            summaryContainer.innerHTML = '';

            // Wikipedia API URL to get the summary of the first search result
            const apiUrl = `https://en.wikipedia.org/w/api.php?action=query&format=json&prop=extracts&exintro=true&explaintext=true&origin=*&titles=${searchInput}`;

            // Make an API request
            fetch(apiUrl)
                .then(response => response.json())
                .then(data => {
                    const pages = data.query.pages;
                    const firstPageId = Object.keys(pages)[0];
                    const firstPage = pages[firstPageId];
                    
                    if (firstPage) {
                        const title = firstPage.title;
                        const extract = firstPage.extract;

                        if (extract) {
                            summaryContainer.innerHTML = `<h2>${title}</h2>${extract}`;
                        } else {
                            summaryContainer.innerHTML = '<p>No summary found for this article.</p>';
                        }
                    } else {
                        summaryContainer.innerHTML = '<p>No results found.</p>';
                    }
                })
                .catch(error => {
                    console.error('Error fetching data:', error);
                });
        }
    </script>
</body>
</html>