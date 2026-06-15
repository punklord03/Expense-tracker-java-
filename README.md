# Expense-tracker-java-
It's just my first project .it's just Java console application for tracking and managing personal expenses using OOP concepts.




import java.util.ArrayList;
import java.util.Scanner;

class Expense {
    private String name;
    private double amount;

    public Expense(String name, double amount) {
        this.name = name;
        this.amount = amount;
    }

    public String getName() {
        return name;
    }

    public double getAmount() {
        return amount;
    }
}

public class ExpenseTracker {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Expense> expenses = new ArrayList<>();

        while (true) {
            System.out.println("\n===== Expense Tracker =====");
            System.out.println("1. Add Expense");
            System.out.println("2. View Expenses");
            System.out.println("3. Show Total");
            System.out.println("4. Delete Expense");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");

            int choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Expense Name: ");
                    String name = sc.nextLine();

                    System.out.print("Amount: ");
                    double amount = sc.nextDouble();

                    expenses.add(new Expense(name, amount));
                    System.out.println("Expense added successfully!");
                    break;

                case 2:
                    if (expenses.isEmpty()) {
                        System.out.println("No expenses found.");
                    } else {
                        System.out.println("\nExpenses:");
                        for (int i = 0; i < expenses.size(); i++) {
                            Expense e = expenses.get(i);
                            System.out.println((i + 1) + ". "
                                    + e.getName() + " - ₹" + e.getAmount());
                        }
                    }
                    break;

                case 3:
                    double total = 0;
                    for (Expense e : expenses) {
                        total += e.getAmount();
                    }
                    System.out.println("Total Spending: ₹" + total);
                    break;

                case 4:
                    if (expenses.isEmpty()) {
                        System.out.println("No expenses to delete.");
                    } else {
                        System.out.print("Enter expense number to delete: ");
                        int index = sc.nextInt();

                        if (index >= 1 && index <= expenses.size()) {
                            expenses.remove(index - 1);
                            System.out.println("Expense deleted.");
                        } else {
                            System.out.println("Invalid number.");
                        }
                    }
                    break;

                case 5:
                    System.out.println("Thank you for using Expense Tracker!");
                    sc.close();
                    return;

                default:
                    System.out.println("Invalid choice.");
            }
        }
    }
}
