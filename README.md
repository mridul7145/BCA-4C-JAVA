# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-
import java.util.Scanner;

public class EMPLOYEE {
    private String NameOfEmp;
    private int EmpId;
    private double BasicSalary;
    private double GrossSalary;

    // Constructor
    public EMPLOYEE(String nameOfEmp, int empId, double basicSalary) {
        NameOfEmp = nameOfEmp;
        EmpId = empId;
        BasicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate GrossSalary
    private void calculateGrossSalary() {
        double HRA = 0.25 * BasicSalary;
        double DA = 0.40 * BasicSalary;
        GrossSalary = BasicSalary + HRA + DA;
    }

    // Method to display NameOfEmp and GrossSalary of employees whose name starts with a consonant
    public void displayConsonantEmployees() {
        if (!isVowel(NameOfEmp.charAt(0))) {
            System.out.println("NameOfEmp: " + NameOfEmp + ", GrossSalary: " + GrossSalary);
        }
    }

    // Method to display EmpId and GrossSalary of Employees whose EmpId is between 101 and 150
    public void displayEmployeesInRange() {
        if (EmpId >= 101 && EmpId <= 150) {
            System.out.println("EmpId: " + EmpId + ", GrossSalary: " + GrossSalary);
        }
    }

    // Method to check if a character is a vowel
    private boolean isVowel(char ch) {
        ch = Character.toUpperCase(ch);
        return ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U';
    }

    // Getter method for GrossSalary
    public double getGrossSalary() {
        return GrossSalary;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        EMPLOYEE[] employees = new EMPLOYEE[3]; // Change the array size as needed

        // Input data for employees
        for (int i = 0; i < employees.length; i++) {
            System.out.println("Enter details for employee " + (i + 1) + ":");
            System.out.print("NameOfEmp: ");
            String name = scanner.nextLine();
            System.out.print("EmpId: ");
            int id = scanner.nextInt();
            System.out.print("BasicSalary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume the newline character
            employees[i] = new EMPLOYEE(name, id, basicSalary);
        }

        // Query a) Display the NameOfEmp and GrossSalary of employees whose name starts with a consonant
        System.out.println("Employees whose name starts with a consonant:");
        for (EMPLOYEE employee : employees) {
            employee.displayConsonantEmployees();
        }

        // Query b) Display the EmpId and GrossSalary of Employees whose EmpId is between 101 and 150
        System.out.println("\nEmployees whose EmpId is between 101 and 150:");
        for (EMPLOYEE employee : employees) {
            employee.displayEmployeesInRange();
        }

        // Query c) Count the total number of Employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (EMPLOYEE employee : employees) {
            if (employee.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of Employees whose GrossSalary is less than 35000/-: " + count);
    }
}
