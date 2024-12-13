<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock-Paper-Scissors Game</title>
    <style>
        body {
            background-image: url(/download.png);
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }

        .container {
            margin: 50px auto;
            max-width: 500px;
            padding: 20px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        h1 {

            color: #333;
        }
 
        .instructions {
            font-size: 1.2em;
            color: #555;
            margin-bottom: 20px;
        }

        .choices {
            display: flex;
            justify-content: space-around;
            margin-bottom: 20px;
        }

        .choices img {
            width: 100px;
            height: 100px;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .choices img:hover {
            transform: scale(1.1);
        }

        .result {
            font-size: 1.2em;
            color: #333;
            margin-top: 20px;
        }

        .result img {
            width: 80px;
            height: 80px;
        }

        .play-again {
            margin-top: 20px;
        }

        .play-again button {
            padding: 10px 20px;
            font-size: 1em;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .play-again button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Rock-Paper-Scissors Game</h1>
        <p class="instructions">Choose Rock, Paper, or Scissors</p>
        <div class="choices">
            <img src="rock.png" alt="Rock" id="rock" />
            <img src="paper.png" alt="Paper" id="paper" />
            <img src="scissor.png" alt="Scissors" id="scissors" />
        </div>
        <div class="result" id="result"></div>
        <div class="play-again" id="play-again" style="display: none;">
            <button onclick="resetGame()">Play Again</button>
        </div>
    </div>

    <script>
        const choices = ["Rock", "Paper", "scissor"];
        const resultDiv = document.getElementById("result");
        const playAgainDiv = document.getElementById("play-again");

        document.getElementById("rock").addEventListener("click", () => playGame(0));
        document.getElementById("paper").addEventListener("click", () => playGame(1));
        document.getElementById("scissors").addEventListener("click", () => playGame(2));

        function playGame(userChoice) {
            const computerChoice = Math.floor(Math.random() * 3);

            const userSelection = choices[userChoice];
            const computerSelection = choices[computerChoice];

            let result = `<p>User chose: ${userSelection} <img src="${choices[userChoice].toLowerCase()}.png" alt="User choice"></p>`;
            result += `<p>Computer chose: ${computerSelection} <img src="${choices[computerChoice].toLowerCase()}.png" alt="Computer choice"></p>`;

            if (userChoice === computerChoice) {
                result += "<p>It's a draw!</p>";
            } else if ((userChoice === 0 && computerChoice === 2) || 
                       (userChoice === 1 && computerChoice === 0) || 
                       (userChoice === 2 && computerChoice === 1)) {
                result += "<p>You win!</p>";
            } else {
                result += "<p>Computer wins!</p>";
            }

            resultDiv.innerHTML = result;
            playAgainDiv.style.display = "block";
        }

        function resetGame() {
            resultDiv.innerHTML = "";
            playAgainDiv.style.display = "none";
        }
    </script>
</body>
</html>
