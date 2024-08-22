import java.util.Random;
import java.util.Scanner;

public class Task1 {


    private static final int MaxAttempts = 10;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Random random = new Random();
        int score = 0;
        boolean playAgain = true;

        while (playAgain) {
            int numberToGuess = random.nextInt(100) + 1;
            int attempts = 0;
            boolean hasGuessedCorrectly = false;

            System.out.println("I have generated a number between 1 and 100. Can you guess it?");
            while (attempts < MaxAttempts && !hasGuessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = sc.nextInt();
                attempts++;

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You guessed the number correctly.");
                    hasGuessedCorrectly = true;
                    score += (MaxAttempts - attempts + 1);  // Higher score for fewer attempts
                } else if (userGuess < numberToGuess) {
                    System.out.println("you have guessed too low! Try again.");
                } else {
                    System.out.println("you have guessed too high! Try again.");
                }
            }

            if (!hasGuessedCorrectly) {
                System.out.println("ohh sryy, you have used all your attempts: " + numberToGuess);
            }

            System.out.println("Your current score : " + score);

            System.out.print("say yes if you want to play again? (yes/no): ");
            String response = sc.next();
            playAgain = response.equalsIgnoreCase("yes");
        }

        System.out.println("Thanks  for your  play! Your finalScore: " + score);
        sc.close();
    }
}
