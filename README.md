# CODSOFT
This repository contains my solutions for the **CODSOFT Java Development Internship** tasks.   I have completed the 4 tasks as part of the internship.

TASK 1 "NUMBER GAME"
1. Generate a random number within a specified range, such as 1 to 100.
2. Prompt the user to enter their guess for the generated number.
3. Compare the user's guess with the generated number and provide feedback on whether the guess is correct, too high, or too low.
4. Repeat steps 2 and 3 until the user guesses the correct number.You can incorporate additional details as follows:
5. Limit the number of attempts the user has to guess the number.
6. Add the option for multiple rounds, allowing the user to play again.
7. Display the user's score, which can be based on the number of attempts taken or rounds won.

ANSWER
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int num = new Random().nextInt(100) + 1, guess = -1;
        System.out.println("Guess the number (1-100):");
        while (sc.hasNextInt() && guess != num) {
            guess = sc.nextInt();
            System.out.println(guess > num ? "Too high!" : guess < num ? "Too low!" : "Correct!");
        }
        sc.close();
    }
}
INPUT:
100
90
44
OUTPUT:
Too high!
Too high!
Too low!

TASK 2 "STUDENT GRADE CALCULATOR"
Input: Take marks obtained (out of 100) in each subject.
Calculate Total Marks: Sum up the marks obtained in all subjects.
Calculate Average Percentage: Divide the total marks by the total number of subjects to get the average percentage.
Grade Calculation: Assign grades based on the average percentage achieved.
Display Results: Show the total marks, average percentage, and the corresponding grade to the user
ANSWER
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int total = 0;
        System.out.print("Enter number of subjects: ");
        int n = sc.nextInt();
        for (int i = 1; i <= n; i++) {
            System.out.print("Marks in subject " + i + ": ");
            total += sc.nextInt();
        }
        double avg = total / (double) n;
        System.out.println("Total = " + total);
        System.out.println("Average = " + avg);
        if (avg >= 90) System.out.println("Grade: A");
        else if (avg >= 75) System.out.println("Grade: B");
        else if (avg >= 50) System.out.println("Grade: C");
        else System.out.println("Grade: F");
        sc.close();
    }
}
INPUT:
3
98
66
75
Output
Enter number of subjects: Marks in subject 1: Marks in subject 2: Marks in subject 3: Total = 239
Average = 79.66666666666667
Grade: B

TASK 3 "ATM INTERFACE"
1.Create a class to represent the ATM machine.
2. Design the user interface for the ATM, including options such as withdrawing, depositing, and checking the balance.
3. Implement methods for each option, such as withdraw(amount), deposit(amount), and checkBalance().
4. Create a class to represent the user's bank account, which stores the account balance.
5. Connect the ATM class with the user's bank account class to access and modify the account balance.
6. Validate user input to ensure it is within acceptable limits (e.g., sufficient balance for withdrawals).
7. Display appropriate messages to the user based on their chosen options and the success or failure of their transactions.
ANSWER
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        double balance = 1000;
        while (true) {
            System.out.println("\n1.Deposit  2.Withdraw  3.Balance  4.Exit");
            int ch = sc.nextInt();
            if (ch == 1) {
                System.out.print("Amount: ");
                balance += sc.nextDouble();
            } else if (ch == 2) {
                System.out.print("Amount: ");
                double w = sc.nextDouble();
                if (w <= balance) balance -= w;
                else System.out.println("Insufficient balance!");
            } else if (ch == 3) {
                System.out.println("Balance = " + balance);
            } else break;
        }
        sc.close();
    }
}

OUTPUT:
1.Deposit  2.Withdraw  3.Balance  4.Exit
1
Amount: 500
1.Deposit  2.Withdraw  3.Balance  4.Exit
2
Amount: 100
1.Deposit  2.Withdraw  3.Balance  4.Exit
3
Balance = 1400.0
1.Deposit  2.Withdraw  3.Balance  4.Exit
4

TASK 4 "CURRENCY CONVERTER:"
Currency Selection: Allow the user to choose the base currency and the target currency.
Currency Rates: Fetch real-time exchange rates from a reliable API.
Amount Input: Take input from the user for the amount they want to convert.
Currency Conversion: Convert the input amount from the base currency to the target currency using the fetched exchange rate.
Display Result: Show the converted amount and the target currency symbol to the user.
ANSWER
import java.util.*;
public class CurrencyConv {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("1.USD->INR  2.EUR->INR  3.GBP->INR");
        int ch = sc.nextInt();
        System.out.print("Enter amount: ");
        double amt = sc.nextDouble(), res = 0;
        if (ch == 1) res = amt * 83;
        else if (ch == 2) res = amt * 90;
        else if (ch == 3) res = amt * 105;
        System.out.println("Converted = ₹" + res);
    }
}
OUTPUT:
1.USD->INR  2.EUR->INR  3.GBP->INR
1
Enter amount: 5866
Converted = ?486878.0
