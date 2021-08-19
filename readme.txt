<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link href="style.css" rel="stylesheet" type="text/css" />

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap" rel="stylesheet">

  </head>
  <body>
    <div id="game-container">
      <h1>Magic 8 ball</h1>
      <p id="prompt">Ask what you will then click the 8-Ball to reveal the truth...</p>
      
      <input id="question" type="text" >

      <!-- TODO:: Call answerQuestion function when this is clicked. -->
      <div onclick="answerQuestion()"
       id="eight-ball">
        <div id="window">

          <!-- A "hidden" class will be added to this using javascript when an answer is shown. -->
          <div id="eight">8</div>

          <!-- A "hidden" class will be removed from these using javascript when an answer is shown. -->
          <div id="triangle" class="hidden"></div>
          <div id="answer-text" class="hidden"></div>
          
        </div>
      </div>
    </div>
    <script src="provided.js"></script>
    <script src="script.js"></script>
  </body>
</html>


/***** START PROVIDED JS CODE ******/

function makeAnswerAppear(answerText) {
  // Adds "hidden" CSS class to the '8'.
  document.getElementById("eight").classList.add("hidden");

  // Find the answer element, change the text, and remove the CSS "hidden" class.
  document.getElementById("answer-text").innerText = answerText;

  document.getElementById("answer-text").classList.add("hidden");
  document.getElementById("triangle").classList.add("hidden");

  // Allow 1/1000th of a second to pass in order for the above changes to take effect.  Then remove the elements
  setTimeout(() => {
    document.getElementById("answer-text").classList.remove("hidden");
    document.getElementById("triangle").classList.remove("hidden");
  }, 1);
}

/***** END PROVIDED JS CODE ******/

//script.js//

/* 
   Welcome to the Magic 8-ball Project.  Complete the 
   tasks outlined by the comments in this file.

   The following functions are available to you 
   (you can just call them):

   // This will hide the '8' (if shown) and 
   // show the triangle (if hidden).  It will
   // set the text on the triangle to the
   // string 'answerText'.
   function makeAnswerAppear(answerText)
*/


/* Returns a random integer in the range 'min' through 'max' inclusive. 

   This can be taken directly from MDN documentation: 
     https://tinyurl.com/3jkxa8h3

*/
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1) + min);
  }

/* Write a function that handles the magic 8-ball being clicked. Here are the steps:

   - Create an array containing at least 5 possible answers as strings.
   - Generate a random array index by calling 
       getRandomIntInclusive function.
   - Call 'makeAnswerAppear' using the random
       answer you selected.
   - (Level-up) Prevent your code from selecting the 
       same answer multiple times in a row 
       (loops could be required).
*/
 function answerQuestion() {
 let answerText = ["It is certain", "It is decidedly so" ,"Without a doubt", "Yes - definitely", "You may rely on it", "As I see it, yes", "Most likely", "Outlook good", "Yes", "Signs point to yes", "Don't count on it", "My reply is no", "My sources say no", "Outlook not so good", "Very doubtful", "Reply hazy, try again", "Ask again later", "Better not tell you now", "Cannot predict now", "Concentrate and ask again", "Are you Serious", "This is where I would put a response, IF I HAD ONE!!"]

 random = getRandomIntInclusive(0,21);
 
 makeAnswerAppear(answerText [random]);

 var result = '';
 var i = 0;
 do
  {
    i += 1;
    result += i + ' ';
}
while (i > 0 && i < 21);
// Despite i == 0 this will still loop as it starts off without the test
 }

//style.css//

#game-container { 
  width: 600px; 
  margin: 0 auto; 
  margin-top: 50px; 
  border: 2px dashed black;
  text-align: center; 
  font-family: "Open Sans", sans-serif; 
  font-weight: 100;
}

input {
  font-size: 22px;
  text-align: center;
  width: 240px;
}

#eight-ball {
  cursor: pointer;
  background-color: black;
  border: 4px solid rgb(95, 95, 95);
  border-radius: 50%;
  width: 300px;
  height: 300px;
  margin: 40px auto;
}

#window {
  position: relative;
  background-color: #333;
  border: 8px solid rgb(95, 95, 95);
  border-radius: 50%;
  width: 150px;
  height: 150px;
  margin: 75px auto;
  color: white; 
}

#eight {
  font-size: 5em;
  line-height: 150px;
}

#eight.hidden {
  display: none;
}

#triangle {
  position: absolute;
  top: 35px;
  left: 15px;
  width: 0; 
  height: 0; 
  border-left: 60px solid transparent;
  border-right: 60px solid transparent;
  border-top: 100px solid #56007a;
  transition-duration: 2s;
}

#triangle.hidden  {
  opacity: 0;
  transition-duration: 0s;
}

#answer-text {
  position: absolute;
  width: 60px;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -40%);
  font-size: 12px;
  transition-duration: 2s;
}

#answer-text.hidden {
  opacity: 0;
  transition-duration: 0s;
}