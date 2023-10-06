# Codsoft_Task1

import java.util.Random;
import java.util.Scanner;

public class GuessingGame {

    private static final int MAX_RANGE = 100;
    private static final int MAX_ATTEMPTS = 5;

    private Random random;
    private int randomNumber;
    private int userGuess;
    private int numAttempts;
    private int score;

    public GuessingGame() {
        random = new Random();
        randomNumber = random.nextInt(MAX_RANGE) + 1;
        numAttempts = 0;
        score = 0;
    }

    public void play() {
        System.out.println("Welcome to the guessing game!");
        System.out.println("You have " + MAX_ATTEMPTS + " attempts to guess the correct number.");

        while (numAttempts < MAX_ATTEMPTS) {
            numAttempts++;

            System.out.println("Enter your guess: ");
            Scanner scanner = new Scanner(System.in);
            userGuess = scanner.nextInt();

            if (userGuess == randomNumber) {
                System.out.println("Congratulations! You guessed the correct number.");
                score++;
                break;
            } else if (userGuess > randomNumber) {
                System.out.println("Your guess is too high.");
            } else {
                System.out.println("Your guess is too low.");
            }
        }

        if (numAttempts == MAX_ATTEMPTS) {
            System.out.println("Sorry, you ran out of attempts.");
            System.out.println("The correct number was: " + randomNumber);
        }

        System.out.println("Your score is: " + score);
    }

    public void playAgain() {
        System.out.println("Would you like to play again? (Y/N)");
        Scanner scanner = new Scanner(System.in);
        String answer = scanner.nextLine();

        if (answer.equalsIgnoreCase("Y")) {
            randomNumber = random.nextInt(MAX_RANGE) + 1;
            numAttempts = 0;
            play();
        } else {
            System.out.println("Thank you for playing!");
        }
    }

    public static void main(String[] args) {
        GuessingGame game = new GuessingGame();
        game.play();
        game.playAgain();
    }
}
