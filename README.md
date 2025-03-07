<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Holi Celebration</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Festive&display=swap');

        body {
            background-color: #fff3e0;
            overflow: hidden;
            font-family: 'Pacifico', cursive;
            text-align: center;
        }

        .popup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 15px rgba(0,0,0,0.3);
            display: none;
            z-index: 10;
            text-align: center;
            font-size: 24px;
        }

        .popup h2 {
            font-family: 'Festive', cursive;
            color: #e74c3c;
            font-size: 32px;
        }

        .popup button {
            background-color: #ff9800;
            border: none;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            color: white;
            border-radius: 5px;
            margin-top: 15px;
        }

        .popup button:hover {
            background-color: #e65100;
        }

        .color-splash {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
            opacity: 0;
            animation: splash 1s linear infinite;
        }

        @keyframes splash {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(4); opacity: 0; }
        }
    </style>
</head>
<body>
    <audio id="holiSong" autoplay loop>
        <source src="128-Jogi Ji Dheere Dheere - Nadiya Ke Paar 128 Kbps.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>

    <div id="popup1" class="popup">
        <h2>Happy Holi Sabar!</h2>
    </div>

    <div id="popup2" class="popup">
        <h2>To move forward, click Enjoy!</h2>
        <button onclick="showPopup3()">Enjoy</button>
    </div>

    <div id="popup3" class="popup">
        <h2>Bina tumhe rang lagaye kahi Fagun laut na jaye!</h2>
    </div>

    <script>
        function createColorSplash() {
            let splash = document.createElement("div");
            splash.classList.add("color-splash");
            splash.style.left = Math.random() * window.innerWidth + "px";
            splash.style.top = Math.random() * window.innerHeight + "px";
            splash.style.backgroundColor = `rgb(${Math.random()*255}, ${Math.random()*255}, ${Math.random()*255})`;
            document.body.appendChild(splash);

            setTimeout(() => {
                splash.remove();
            }, 1000);
        }

        function showPopup(id) {
            document.getElementById(id).style.display = "block";
            for (let i = 0; i < 20; i++) {
                setTimeout(createColorSplash, i * 100);
            }
        }

        function showPopup3() {
            document.getElementById("popup2").style.display = "none";
            showPopup("popup3");
        }

        window.onload = function() {
            document.getElementById("holiSong").play();
            showPopup("popup1");
            setTimeout(() => {
                document.getElementById("popup1").style.display = "none";
                showPopup("popup2");
            }, 5000);
        }
    </script>
</body>
</html>
