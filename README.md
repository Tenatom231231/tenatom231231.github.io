<!DOCTYPE html>
<html>
<head>
  <title>My Game</title>
</head>
<body>
  <canvas id="canvas" width="500" height="500"></canvas>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.12.0/p5.min.js"></script>
  <script>
    var canvas = document.getElementById("canvas");
    var ctx = canvas.getContext("2d");
    var ball = {
      x: 250,
      y: 250,
      speedX: 5,
      speedY: 5
    };

    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "black";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "red";
      ctx.fillCircle(ball.x, ball.y, 50);

      ball.x += ball.speedX;
      ball.y += ball.speedY;

      if (ball.x < 0 || ball.x > canvas.width) {
        ball.speedX = -ball.speedX;
      }

      if (ball.y < 0 || ball.y > canvas.height) {
        ball.speedY = -ball.speedY;
      }
    }

    window.addEventListener("keydown", function(event) {
      if (event.keyCode == 38) {
        ball.speedY = -5;
      } else if (event.keyCode == 40) {
        ball.speedY = 5;
      } else if (event.keyCode == 37) {
        ball.speedX = -5;
      } else if (event.keyCode == 39) {
        ball.speedX = 5;
      }
    });

    setInterval(draw, 20);
  </script>
</body>
</html>
