# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-


// Name = Sujal 
// Roll No. =2210997245


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
    }

    public void calculateSalary() {
        double hra = 0.25 * basicSalary;
        double da = 0.4 * basicSalary;
        grossSalary = basicSalary + hra + da;
    }

    public void display() {
        System.out.println("Employee Name: " + nameOfEmp);
        System.out.println("Gross Salary: " + grossSalary);
    }

    public String getNameOfEmp() {
        return nameOfEmp;
    }

    public double getGrossSalary() {
        return grossSalary;
    }

    public int getEmpId() {
        return empId;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of employees: ");
        int numOfEmployees = scanner.nextInt();

        Employee[] employees = new Employee[numOfEmployees];

        for (int i = 0; i < numOfEmployees; i++) {
            System.out.println("Enter details for Employee " + (i + 1) + ":");
            employees[i] = new Employee();
            employees[i].input();
            employees[i].calculateSalary();
        }

        // Query a) Display the NameOfEmp and GrossSalary of employees whose name starts with a consonant.
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee employee : employees) {
            String name = employee.getNameOfEmp();
            if (name.matches("[bcdfghjklmnpqrstvwxyzBCDFGHJKLMNPQRSTVWXYZ].*")) {
                employee.display();
            }
        }

        // Query b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
        System.out.println("\nEmployees with Emp-Id between 101 and 150:");
        for (Employee employee : employees) {
            int empId = employee.getEmpId();
            if (empId >= 101 && empId <= 150) {
                employee.display();
            }
        }

        // Query c) Count the total number of Employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (Employee employee : employees) {
            double grossSalary = employee.getGrossSalary();
            if (grossSalary < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of employees with GrossSalary less than 35000: " + count);
    }
}

