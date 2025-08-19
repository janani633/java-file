import java.util.*;

public class VotingSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

         Candidates list
        String[] candidates = {"Alice", "Bob", "Charlie"};
        int[] votes = new int[candidates.length];

        System.out.println("===== Voting System =====");
        System.out.println("Candidates:");
        for (int i = 0; i < candidates.length; i++) {
            System.out.println((i + 1) + ". " + candidates[i]);
        }

        System.out.print("\nEnter number of voters: ");
        int voters = sc.nextInt();

         Voting process
        for (int i = 0; i < voters; i++) {
            System.out.print("Voter " + (i + 1) + ", enter your vote (1-" + candidates.length + "): ");
            int choice = sc.nextInt();

            if (choice >= 1 && choice <= candidates.length) {
                votes[choice - 1]++;
            } else {
                System.out.println("Invalid choice! Vote not counted.");
            }
        }

        Display results
        System.out.println("\n===== Voting Results =====");
        int maxVotes = -1;
        String winner = "";

        for (int i = 0; i < candidates.length; i++) {
            System.out.println(candidates[i] + " got " + votes[i] + " votes.");
            if (votes[i] > maxVotes) {
                maxVotes = votes[i];
                winner = candidates[i];
            }
        }

        Check for tie
        int winnersCount = 0;
        for (int v : votes) {
            if (v == maxVotes) winnersCount++;
        }
 if (winnersCount > 1) {
            System.out.println("\nResult: It's a tie!");
        } else {
            System.out.println("\nWinner: " + winner + " with " + maxVotes + " votes!");
        }

        sc.close();
    }
}
