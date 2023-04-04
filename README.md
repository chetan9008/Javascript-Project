<!DOCTYPE html>
<html>

<head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani&display=swap" rel="stylesheet">
    <title>
        Reaction Tester
    </title>
    <style>
        #area {
            background-color: blue;
            display: none;
            position: relative;
        }
        body {
    background-color: #323437;
    color: #cca618;
    letter-spacing: 1px;
    font-family: 'Rajdhani', sans-serif;
}

#css {
    font-size: 140%;
    font-weight: bold;
}
#line {
    font-size:120%;
}
    </style>
</head>

<body>
    <h1>Test Your reactions</h1>
    <p id="line">Click on the boxes or circles as quick as you can!</p>
    <div id="css">
        <p>Time taken :
            <span id="time"></span>
        <p>Best Score :<span id="Best"></span></p>
    </div>
    <div id="area">

    </div>
    <script>
        var timelap = [];
        function random() {
            var letter = "0123456789ABCDEF".split('');
            var color = "#";
            for (var i = 0; i < 6; i++) {
                color += letter[Math.floor(Math.random() * 15)];
            }
            return color;

        }


        var start = new Date(); // return day,month,date,year,time with hours,minutes,seconds,miliseconds
        start = start.getTime();// return miliseconds from 1970 
        function appear() {
            var top = Math.random() * 200;
            var left = Math.random() * 800;
            var width = Math.random() * 200;
            if (width < 150) {
                width = 150;
            }
            var radius;
            if (Math.random() > 0.5)
                radius = 0;
            else
                radius = 50;
            document.getElementById("area").style.backgroundColor = random();;
            document.getElementById("area").style.top = top + "px";
            document.getElementById("area").style.left = left + "px";
            document.getElementById("area").style.width = width + "px";
            document.getElementById("area").style.height = width + "px";
            document.getElementById("area").style.borderRadius = radius + "%";
            document.getElementById("area").style.display = "block";
            start = new Date().getTime();
        }
        function delay() {
            setTimeout(appear, Math.random() * 1500); //It is used to time out for given miliseconds
        }
        delay();
        var time;
        document.getElementById("area").onclick = function () {
            var end = new Date();
            end = end.getTime();
            document.getElementById("area").style.display = "none";
            time = end - start;
            time = time / 1000;
            timelap.push(time);
            document.getElementById("time").innerHTML = time + " seconds";
            document.getElementById("Best").innerHTML = Math.min(...timelap) + " seconds"; // find the shortest element in javascript
            delay();
        }



    </script>
</body>

</html> 
