# StopWatch

### Step 1: HTML
This is a simple stopwatch built using HTML, CSS, and JavaScript. 

The HTML file contains the basic structure of the stopwatch. It includes a div element with the id of "timer" that will display the time, and a div element with the id of "buttons" that will contain the start, stop, and reset buttons.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div id="timer">
        00:00:00</div>
    <div id="buttons">
        <button id="start">Start</button>
        <button id="stop">Stop</button>
        <button id="reset">Reset</button>
    </div>
   <footer> 🤟 RONAK SHARMA</footer>
    <script src="index.js"></script>
</body>
</html>
```

### Step 2: CSS
The CSS file contains the styles for the stopwatch. It includes styles for the timer and the buttons.
```css
#timer {
  font-size: 36px;
  font-weight: bold;
  text-align: center;
}

#buttons {
  display: flex;
  justify-content: space-around;
}

button {
  padding: 10px 20px;
  border-radius: 5px;
  background-color: #000;
  color: #fff;
  cursor: pointer;
}
```

### Step 3: JavaScript
The JavaScript file contains the logic for the stopwatch. It includes functions to start, stop, and reset the stopwatch.
```javascript
const timer = document.getElementById("timer");
const startButton = document.getElementById("start");
const stopButton = document.getElementById("stop");
const resetButton
 = document.getElementById("reset");

let startTime = 0;
let elapsedTime = 0;
let timerInterval;

function startTimer() {
  startTime = Date.now() - elapsedTime;

  timerInterval = setInterval(() => {
    elapsedTime = Date.now() - startTime;
    timer.textContent = formatTime(elapsedTime);
  }, 10);

  startButton.disabled = true;
  stopButton.disabled = false;
}

function formatTime(elapsedTime) {
  const milliseconds = Math.floor((elapsedTime % 1000) / 10);
  const seconds = Math.floor((elapsedTime % (1000 * 60)) / 1000);
  const minutes = Math.floor((elapsedTime % (1000 * 60 * 60)) / (1000 * 60));
  const hours = Math.floor(elapsedTime / (1000 * 60 * 60));
  return (
    (hours ? (hours > 9 ? hours : "0" + hours) : "00") +
    ":" +
    (minutes ? (minutes > 9 ? minutes : "0" + minutes) : "00") +
    ":" +
    (seconds ? (seconds > 9 ? seconds : "0" + seconds) : "00") +
    "." +
    (milliseconds > 9 ? milliseconds : "0" + milliseconds)
  );
}
function stopTimer() {
  clearInterval(timerInterval);
  startButton.disabled = false;
  stopButton.disabled = true;
}
function resetTimer() {
  clearInterval(timerInterval);

  elapsedTime = 0;
  timer.textContent = "00:00:00";

  startButton.disabled = false;
  stopButton.disabled = true;
}

startButton.addEventListener("click", startTimer);
stopButton.addEventListener("click", stopTimer);
resetButton
.addEventListener("click", resetTimer);
```
