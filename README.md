# Java Fundamentals for Spring Boot

## Introduction
This documentation aims to provide an overview of fundamental Java concepts necessary for working with Spring Boot.

## Table of Contents
- [What is JDK, JRE and JVM in Java](#What-is-JDK-JRE-and-JVM-in-Java)
- [How to Execute a Java Program](#How-to-execute-a-Java-Program)
- [Java Basics](#Java-Basics)
- [Java OOP (Object-Oriented Programming)](#Java-OOP (Object-Oriented Programming))
- [Interfaces](#interfaces)
- [Exception Handling](#exception-handling)

## What is JDK, JRE and JVM in Java
 ### 1. JDK (Java Development Kit)
   - The `JDK (Java Development Kit)` is a superset of the JRE and contains everything that is in the JRE, plus tools such as the compiler, debugger, JavaDoc, keytool etc necessary for developing and running Java programs or applications.
     
     
     ![Java JDK JRE and JVM](https://github.com/douaeelh2/Java-Documentation/assets/127549220/ab43eb26-79a7-4936-8ace-10da5a248a51)

 ### 2. JVM (Java Virtual Machine)
   - The `JVM (Java Virtual Machine)` is a very important component of Java programming language. When you run the Java program, the Java compiler first compiles your Java code to bytecode. Then, the JVM translates bytecode into native machine code (set of instructions that a computer's CPU executes directly).
   - `JVM` is called virtual because it provides an interface that does not depend on the underlying operating system and machine hardware.
  
     ![JVM](https://github.com/douaeelh2/Java-Documentation/assets/127549220/2b0cfefd-eae7-405d-8d67-be6492089df4)
     

 ### 3. JRE (Java Runtime Environment)
   - The `Java Runtime Environment (JRE)`provides the libraries, the Java Virtual Machine, and other components to run applets and applications written in the Java programming language.
JRE doesn’t contain any development tools such as Java compiler, debugger, JShell, etc.
   - If you just want to execute a java program, you can install only JRE. You don’t need JDK because there is no development or compilation of java source code is required.

   ![JRE](https://github.com/douaeelh2/Java-Documentation/assets/127549220/30dc98dd-e601-47c5-b516-1fa1cc03797e)
   

## How to Execute a Java Program
 ### 1. Writing the Source Code 
   - Begin by writing your Java program using a text editor or an Integrated Development Environment (IDE) such as Eclipse, Netbeans, or IntelliJ IDEA. Save the Java source code in files with the .java extension.

 ### 2. Compilation:
   - Compile your Java source code into bytecode using a Java compiler included in the `Java Development Kit (JDK)`. You can compile your code using the `javac` command-line tool or built-in features of an IDE. Compilation converts your Java source code into `.class` files containing Java bytecode.

### 3. Runtime Environment (JRE)
   - To execute the Java bytecode, install the `Java Runtime Environment (JRE)`, which includes the `Java Virtual Machine (JVM)` and standard Java class libraries. The JRE provides an environment for executing Java bytecode.

### 4. Running the Program
   - Once the JRE is installed, run your Java program using the `java` command followed by the name of the class containing the `main()` method in your terminal or command prompt.


## Java OOP (Object-Oriented Programming)
 ### 1. Encapsulation 
   - `Encapsulation` is the mechanism of bundling the data (attributes) and the methods (functions) that operate on the data into a single unit called a class.
   -  It allows data to be hidden from the outside world and accessed only through the methods defined in the class.
     
     
   ```java
   public class Car {
    private String model;
    private int year;
    
    // Constructor
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
    }
    
    // Getter methods
    public String getModel() {
        return model;
    }
    
    public int getYear() {
        return year;
    }
    
    // Setter methods
    public void setModel(String model) {
        this.model = model;
    }
    
    public void setYear(int year) {
        this.year = year;
    }
   }
   ```
   
 ### 2. Inheritance
   - `Inheritance` is a mechanism in which a new class inherits properties and behavior (methods) from an existing class.
   - Promoting code reuse, class hierarchy, and object specialization.

   ```java
    // Parent class
class Vehicle {
    String brand;

    void drive() {
        System.out.println("Driving a vehicle...");
    }
}
 ```

 ```java

// Child class inheriting from Vehicle
class Car extends Vehicle {
    int numberOfSeats;

    void accelerate() {
        System.out.println("Car is accelerating...");
    }
}
 ```

 ```java

// Main class
public class Main {
    public static void main(String[] args) {
        // Creating an instance of Car
        Car myCar = new Car();
        myCar.brand = "Toyota";
        myCar.numberOfSeats = 5;

        // Accessing methods from both Vehicle and Car
        myCar.drive(); // Inherited from Vehicle class
        myCar.accelerate(); // Specific to Car class
    }
}

```
 ### 3. Abstraction
   - `Abstraction` is the process of hiding the implementation details and showing only the essential features of an object. It helps in reducing programming complexity and focusing on relevant aspects
   - `Abstract class` cannot be instantiated on their own and may contain abstract methods (methods without implementation)
     
```java
  // Abstract class
abstract class Shape {
    abstract void draw(); // Abstract method
}
```

```java
// Concrete class implementing Shape
class Circle extends Shape {
    void draw() {
        System.out.println("Drawing a circle");
    }
}
```
### 4. Polymorphism
  - `Polymorphism` is the ability of an object to take on different forms or behaviors depending on the context in which it is used. There are two types of polymorphism in Java: compile-time (method overloading) and runtime (method overriding).
    
### 5. Overloading and Overriding
  - `Overloading` occurs when a class has multiple methods with the same name but different signature. 
    
  ```java
    class MathOperations {
    // Method overloading
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
     }
    }
 ```
  - `Overriding` happens when a subclass provides a specific implementation of a method that is already defined in its superclass with the same signature.
    
  ```java
    class Animal {
        void makeSound() {
            System.out.println("Animal makes a sound");
        }
    }
    
    class Dog extends Animal {
        void makeSound() {
            System.out.println("Dog barks");
        }
    }
  ```
 ### 6. Aggregation and Composition
  - `Aggregation` represents a "has-a" relationship.
  - It occurs when an object contains another object, but the contained object can exist independently of the container object.

   ```java
       class Department {
       private String name;
       // Other attributes and methods
       
       // Aggregation: Department has-a Professor
       private Professor[] professors; // Array of professors
   
       public Department(String name) {
           this.name = name;
           professors = new Professor[10]; // Example: department can have up to 10 professors
       }
       
       // Other methods to manage professors
   }
   
   class Professor {
       private String name;
       // Other attributes and methods
       
       public Professor(String name) {
           this.name = name;
       }
   }

  ```
In this example, a `Department` has multiple `Professor` objects. However, the `Professor` objects can exist independently of the`Department`. If the `Department` object is destroyed, the `Professor` objects still exist.

  - `Composition` represents a stronger form of aggregation and implies a "part-of" relationship.
  - In composition, the lifetime of the contained object is dependent on the lifetime of the container object.
    
       ```java
        class Car {
         // Composition: Car has-a Engine
         private Engine engine;
     
         public Car() {
             this.engine = new Engine(); // Engine is created along with the Car
         }
         
           // Other attributes and methods
       }
       
       class Engine {
           // Attributes and methods of Engine
       }

     ```
 In this example, a `Car` is composed of an `Engine`. The Engine object is created along with the `Car` object and cannot exist independently. If the `Car` object is destroyed, the `Engine` object is also destroyed.







