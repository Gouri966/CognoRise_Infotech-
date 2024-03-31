# CognoRise_Infotech-
Hangman_Game
import java.util.Scanner;
	import java.util.Random;

	public class Hangman {
	    public static void main(String[] args) {
	        String[] words = {"java", "programming", "computer", "algorithm", "code", "developer", "debug", "software"};
	        Random random = new Random();
	        Scanner scanner = new Scanner(System.in);

	        String wordToGuess = words[random.nextInt(words.length)];
	        int attempts = 6;
	        char[] guessedWord = new char[wordToGuess.length()];
	        boolean[] guessedLetters = new boolean[26]; // to keep track of guessed letters

	        for (int i = 0; i < wordToGuess.length(); i++) {
	            guessedWord[i] = '_';
	        }

	        while (attempts > 0) {
	            System.out.println("Word to guess: " + new String(guessedWord));
	            System.out.println("Attempts left: " + attempts);
	            System.out.print("Enter a letter: ");
	            char guess = scanner.next().charAt(0);

	            if (guessedLetters[guess - 'a']) {
	                System.out.println("You've already guessed that letter!");
	                continue;
	            }

	            guessedLetters[guess - 'a'] = true;

	            boolean found = false;
	            for (int i = 0; i < wordToGuess.length(); i++) {
	                if (wordToGuess.charAt(i) == guess) {
	                    guessedWord[i] = guess;
	                    found = true;
	                }
	            }

	            if (!found) {
	                System.out.println("Incorrect guess!");
	                attempts--;
	            }

	            boolean allLettersGuessed = true;
	            for (char c : guessedWord) {
	                if (c == '_') {
	                    allLettersGuessed = false;
	                    break;
	                }
	            }

	            if (allLettersGuessed) {
	                System.out.println("Congratulations! You've guessed the word: " + wordToGuess);
	                break;
	            }
	        }

	        if (attempts == 0) {
	            System.out.println("You ran out of attempts. The word was: " + wordToGuess);
	        }

	        scanner.close();
	    }
	}
