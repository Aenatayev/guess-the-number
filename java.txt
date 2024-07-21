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
