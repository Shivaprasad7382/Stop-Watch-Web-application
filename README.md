Stopwatchwebapplication
<!DOCTYPE html>
<html>

<head>
    <title>Stopwatch</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>

<body>
    <div class="stopwatch">
        <h1 id="display">00:00:00</h1>
        <button onclick="startStop()">Start/Stop</button>
        <button onclick="reset()">Reset</button>
    </div>
    <script src="script.js"></script>
</body>

</html>
//css
.stopwatch {
    text-align: center;
    margin-top: 100px;
}

button {
    padding: 10px 20px;
    margin: 0 5px;
}
//javascript
let timer;
let isRunning = false;
let seconds = 0;
let minutes = 0;
let hours = 0;

function startTimer() {
    seconds++;
    if (seconds >= 60) {
        seconds = 0;
        minutes++;
        if (minutes >= 60) {
            minutes = 0;
            hours++;
        }
    }

    document.getElementById("display").textContent =
        (hours < 10 ? "0" + hours : hours) + ":" +
        (minutes < 10 ? "0" + minutes : minutes) + ":" +
        (seconds < 10 ? "0" + seconds : seconds);
}

function startStop() {
    if (isRunning) {
        clearInterval(timer);
        isRunning = false;
    } else {
        timer = setInterval(startTimer, 1000);
        isRunning = true;
    }
}

function reset() {
    clearInterval(timer);
    isRunning = false;
    seconds = 0;
    minutes = 0;
    hours = 0;
    document.getElementById("display").textContent = "00:00:00";
}
