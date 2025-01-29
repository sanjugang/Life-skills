# SOLID Principles
The SOLID principles are a set of design principles for writing clean, maintainable, and scalable object-oriented code. 
    They are an acronym for five key principles introduced by Robert C. Martin (Uncle Bob).
![](https://media.geeksforgeeks.org/wp-content/uploads/20241011163144806245/SOLID-Principles-in-Programming.webp)
  ## 1.Single Responsibility Principle (SRP) 
  A class should have one and only one reason to change, meaning that a class should have only one job.
#### Keyoints:
+ Each class should focus on a specific functionality.
- Helps avoid tightly coupled code.

      class Employee {
          void getDetails() { /* Employee details */ }
      }

      class SalaryCalculator {
          void calculateSalary() { /* Salary logic */ }
      }

[Know more about SRP](https://www.techtarget.com/whatis/definition/Single-Responsibility-Principle-SRP)


## 2.Open/Closed Principle (OCP)
 Objects or entities should be open for extension but closed for modification.
#### Key Points:

+ Extend the behavior of a class without modifying its existing code.
+ Achieved using abstractions (e.g., interfaces, inheritance).
    
      abstract class SalaryCalculator {
          abstract double calculateSalary();
      }

      class FullTimeSalary extends SalaryCalculator {
          double calculateSalary() { return 50000; }
      }

      class PartTimeSalary extends SalaryCalculator {
          double calculateSalary() { return 20000; }
      }

[Know more about OCP](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)

## 3.Liskov Substitution Principle (LSP)
Derived classes must be substitutable for their base classes.
#### Keyoints
+ Subtypes must maintain the behavior of their parent type.
+ Avoid overriding methods that alter the intended behavior.


      class Bird { }
      class FlyingBird extends Bird { 
          void fly() { System.out.println("Flying"); 
          }
      }
      class Penguin extends Bird { 
          void swim() { System.out.println("Swimming"); 
          }
      }
  
[Know more about OCP](https://www.linkedin.com/pulse/liskov-substitution-principle-lsp-frontend-prithveesh-goel)

## 4. Interface Segregation Principle (ISP)
Clients should not be forced to depend on interfaces they do not use.
#### Key Points:
+ Split large interfaces into smaller, specific ones.
+ Avoid "fat" interfaces that include unrelated methods.


      interface Workable { 
          void work(); 
      }
      interface Eatable { 
          void eat();
      }

      class Robot implements Workable {
          public void work() { 
             System.out.println("Robot working"); 
          }
      }

      class Human implements Workable, Eatable {
          public void work() { 
              System.out.println("Human working"); 
              }
          public void eat() { 
            System.out.println("Human eating");
             }
      }


[Know more about ISP](https://en.wikipedia.org/wiki/Interface_segregation_principle)

## 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions.

Key Points:

+ Depend on abstractions (e.g., interfaces) rather than concrete implementations.
+ Makes code more flexible and testable.



      interface Database {
          void saveData(String data);
      }

      class MySQLDatabase implements Database {
      public void saveData(String data) { System.out.println("Saving to MySQL"); }
      }

      class EmployeeService {
          private Database db;
          EmployeeService(Database db) { this.db = db; } // ✅ Dependency Injection
          void saveEmployee() { db.saveData("John"); }
      }

      // Usage
      public class Main {
      public static void main(String[] args) {
        Database db = new MySQLDatabase();
        EmployeeService service = new EmployeeService(db);
        service.saveEmployee();
           }
        }

[Know more about DIP](https://www.geeksforgeeks.org/dependecy-inversion-principle-solid/)
