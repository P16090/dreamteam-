<!DOCTYPE html>
<html>
<head>
    <title>Countdown Timer</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: black;
        }

        #countdown {
            font-size: 62px;
            color: red;
        }

        #countdown-label {
            font-size: 62px;
            color: red;
        }

        #centered-image {
            max-width: 100%;
            max-height: 80vh; /* Adjust this to control image height */
            margin-top: 20px; /* Adjust this to control the space between countdown and image */
            cursor: pointer; /* Add a cursor pointer to indicate it's clickable */
        }
    </style>
</head>
<body>
<div id="countdown-label">DREAM TEAM PREMIERE STARTS IN:</div>
<div id="countdown">Loading...</div>
<img id="centered-image" src="C:\Users\a.besimi\Desktop\wetransfer_dream-team-use_2023-09-14_1917\dream team use\team2.jpg" alt="Centered Image">

<audio id="background-audio" loop>
    <source src="C:\Users\a.besimi\Desktop\wetransfer_dream-team-use_2023-09-14_1917\dream team use\Kurtis Blow - Basketball (Official Video).mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>

<script>
    // Check if an end date is stored in local storage
    let endDate = localStorage.getItem('endDate');

    // If no end date is stored, set it to 1 week from the current date
    if (!endDate) {
        endDate = new Date();
        endDate.setDate(endDate.getDate() + 7);
        localStorage.setItem('endDate', endDate);
    }

    // Update the countdown every second
    const countdown = document.getElementById('countdown');
    const countdownLabel = document.getElementById('countdown-label');

    function updateCountdown() {
        const now = new Date();
        const timeLeft = new Date(endDate) - now;

        if (timeLeft <= 0) {
            countdown.textContent = "Countdown complete!";
        } else {
            const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

            countdown.textContent = `${days} DAYS, ${hours} HOURS, ${minutes} MINUTES, ${seconds} SECONDS`;
        }
    }

    // Function to start playing audio
    function playAudio() {
        const audio = document.getElementById('background-audio');
        audio.play();
    }

    // Attach click event to the image
    const centeredImage = document.getElementById('centered-image');
    centeredImage.addEventListener('click', playAudio);

    // Play audio automatically when the page is loaded
    window.addEventListener('load', playAudio);

    // Initial call to update the countdown
    updateCountdown();

    // Update the countdown every second
    setInterval(updateCountdown, 1000);
</script>
</body>
</html>

