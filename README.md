import java.util.ArrayList;
import java.util.Scanner;

class BankingSystem {
    private String accountHolder;
    private double balance;
    private ArrayList<String> transactions;

    // Constructor to initialize the account
    public class  BankAccount(String accountHolder) {
        this.accountHolder = accountHolder;
        this.balance = 0.0;
        this.transactions = new ArrayList<>();
    }

    // Method to deposit money
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            transactions.add("Deposited: $" + amount);
            System.out.println("Deposited $" + amount + ". New balance: $" + balance);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    // Method to withdraw money
    public void withdraw(double amount) {
        if (amount <= balance) {
            if (amount > 0) {
                balance -= amount;
                transactions.add("Withdrew: $" + amount);
                System.out.println("Withdrew $" + amount + ". New balance: $" + balance);
            } else {
                System.out.println("Withdrawal amount must be positive.");
            }
        } else {
            System.out.println("Insufficient balance.");
        }
    }

    // Method to check balance
    public void checkBalance() {
        System.out.println("Account balance: $" + balance);
    }

    // Method to show transaction history
    public void transactionHistory() {
        System.out.println("Transaction History:");
        for (String transaction : transactions) {
            System.out.println(transaction);
        }
    }
}

public class SimpleBankingSystem {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Welcome to the Simple Bank System");
        System.out.print("Enter account holder name: ");
        String name = scanner.nextLine();

        BankAccount account = new BankAccount(name);
        System.out.println("Account created for " + name + ".\n");

        while (true) {
            // Display menu options
            System.out.println("\n1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Transaction History");
            System.out.println("5. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter amount to deposit: $");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;

                case 2:
                    System.out.print("Enter amount to withdraw: $");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;

                case 3:
                    account.checkBalance();
                    break;

                case 4:
                    account.transactionHistory();
                    break;

                case 5:
                    System.out.println("Thank you for using the Simple Bank System!");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid option. Please choose a valid action.");
            }
        }
    }
}
