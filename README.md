import java.util.Scanner;
import java.util.Random;

public class NumberGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int maxAttempts = 5;
        int score = 0;
        boolean playAgain = true;
        int round = 1;

        System.out.println("Number Guessing Game");
        System.out.println("You need to guess a number between 1 and 100.");

        while (playAgain) {
            int numberToGuess = random.nextInt(100) + 1;
            int attempts = 0;
            boolean guessedCorrectly = false;

            System.out.println("\nRound " + round);

            while (attempts < maxAttempts) {
                System.out.print("Enter your guess (" + (attempts + 1) + "/" + maxAttempts + "): ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == numberToGuess) {
                    System.out.println("Correct! You guessed the number.");
                    guessedCorrectly = true;
                    score += (maxAttempts - attempts + 1); // More points for fewer attempts
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low. Try again.");
                } else {
                    System.out.println("Too high. Try again.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("You used all attempts. The correct number was: " + numberToGuess);
            }

            System.out.print("Do you want to play another round? (yes/no): ");
            String answer = scanner.next().toLowerCase();
            if (!answer.equals("yes")) {
                playAgain = false;
            }

            round++;
        }

        System.out.println("\nGame Over.");
        System.out.println("Total Score: " + score);
        scanner.close();
    }
}
