---
toc: true
comments: false
layout: post
title: JS API Movie and TV Series Search Box
description: This search box uses JavaScript API so extract details from The Movie Database using an API created at that website. It then formats it to produce 8 major details, the name, the movie/series's poster, overview, rating, release date, genre, Mpaa rating aswell as using the input from the dynamic script and using it to search for trailers about the movie across youtube. Most of the code was done using the air of helpful tools such as my family, friends and chat, but I've done the code of the CSS formatting, genre and Mpaa maping. 
type: hacks
courses: { compsci: {week: 3} }
---

***Link to the original website:*** [The Movie Database (TMDb)](https://www.themoviedb.org/?language=en-US) 

<br><br>






<html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Movie/TV Series Search</title>
     <style>
        /* CSS styles for the search bar */
        #searchInput {
            width: 300px; 
            height: 40px; 
            font-size: 16px; 
            border-radius: 20px; 
            padding: 5px 10px; 
        }
    </style>

</head>
<body>
    <div class="container">
        <h1>Movie/TV Series Search</h1>
        <input type="text" id="searchInput" placeholder="Enter a movie or TV series name">
        <button id="searchButton">Search</button>
        <div id="result"></div>
    </div>

    <script>
        const searchInput = document.getElementById('searchInput');
        const searchButton = document.getElementById('searchButton');
        const resultDiv = document.getElementById('result');

        
        const apiKey = '8b9514e6242bb1620afcbec32775e783';

        
        const genreMap = {
               12: "Adventure",
               14: "Fantasy",
               16: "Animation",
               18: "Drama",
               27: "Horror",
               28: "Action",
               35: "Comedy",
               36: "History",
               37: "Western",
               53: "Thriller",
               80: "Crime",
               99: "Documentary",
               9648: "Mystery",
               10402: "Music",
               10749: "Romance",
               10751: "Family",
               10752: "War",
               10759: "Action & Adventure",
               10762: "Kids",
               10763: "News",
               10764: "Reality",
               10765: "Sci-Fi & Fantasy",
               10766: "Soap",
               10767: "Talk",
               10768: "War & Politics",
               878: "Science Fiction",
            
        };


       
        const mpaaRatingMap = {
            "G": "General Audiences",
            "PG": "Parental Guidance Suggested",
            "PG-13": "Parents Strongly Cautioned",
            "TV-14": "For TV Shows above 14",
            "R": "Restricted",
            "NC-17": "Adults Only",
            "NR": "Not Rated",
            "Unrated": "Unrated",
            
        };
        

        
        const languageMap = {
            "en": "English",
            "es": "Spanish",
            "fr": "French",
            "de": "German",
            "el": "Greek",
            "ga": "Irish",
            "hi": "Hindi",
            "ru": "Russian",
            "ta": "Tamil",
            "zh": "Chinese",
            "ko": "Korean",
            "ml": "Malayalam",
            
        };

        // Event listener for the search button
        searchButton.addEventListener('click', () => {
            const searchTerm = searchInput.value.trim();

            if (searchTerm) {

                resultDiv.innerHTML = '';

                
                fetchMovieData(searchTerm);
            }
        });

        
        function fetchMovieData(searchTerm) {
            // Construct the TMDb API URL for searching movies/TV series
            const apiUrl = `https://api.themoviedb.org/3/search/multi?api_key=${apiKey}&query=${encodeURIComponent(searchTerm)}`;

            
            fetch(apiUrl)
                .then((response) => response.json())
                .then((data) => {
                    if (data.results && data.results.length > 0) {
                        // Get the first result (most relevant)
                        const result = data.results[0];


                        const title = result.title || result.name || "Title: N/A";
                        const overview = result.overview || "Overview: N/A";
                        const ratings = result.vote_average
                            ? `Ratings: ${result.vote_average} / 10`
                            : "Ratings: N/A";
                        const releaseDate = result.release_date || result.first_air_date || "Release Date: N/A";
                        const formattedReleaseDate = formatDate(releaseDate);
                        const genre = result.genre_ids
                            ? `Genre: ${getGenre(result.genre_ids)}`
                            : "Genre: N/A";
                        const mpaaRating = result.content_ratings
                            ? `MPAA Rating: ${getMPAARating(result.content_ratings)}`
                            : "MPAA Rating: N/A";
                        const originalLanguage = result.original_language
                            ? `Original Language: ${getOriginalLanguage(result.original_language)}`
                            : "Original Language: N/A";
                        const posterPath = result.poster_path
                            ? `https://image.tmdb.org/t/p/w300${result.poster_path}`
                            : "https://via.placeholder.com/300x450"; // Placeholder image if no poster available;
                        const youtubeTrailerLink = getYouTubeTrailerLink(searchTerm);

                        
                        const updatedSummary = `
                            <h2>${title}</h2>
                            <img src="${posterPath}" alt="${title} Poster" style="max-width: 300px; height: auto;">
                            <p>${overview}</p>
                            <p>${ratings}</p>
                            <p>${formattedReleaseDate}</p>
                            <p>${genre}</p>
                            <p>${mpaaRating}</p>
                            <p>${originalLanguage}</p>
                            <p><a href="${youtubeTrailerLink}" target="_blank">Watch Trailer on YouTube</a></p>
                        `;

                        resultDiv.innerHTML = updatedSummary;
                    } else {
                        resultDiv.innerHTML = '<p>No results found.</p>';
                    }
                })
                .catch((error) => {
                    console.error('Error fetching data from TMDb:', error);
                });
        }

        
        function getGenre(genreIds) {
            const genres = genreIds.map((id) => genreMap[id] || "Unknown");
            return genres.join(', ');
        }

        
        function getMPAARating(contentRatings) {
            if (contentRatings && contentRatings.length > 0) {
                const rating = contentRatings[0].rating;
                return mpaaRatingMap[rating] || rating;
            } else {
                return "N/A";
            }
        }

        
        function getOriginalLanguage(languageCode) {
            return languageMap[languageCode] || "N/A";
        }

        
        function formatDate(dateString) {
            if (!dateString) return "Release Date: N/A";

            const date = new Date(dateString);
            const options = { year: 'numeric', month: '2-digit', day: '2-digit' };
            return "Release Date: " + date.toLocaleDateString('en-US', options);
        }

        
        function getYouTubeTrailerLink(searchTerm) {
            
            const youtubeSearchQuery = encodeURIComponent(`${searchTerm} trailer`);
            return `https://www.youtube.com/results?search_query=${youtubeSearchQuery}`;
        }
    </script>
