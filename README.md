import java.util.Scanner;

public class QuizApp {
    private FlashcardDeck deck;
    private Scanner scanner;

    public QuizApp() {
        this.deck = new FlashcardDeck();
        this.scanner = new Scanner(System.in);
    }

    public void addFlashcard(String question, String answer) {
        deck.addFlashcard(question, answer);
    }

    public void runQuiz() {
        int score = 0;
        int totalQuestions = deck.getSize();

        for (int i = 0; i < totalQuestions; i++) {
            Flashcard flashcard = deck.getFlashcard(i);
            if (flashcard != null) {
                System.out.println("Question " + (i + 1) + ": " + flashcard.getQuestion());
                System.out.print("Your answer: ");
                String userAnswer = scanner.nextLine();

                if (userAnswer.equalsIgnoreCase(flashcard.getAnswer())) {
                    System.out.println("Correct!\n");
                    score++;
                } else {
                    System.out.println("Incorrect. The correct answer is: " + flashcard.getAnswer() + "\n");
                }
            }
        }

        System.out.println("Quiz complete!");
        System.out.println("Your score: " + score + " out of " + totalQuestions);
    }

    public static void main(String[] args) {
        QuizApp quizApp = new QuizApp();

        // Adding sample flashcards
        quizApp.addFlashcard("What is the capital of France?", "Paris");
        quizApp.addFlashcard("What is the largest planet in our solar system?", "Jupiter");
        quizApp.addFlashcard("Who wrote 'Hamlet'?", "William Shakespeare");

        // Running the quiz
        quizApp.runQuiz();
    }
}
