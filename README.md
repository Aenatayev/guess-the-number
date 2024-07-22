<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Guess the Number Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Guess the Number Game</h1>
        <p id="message">I'm thinking of a number between 1 and 100.</p>
        <input type="number" id="guessInput" placeholder="Enter your guess">
        <button id="guessButton">Submit</button>
        <p id="result"></p>
    </div>
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    text-align: center;
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    color: #333;
}

#guessInput {
    padding: 10px;
    width: 80%;
    margin-bottom: 10px;
}

#guessButton {
    padding: 10px 20px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#guessButton:hover {
    background-color: #218838;
}

#result {
    margin-top: 20px;
    font-weight: bold;
}
let numberToGuess = Math.floor(Math.random() * 100) + 1;
let attempts = 0;

document.getElementById('guessButton').addEventListener('click', function() {
    const userGuess = parseInt(document.getElementById('guessInput').value);
    attempts += 1;

    let message = '';

    if (userGuess < numberToGuess) {
        message = 'Too low! Try again.';
    } else if (userGuess > numberToGuess) {
        message = 'Too high! Try again.';
    } else {
        message = `Congratulations! You guessed the number in ${attempts} attempts. Starting a new game...`;
        startNewGame();
    }

    document.getElementById('result').textContent = message;
});

function startNewGame() {
    numberToGuess = Math.floor(Math.random() * 100) + 1;
    attempts = 0;
    document.getElementById('guessInput').value = '';
    document.getElementById('message').textContent = "I'm thinking of a number between 1 and 100.";
    document.getElementById('result').textContent = '';
}
