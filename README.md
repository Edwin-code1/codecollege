<!DOCTYPE html>
<html>
  <head>
    <title class="main">Rock Paper Scissors</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="style2.css">
  </head>
  <body>
    <div class="container">
      <h1>Rock Paper Scissors</h1>
      <div class="game">
        <div class="choices">
          <button id="rock">Rock</button>
          <button id="paper">Paper</button>
          <button id="scissors">Scissors</button>
        </div>
        <div class="results">
          <p id="result"></p>
          <p id="score"></p>
          <button id="play-again">Play Again</button>
        </div>
      </div>
    </div>
    <script>
      let userScore = 0;
      let computerScore = 0;
      const getUserChoice = (userInput) => {
        userInput = userInput.toLowerCase();
        if (userInput === "rock" || userInput === "paper" || userInput === "scissors") {
          return userInput;
        } else {
          console.log("Error, please type: rock, paper or scissors");
        }
      };

      const getComputerChoice = () => {
        const randomNumber = Math.floor(Math.random() * 3);
        switch (randomNumber) {
          case 0:
            return "rock";
          case 1:
            return "paper";
          case 2:
            return "scissors";
        }
      };

      const determineWinner = (userChoice, computerChoice) => {
        if(userChoice === computerChoice) {
         return "This game is a tie";
        }
        if (userChoice ==="rock"){
           if( computerChoice === "paper") {
            computerScore++;
           return "Sorry, computer won!";
           } else {
            userScore++;
            return "Congratulations, you won!";
           }
        }
        if(userChoice === "paper"){
          if(computerChoice === "scissors") {
            computerScore++;
            return "Sorry, computer won!";
          } else {
            userScore++;
            return "Congratulations, you won!";
          }
        }
        if(userChoice === "scissors") {
          if(computerChoice === "rock") {
            computerScore++;
            return "Sorry, computer won!";
          } else {
            userScore++;
            return "Congratulations, you won!";
          }
        }
      };

      const playGame = () => {
        const rockButton = document.getElementById("rock");
        const paperButton = document.getElementById("paper");
        const scissorsButton = document.getElementById("scissors");
        const playAgainButton = document.getElementById("play-again");
        const resultParagraph = document.getElementById("result");
        const scoreParagraph = document.getElementById("score");

        rockButton.addEventListener("click", () => {
          const userChoice = getUserChoice("rock");
          const computerChoice = getComputerChoice();
          resultParagraph.textContent = determineWinner(userChoice, computerChoice);
          scoreParagraph.textContent = "User score: " + userScore + " Computer score: " + computerScore;
        });

        paperButton.addEventListener("click", () => {
          const userChoice = getUserChoice("paper");
          const computerChoice = getComputerChoice();
          resultParagraph.textContent = determineWinner(userChoice, computerChoice);
          scoreParagraph.textContent = "User score: " + userScore + " Computer score: " + computerScore;
        });

        scissorsButton.addEventListener("click", () => {
  const userChoice = getUserChoice("scissors");
  const computerChoice = getComputerChoice();
  resultParagraph.textContent = determineWinner(userChoice, computerChoice);
  scoreParagraph.textContent = "User score: " + userScore + " Computer score: " + computerScore;
});

        playAgainButton.addEventListener("click", () => {
      userScore = 0;
      computerScore = 0;
      resultParagraph.textContent = "";
      scoreParagraph.textContent = "User score: " + userScore + " Computer score: " + computerScore;
    });
  };

  playGame();
</script>
