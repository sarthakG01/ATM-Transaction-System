# ATM-Transaction-System

import java.util.Scanner;

public class ATM {
    
    // Predefined user details
    static String userID = "sarthak3456";  // Example user ID
    static String userPIN = "4321";  // Example PIN
    static double balance = 1000.00;  // Initial balance
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Ask for User ID and PIN
        System.out.println("Enter User ID: ");
        String enteredID = scanner.nextLine();
        
        System.out.println("Enter PIN: ");
        String enteredPIN = scanner.nextLine();
        
        // Validate User ID and PIN
        if (validateUser(enteredID, enteredPIN)) {
            System.out.println("Login Successful!");
            
            // Show ATM menu
            int choice;
            do {
                System.out.println("\nATM Menu:");
                System.out.println("1. Check Balance");
                System.out.println("2. Deposit Money");
                System.out.println("3. Withdraw Money");
                System.out.println("4. Quit");
                
                System.out.print("Choose an option by choosing number: ");
                choice = scanner.nextInt();
                
                switch (choice) {
                    case 1:
                        checkBalance();
                        break;
                    case 2:
                        depositMoney();
                        break;
                    case 3:
                        withdrawMoney();
                        break;
                    case 4:
                        System.out.println("Thank you for using the ATM. Goodbye!");
                        break;
                    default:
                        System.out.println("Invalid option, please try again.");
                }
            } while (choice != 4);  // Repeat until user chooses to quit
            
        } else {
            System.out.println("Invalid User ID or PIN.");
        }
        
        scanner.close();
    }
    
    // Validate user credentials
    public static boolean validateUser(String enteredID, String enteredPIN) {
        return userID.equals(enteredID) && userPIN.equals(enteredPIN);
    }
    
    // Check balance
    public static void checkBalance() {
        System.out.println("\nYour current balance is: Rs" + balance);
    }
    
    // Deposit money
    public static void depositMoney() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("\nEnter amount to deposit: ");
        double amount = scanner.nextDouble();
        
        if (amount <= 0) {
            System.out.println("Please enter a valid amount.");
        } else {
            balance += amount;
            System.out.println("Successfully deposited Rs" + amount + ". Your updated balance is: Rs" + balance);
        }
    }
    
    // Withdraw money
    public static void withdrawMoney() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("\nEnter amount to withdraw: ");
        double amount = scanner.nextDouble();
        
        if (amount <= 0) {
            System.out.println("Please enter a valid amount.");
        } else if (amount > balance) {
            System.out.println("Insufficient balance. Try a smaller amount.");
        } else {
            balance -= amount;
            System.out.println("Successfully withdrawn Rs" + amount + ". Your updated balance is: Rs" + balance);
        }
    }
}

