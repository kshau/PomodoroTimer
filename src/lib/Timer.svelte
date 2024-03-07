<script>
    
    var timerStatus = "Work";

    var minutes = 25;
    var seconds = 0;

    var timeDisplay;
    var startCtrl;
    
    var timerPaused = true;

    const timerInterval = setInterval(() => {

        if (!timerPaused) {

            if (seconds == 0) {

                if (minutes == 0) {

                    if (timerStatus == "Work") {
                        minutes = 3;
                        timerStatus = "Break";
                        document.body.style.backgroundColor = "rgb(124, 247, 157)";
                    }

                    else {
                        minutes = 24;
                        timerStatus = "Work";
                        document.body.style.backgroundColor = "rgb(221, 73, 73)";
                    }
                }

                else {
                    minutes--;
                }

                seconds = 60;

            }

            seconds--;
            timeDisplay.innerText = getTimeDisplay();

        }

    },  1000);

    function toggleTimer() {

        timerPaused = !timerPaused;

        if (timerPaused) {
            startCtrl.innerText = "Start";
        }

        else {
            startCtrl.innerText = "Stop";
        }
        
    }

    function getTimeDisplay() {
        
        return `${minutes.toString().padStart(2, "0")}:${seconds.toString().padStart(2, "0")}`;
        
    }

    function resetTimer() {

        timerPaused = true;
        startCtrl.innerText = "Start";

        minutes = 25;
        seconds = 0;

        timeDisplay.innerText = getTimeDisplay();

    }

</script>

<div class="container">

    <div class="timer">
        <h1 class="timeDisplay" bind:this={timeDisplay}>25:00</h1>
        <span class="status">{timerStatus} time!</span>
    </div>

    <div class="controls">
        <button class="startCtrl" on:click={toggleTimer} bind:this={startCtrl}>Start</button>
        <button class="resetCtrl" on:click={resetTimer}>Reset</button>
    </div>

</div>

<style>

    .container {
        display: flex;
        flex-direction: column;
    }

    .timeDisplay {

        font-size: 200px;
        color: white;
        background-color: rgb(27, 27, 27);
        border-radius: 60px;
        padding: 30px;

        width: fit-content;
        margin-left: auto;
        margin-right: auto;
        
    }

    .timer {
        text-align: center;
    }

    .status {
        font-size: 96px;
        position: relative;
        bottom: 100px;
    }

    .controls {
        display: flex;
        justify-content: center;
        background-color: rgb(34, 34, 34);

        width: fit-content;
        margin-left: auto;
        margin-right: auto;
        padding: 20px;
        border-radius: 20px;
    }

    .controls button {
        color: white;
        background-color: rgb(27, 27, 27);
        border-radius: 15px;
        border: 2px solid white;

        padding: 10px;
        margin: 10px;
        font-size: 50px;
    }

    .controls button:hover {
        background-color: rgb(54, 54, 54);
    }

</style>