# Guvi-project
To run the Java ATM project step by step, here’s a beginner-friendly guide you can follow whether you're using a simple text editor, an IDE like Eclipse/IntelliJ, or an online compiler.

STEP-BY-STEP GUIDE TO RUN THE ATM PROJECT
Step 1: Prepare Your Environment
Choose where you want to write and run the code:

Option A: Install JDK and use a text editor (like Notepad++ or VS Code) + terminal

Option B: Use an IDE (like Eclipse or IntelliJ IDEA)

Option C: Use an online compiler (e.g., https://www.jdoodle.com or https://www.onlinegdb.com/)

Step 2: Create the Java File
Open your editor or IDE.

Create a new file and name it exactly: SimpleATM.java
(Java class and filename must match.)

Step 3: Copy the Full Code
Paste this complete code into your file:

java
Copy code
import java.util.Scanner;

interface ATMOperations {
    void checkBalance();
    void deposit(double amount);
    void withdraw(double amount);
}

public class SimpleATM implements ATMOperations {
    private double balance;
    private static final String PIN = "1234";

    public SimpleATM(double initialBalance) {
        this.balance = initialBalance;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        SimpleATM atm = new SimpleATM(1000.0);  // Initial balance set to $1000

        System.out.println("Welcome to the ATM!");
        System.out.print("Enter your 4-digit PIN: ");
        String enteredPin = scanner.nextLine();

        if (enteredPin.equals(PIN)) {
            int choice;
            do {
                System.out.println("\n--- ATM MENU ---");
                System.out.println("1. Check Balance");
                System.out.println("2. Deposit Money");
                System.out.println("3. Withdraw Money");
                System.out.println("4. Exit");
                System.out.print("Enter your choice: ");
                choice = scanner.nextInt();

                switch (choice) {
                    case 1:
                        atm.checkBalance();
                        break;
                    case 2:
                        System.out.print("Enter amount to deposit: $");
                        double depositAmount = scanner.nextDouble();
                        atm.deposit(depositAmount);
                        break;
                    case 3:
                        System.out.print("Enter amount to withdraw: $");
                        double withdrawAmount = scanner.nextDouble();
                        atm.withdraw(withdrawAmount);
                        break;
                    case 4:
                        System.out.println("Thank you for using the ATM. Goodbye!");
                        break;
                    default:
                        System.out.println("Invalid choice.");
                }
            } while (choice != 4);
        } else {
            System.out.println("Incorrect PIN. Access denied.");
        }

        scanner.close();
    }

    @Override
    public void checkBalance() {
        System.out.printf("Current balance: $%.2f\n", balance);
    }

    @Override
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.printf("$%.2f deposited successfully.\n", amount);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    @Override
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.printf("$%.2f withdrawn successfully.\n", amount);
        } else {
            System.out.println("Invalid or insufficient funds.");
        }
    }
}
Step 4: Compile the Code
If using Command Line (Windows/macOS/Linux):
Open terminal or command prompt.

Navigate to the folder where SimpleATM.java is saved.

Compile the file:

bash
Copy code
javac SimpleATM.java
This will create a SimpleATM.class file.

Step 5: Run the Program
bash
Copy code
java SimpleATM
You will see:

css
Copy code
Welcome to the ATM!
Enter your 4-digit PIN:
Now you can interact with the ATM in the terminal.

Step 6: Use the ATM Features
Enter 1234 when prompted for the PIN (this is the correct one).

Choose from the menu:

1 to check balance

2 to deposit

3 to withdraw

4 to exit

Try out different inputs to test the logic.

Need to Submit This for a Project?
Include:

SimpleATM.java file

A screenshot of the terminal running the program

A short PDF or .txt file explaining the features

Let me know if you want help turning this into a GUI version or packaging it into a .jar file for easy sharing.






You said:
Does the contains interface too


ChatGPT said:
Yes, the code I gave you above does contain an interface.

Here's the interface part clearly:
java
Copy code
// This is the interface declaration
interface ATMOperations {
    void checkBalance();
    void deposit(double amount);
    void withdraw(double amount);
}
What does this mean?
This is a Java interface named ATMOperations.

It defines three method signatures:

checkBalance()

deposit(double amount)

withdraw(double amount)

It doesn't contain any implementation—just the method names.

Then, in the same file, this class implements the interface:
java
Copy code
public class SimpleATM implements ATMOperations {
    // Class body with all method implementations
}
SimpleATM implements the ATMOperations interface.

It provides actual code for all three methods.

Why is this important?
Using an interface:

Makes your code more modular and maintainable.

Allows you to define a "contract" for any ATM class.

You could easily create another ATM class (like SecureATM, OnlineATM, etc.) that also implements ATMOperations.

So yes — the project includes an interface, and it's properly implemented. You can confidently submit it as an interface-based Java program.

Let me know if you’d like a UML diagram or class diagram to go with it!
