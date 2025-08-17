# Bank-Account
import java.util.Scanner;

class BankAccount {
private String accountHolder;
private String accountNumber;
private double balance;

public BankAccount(String accountHolder, String accountNumber, double initialBalance) {
    this.accountHolder = accountHolder;
    this.accountNumber = accountNumber;
    this.balance = initialBalance;
}

public void deposit(double amount) {
    if (amount > 0) {
        balance += amount;
        System.out.println("Deposited: $" + amount);
    } else {
        System.out.println("Deposit amount must be positive.");
    }
}

public void withdraw(double amount) {
    if (amount > balance) {
        System.out.println("Insufficient balance.");
    } else if (amount <= 0) {
        System.out.println("Withdraw amount must be positive.");
    } else {
        balance -= amount;
        System.out.println("Withdrew: $" + amount);
    }
}

public void checkBalance() {
    System.out.println("Current balance: $" + balance);
}

public void displayAccountInfo() {
    System.out.println("Account Holder: " + accountHolder);
    System.out.println("Account Number: " + accountNumber);
    System.out.println("Balance: $" + balance);
}
}

public class BankAccountApp {
public static void main(String[] args) {
BankAccount myAccount = new BankAccount("Sara Ahmed", "123456789", 1000.0);
Scanner scanner = new Scanner(System.in);
int choice;

    System.out.println("🏦 Welcome to the Bank Account System!");

    do {
        System.out.println("\nMenu:");
        System.out.println("1. Display account info");
        System.out.println("2. Check balance");
        System.out.println("3. Deposit");
        System.out.println("4. Withdraw");
        System.out.println("5. Exit");

        System.out.print("Enter your choice (1-5): ");
        while (!scanner.hasNextInt()) {
            System.out.println("Invalid input. Please enter a number between 1 and 5.");
            scanner.next();
        }

        choice = scanner.nextInt();

        switch (choice) {
            case 1:
                myAccount.displayAccountInfo();
                break;
            case 2:
                myAccount.checkBalance();
                break;
            case 3:
                System.out.print("Enter amount to deposit: ");
                double depositAmount = scanner.nextDouble();
                myAccount.deposit(depositAmount);
                break;
            case 4:
                System.out.print("Enter amount to withdraw: ");
                double withdrawAmount = scanner.nextDouble();
                myAccount.withdraw(withdrawAmount);
                break;
            case 5:
                System.out.println("Thank you for using the system. Goodbye!");
                break;
            default:
                System.out.println("Invalid choice. Please choose a number from 1 to 5.");
        }

    } while (choice != 5);

    scanner.close();
}
}

