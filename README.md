# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-



// Name = Sujal 
// Roll no. = 2210997245


import java.util.Scanner;

class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    public void input() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter Name of Employee: ");
        nameOfEmp = scanner.nextLine();
        System.out.print("Enter Employee ID: ");
        empId = scanner.nextInt();
        System.out.print("Enter Basic Salary: ");
        basicSalary = scanner.nextDouble();
        scanner.close();
    }

    public void calculateSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.4 * basicSalary;
        grossSalary = basicSalary + hra + da;
    }

    public void display() {
        System.out.println("Name of Employee: " + nameOfEmp);
        System.out.println("Gross Salary: " + grossSalary);
    }

    public boolean startsWithConsonant() {
        char firstChar = nameOfEmp.toLowerCase().charAt(0);
        return !(firstChar == 'a' || firstChar == 'e' || firstChar == 'i' || firstChar == 'o' || firstChar == 'u');
    }

    public boolean isBetween101And150() {
        return empId >= 101 && empId <= 150;
    }

    public boolean isSalaryLessThan35000() {
        return grossSalary < 35000;
    }
}

public class Main {
    public static void main(String[] args) {
        int n = 3; // Number of employees
        Employee[] employees = new Employee[n];

        for (int i = 0; i < n; i++) {
            employees[i] = new Employee();
            employees[i].input();
            employees[i].calculateSalary();
        }

        System.out.println("Employees whose name starts with a consonant:");
        for (int i = 0; i < n; i++) {
            if (employees[i].startsWithConsonant()) {
                employees[i].display();
            }
        }

        System.out.println("Employees whose Emp-Id is between 101 and 150:");
        for (int i = 0; i < n; i++) {
            if (employees[i].isBetween101And150()) {
                employees[i].display();
            }
        }

        int count = 0;
        for (int i = 0; i < n; i++) {
            if (employees[i].isSalaryLessThan35000()) {
                count++;
            }
        }
        System.out.println("Total number of Employees whose GrossSalary is less than 35000/-: " + count);
    }
}
