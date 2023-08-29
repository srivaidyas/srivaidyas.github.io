---
layout: default
title: Student Blog
---



## Sri's CSP Home Page
CSP Blog: August 2023 - June 2024

<br>
About Me: I'm Sri, a sophomore here at Del Norte, and I love to explore new places, bike and learn new stuff. I'm part of **Best Buddies** and **EIA**, a tutoring club at Del Norte. I've been to 4 countries around the world and a lot of places within ***San Deigo*** throughout my stay. <br><br>
Here's a little about me in the form of a ***freeform drawing***
<br>
<center>
<img src="images/IMG_9732-1.jpg" alt="aboutme" width="200" height="300">
</center>


<br>




#### Links to my Social sites
- Email: <srivaidyas@gmail.com>
- Instagram: _srivaidyas
- Snapchat: srivaidyas

#### My Favorite songs on YouTube
- [Last Night](https://www.youtube.com/watch?v=bUjPPBxbQrQ)
- [Daylight](https://www.youtube.com/watch?v=MoN9ql6Yymw)
- [Say Yes to Heaven](https://www.youtube.com/watch?v=MiAoetOXKcY&pp=ygURc2F5IHllcyB0byBoZWF2ZW4%3D)
<br><br>

### Here is a little mini game :)
<div>
<script>
    var question = 1
        function checkInput() {
            var userInput = document.getElementById("userInput").value;
            if (userInput == "10th" && question == 1) {
                document.getElementById("questionLabel").textContent = "Which year did I move to San Deigo?"
                document.getElementById("userInput").value = ""
                question = question + 1
            }
            if (userInput == "2022" && question == 2) {
                document.getElementById("questionLabel").textContent = "Name my #1 favorite song."
                document.getElementById("userInput").value = ""
                question = question + 1
                }
             if (userInput == "last night" && question == 3) {
                alert("You got everything right!")
                }
        }
    </script>
    <label id = "questionLabel" for="userInput">What grade am I in?</label>
    <input type="text" id="userInput">
    <button onclick="checkInput()">Submit</button>
</div> 