[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/pAwhWXY5)

1.Write a program to sort a list of Employee objects (name, age, salary) using lambda expressions. 
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

class Employee {
    String name;
    int age;
    double salary;

    public Employee(String name, int age, double salary) {
        this.name = name;
        this.age = age;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "Employee{name='" + name + "', age=" + age + ", salary=" + salary + "}";
    }
}

public class EmployeeSorter {
    public static void main(String[] args) {
        List<Employee> employees = new ArrayList<>();
        employees.add(new Employee("Alice", 30, 50000));
        employees.add(new Employee("Bob", 25, 60000));
        employees.add(new Employee("Charlie", 35, 55000));

        // Sorting by salary using lambda expression
        employees.sort(Comparator.comparingDouble(emp -> emp.salary));
        System.out.println("Employees sorted by salary: ");
        employees.forEach(System.out::println);
    }
}

2.Create a program to use lambda expressions and stream operations to filter students scoring above 75%, sort them by marks, and display their names.
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;

class Student {
    String name;
    double marks;

    public Student(String name, double marks) {
        this.name = name;
        this.marks = marks;
    }

    @Override
    public String toString() {
        return "Student{name='" + name + "', marks=" + marks + "}";
    }
}

public class StudentFilter {
    public static void main(String[] args) {
        List<Student> students = new ArrayList<>();
        students.add(new Student("John", 80));
        students.add(new Student("Jane", 65));
        students.add(new Student("Alice", 90));
        students.add(new Student("Bob", 70));

        // Filtering and sorting students scoring above 75%
        List<String> filteredStudents = students.stream()
                .filter(student -> student.marks > 75)
                .sorted((s1, s2) -> Double.compare(s2.marks, s1.marks))
                .map(student -> student.name)
                .collect(Collectors.toList());

        System.out.println("Students scoring above 75%, sorted by marks:");
        filteredStudents.forEach(System.out::println);
    }
}