</body>
</html>






<br><br><br><br><br>

<h3> Parts of the code </h3>


1. <b>fetchMovieData(searchTerm)</b> :This function is responsible for fetching and displaying movie/TV series data based on the search term entered by the user.<br><br>

2. <b>getGenre(genreIds)</b>: This function takes an array of genre IDs and returns a string containing the corresponding genre names. It's used to map genre IDs to their names.<br><br>

3. <b>getMPAARating(contentRatings)</b>: This function takes content ratings data and returns the MPAA rating in a user-friendly format. It maps MPAA ratings from codes to their full names.<br><br>

4. <b>getOriginalLanguage(languageCode)</b>: This function takes a language code and returns the full name of the language. It's used to display the original language of the movie/TV series.<br><br>

5. <b>formatDate(dateString)</b>: This function formats a date string (release date) in the "month/day/year" format. It's used to format the release date for display.<br><br>

6. <b>getYouTubeTrailerLink(searchTerm)</b>: This function constructs a YouTube trailer search link based on the search term entered by the user. It's used to provide a link to search for the movie's trailer on YouTube.<br><br>





<h3> Different mapping used in this code</h3>

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


<h3>Code explanation</h3>

<p>This JavaScript code is designed to create a simple web application for searching and displaying details about movies and TV series using the TMDb (The Movie Database) API. The code begins by defining event listeners, specifically for a search button click. When the search button is clicked, it triggers a function to fetch and display movie/TV series data.</p><br>

<p>Inside the fetchMovieData function, the TMDb API URL is constructed based on the user's search term, and a fetch request is made to the API. The received JSON data is processed to extract relevant information about the first result, such as title, overview, ratings, release date, genre, MPAA rating, original language, and poster image.</p><br>

<p>Notably, the release date is formatted using the formatDate function, and the genre and MPAA rating are looked up in predefined mapping objects (genreMap and mpaaRatingMap) to provide human-readable values. The code also constructs a link to search for a trailer on YouTube based on the user's search term.</p><br>

<p>The final result is an HTML page where users can enter a movie or TV series name, click the search button, and receive a summary of the selected media's details. If no results are found, a message indicating so is displayed. The code is structured to make the user interface clean and straightforward while providing rich information about the searched media.</p><br>


<h3>Utility fucntion explanation</h3>

<p>This code defines several utility functions that are used within the main code to format and retrieve specific information:</p><br>

1. getGenre(genreIds): This function takes an array of genre IDs as input and maps them to their corresponding genre names using the genreMap object. If a genre ID is not found in the map, it defaults to "Unknown" and returns a comma-separated string of genre names.<br><br>

2. getMPAARating(contentRatings): This function extracts the MPAA (Motion Picture Association of America) rating from the contentRatings array. It looks for the rating in the first element of the array and maps it to a human-readable rating using the mpaaRatingMap object. If no rating is found, it returns "N/A."<br><br>

3. getOriginalLanguage(languageCode): This function takes a language code as input and looks up the full language name from the languageMap object. If the language code is not found, it returns "N/A."<br><br>

4. formatDate(dateString): This function formats a date string (in the format provided by the TMDb API) into a more readable "Month/Day/Year" format using JavaScript's toLocaleDateString method. If the input date string is empty or undefined, it returns "Release Date: N/A."<br><br>

5. getYouTubeTrailerLink(searchTerm): This function constructs a YouTube search query for a trailer based on the user's search term. It appends " trailer" to the search term, encodes it for a URL, and returns a URL to the YouTube search results for that query.<br><br>

<p>These utility functions are crucial for transforming and presenting data retrieved from the TMDb API in a user-friendly and informative way within the web application. They handle tasks such as genre and rating mapping, date formatting, and generating YouTube trailer search links.</p><br>


<hr>JSON in JS</h3>
<br>
<p>In code, "JSON" stands for "JavaScript Object Notation." JSON is a lightweight data interchange format that is easy for humans to read and write and easy for machines to parse and generate. It is often used in programming to represent structured data, such as configuration settings, data exchanged between a server and a client, or data stored in files.</p><br>





<h4> Attribution </h4>

<center>
<img src = "_site/images/hellowe.png" alt= "The TMDb logo" width= "200" height= "200">
</center>
This product uses the TMDB API but is not endorsed or certified by TMDB
