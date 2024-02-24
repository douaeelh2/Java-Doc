# Java Fundamentals for Spring Boot

# Introduction
This documentation aims to provide an overview of fundamental Java 8 , 11 , 17 and 21 concepts necessary for working with Spring Boot.

# Table of Contents
- [What is JDK, JRE and JVM in Java](#what-is-jdk-jre-and-jvm-in-java)
- [How to Execute a Java Program](#how-to-execute-a-java-program)
- [Java 8 Basics](#java-8-basics)
  - [Lambda Expressions](#java-lambda-expressions)
  - [Functional Interfaces](#java-functional-interfaces)
  - [Method References](#java-method-references)
  - [Stream API](#java-stream-api)
  - [Optional Class](#java-optional-class)
  - [Collectors Class](#java-collectors-class)
  - [StringJoiner Class](#java-stringjoiner-class)
  - [Static and Default Methods in Interface](#java-static-and-default-methods-in-interface)
    
- [Java OOP (Object-Oriented Programming)](#java-oop-object-oriented-programming)
  - [Encapsulation](#encapsulation)
  - [Inheritance](#inheritance)
  - [Abstraction](#abstraction)
  - [Polymorphism](#polymorphism)
  - [Overloading & Overriding](#overloading-&-overriding)
  - [Aggregation & Composition](#aggregation-&-composition)
  - [Interface & Abstract Class](#interface-&-abstract-class)
  - [Static](#static)
  - [Final](#final)


# What is JDK, JRE and JVM in Java
 ## 1. JDK (Java Development Kit)
   - The `JDK (Java Development Kit)` is a superset of the JRE and contains everything that is in the JRE, plus tools such as the compiler, debugger, JavaDoc, keytool etc necessary for developing and running Java programs or applications.
     
     
     ![Java JDK JRE and JVM](https://github.com/douaeelh2/Java-Documentation/assets/127549220/ab43eb26-79a7-4936-8ace-10da5a248a51)

 ## 2. JVM (Java Virtual Machine)
   - The `JVM (Java Virtual Machine)` is a very important component of Java programming language. When you run the Java program, the Java compiler first compiles your Java code to bytecode. Then, the JVM translates bytecode into native machine code (set of instructions that a computer's CPU executes directly).
   - `JVM` is called virtual because it provides an interface that does not depend on the underlying operating system and machine hardware.
  
     ![JVM](https://github.com/douaeelh2/Java-Documentation/assets/127549220/2b0cfefd-eae7-405d-8d67-be6492089df4)
     

 ## 3. JRE (Java Runtime Environment)
   - The `Java Runtime Environment (JRE)` provides the libraries, the Java Virtual Machine, and other components to run applets and applications written in the Java programming language.
JRE doesn’t contain any development tools such as Java compiler, debugger, JShell, etc.
   - If you just want to execute a java program, you can install only JRE. You don’t need JDK because there is no development or compilation of java source code is required.

   ![JRE](https://github.com/douaeelh2/Java-Documentation/assets/127549220/30dc98dd-e601-47c5-b516-1fa1cc03797e)
   

# How to Execute a Java Program
 ### 1. Writing the Source Code 
   - Begin by writing your Java program using a text editor or an Integrated Development Environment (IDE) such as Eclipse, Netbeans, or IntelliJ IDEA. Save the Java source code in files with the .java extension.

 ## 2. Compilation:
   - Compile your Java source code into bytecode using a Java compiler included in the `Java Development Kit (JDK)`. You can compile your code using the `javac` command-line tool or built-in features of an IDE. Compilation converts your Java source code into `.class ` files containing Java bytecode.

## 3. Runtime Environment (JRE)
   - To execute the Java bytecode, install the `Java Runtime Environment (JRE)`, which includes the `Java Virtual Machine (JVM)` and standard Java class libraries. The JRE provides an environment for executing Java bytecode.

## 4. Running the Program
   - Once the JRE is installed, run your Java program using the `java` command followed by the name of the class containing the `main()` method in your terminal or command prompt.

# Java 8 Basics
 ## 1. Lambda Expressions
  **Zero Parameters :**
  
  ```java
  () -> System.out.println("No parameters!");
  ```

 **One Parameter :**
  
  ```java
  s -> System.out.println(s);
  ```

 **Multiple Parameters :**
  
  ```java
  (int x, int y) -> x + y;
  ```

 **Single Expression :**
  
  ```java
  a -> a * a // no need for the return keyword
  ```

  **Code Block :**
  
  ```java
 (a , b) -> { return a + b }; // Multiple statements inside braces
  ```
  
  ## 2. Functional Interfaces
  - A functional interface is an interface that contains only `one abstract method`. It can also contain `default` and `static` methods, but it must have exactly one abstract method.
  - The `@FunctionalInterface` notation is optional but recommended to clearly indicate to other developers that this interface is intended to be used as a functional interface. If you try to declare a second abstract method in an interface annotated with `@FunctionalInterface` , the compiler will generate an error.
    
    ```java
        @FunctionalInterface
        interface MyFunctionalInterface {
            void myAbstractMethod();
        
            // This line would generate an error because it introduces a second abstract method
            // void anotherAbstractMethod();
            
            // This is a default method
            default void myDefaultMethod() {
                System.out.println("This is a default method.");
            }
        
            // This is a static method
            static void myStaticMethod() {
                System.out.println("This is a static method.");
            }
        }
    ```

    ```java
       public class Main {
          public static void main(String[] args) {
              // Using a lambda expression to implement the abstract method of the functional interface
              MyFunctionalInterface myInstance = () -> System.out.println("Implementation of myAbstractMethod.");
              
              // Calling the abstract method
              myInstance.myAbstractMethod(); // Output: "Implementation of myAbstractMethod."
              
              // Calling the default method
              myInstance.myDefaultMethod(); // Output: "This is a default method."
              
              // Calling the static method
              MyFunctionalInterface.myStaticMethod(); // Output: "This is a static method."
          }
       }
    ```

  ### Functional Interface with Lambda Expression
  
   ```java
        public class Main {
          public static void main(String[] args) {
      
              // Lambda expression for multiplying two numbers
              BinaryOperator<Integer> multiplication = (a, b) -> a * b;
              int result1 = multiplication.apply(5, 3); // result1 will be 15
      
              // Custom functional interface with an instance main method
              Operation subtraction = (a, b) -> a - b;
              int result3 = subtraction.operate(10, 3); // result3 will be 7
      
              Operation division = (a, b) -> a / b;
              int result4 = division.operate(15, 5); // result4 will be 3
      
              System.out.println("Multiplication: " + result1);
              System.out.println("Subtraction: " + result3);
              System.out.println("Division: " + result4);
              }
            }
            
            // Custom functional interface with an instance main method
            @FunctionalInterface
            interface Operation {
                int operate(int a, int b);
           }
   ```
    
  ### Functional Interface with Method Reference (Methode Instance)
  - `Method Reference:` A method reference is a shorthand notation for invoking a method or passing it as a parameter. It provides a way to refer to a method without executing it directly, typically by using the `::` operator followed by the method name. Method references are often used in functional.
    
  ```java
      public class Main {
        public static void main(String[] args) {
    
            // Using a method reference for addition
            BinaryOperator<Integer> addition = Main::add;
            int result2 = addition.apply(10, 5); // result2 will be 15
  
            System.out.println("Addition: " + result2);

            // Using a method reference for conversion to upper case
            UnaryOperator<String> toUpperCase = String::toUpperCase;
            String upperCaseString = toUpperCase.apply("hello"); // upperCaseString will be "HELLO"
    
            System.out.println("Uppercase String: " + upperCaseString);
            }
    
              // Static method for addition
              static int add(int a, int b) {
                  return a + b;
              }
          }
  ```


## Java OOP (Object-Oriented Programming)
 ### 1. Encapsulation 
   - `Encapsulation` is the mechanism of bundling the data `(attributes)` and the methods `(functions)` that operate on the data into a single unit called a class.
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
   - `Inheritance` is a mechanism in which a new class inherits properties and behavior `(methods)` from an existing class.
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
  - `Polymorphism` is the ability of an object to take on different forms or behaviors depending on the context in which it is used. There are two types of polymorphism in Java: compile-time `(method overloading)` and runtime `(method overriding)`.
    
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

 ### 7. Interface & Class
 
  - `Interface` is a reference type, similar to a class, that can contain only constants, method signatures, default methods, static methods, and nested types.
  - All methods declared in an interface are implicitly `public` and `abstract`. They cannot contain methods with implementation.
  - Classes that implement an interface must provide an `implementation` for all methods declared in that interface.
  - A class can implement `multiple interfaces`, thus providing increased flexibility in program design.
  - Interfaces can be used to define types, enabling `polymorphism`.
  - Extend one or more interfaces

   ```java
     interface MyInterface {
      void abstractMethod(); // Abstract method
  
      default void defaultMethod() { // Default method
          System.out.println("This is a default method.");
        }
      }
   ```
   ```java
    class MyClass implements MyInterface {
    public void abstractMethod() {
       System.out.println("Implementing the abstract method.");
          }
      }
   ```
   ```java
    public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.abstractMethod(); // Calling the abstract method
        obj.defaultMethod();  // Calling the default method
        }
    }
   ```

  - An abstract class is a class that cannot be `instantiated` directly.
  - It can contain both `abstract methods` (methods without implementation) and `concrete methods` (methods with implementation).
  - An abstract class can have instance variables, constructors, and methods with or without implementation.
  - Subclasses must extend an abstract class and implement all its abstract methods, unless they are also declared abstract.
  - An abstract class can also provide default implementation for some methods, which subclasses may choose to override or not.
  - Cannot be declared `final`
  - Abstract methods should not be `private`
  - An `abstract class` can partially implement an `interface`
    
 ```java
     // Abstract class
    abstract class Vehicle {
        abstract void drive();
    
        void stop() {
            System.out.println("Vehicle stopped");
        }
    }

  ```
 ```java
    // Class implementing an interface and extending an abstract class
    class Car extends Vehicle implements Animal {
        @Override
        void drive() {
            System.out.println("Car is being driven");
        }
    
        @Override
        public void makeSound() {
            System.out.println("Car honks");
        }
    }
 ```
```java
    public class Main {
        public static void main(String[] args) {
            Car myCar = new Car();
            myCar.drive();
            myCar.makeSound();
            myCar.stop();
        }
    }
```

### 8. Static
   - `Static Variable:` When a variable is declared as static within a class, it means that the variable belongs to the class itself rather than to any instance of the class. There will be only one copy of a static variable regardless of how many instances of the class are created. 

  ```java
      public class MyClass {
      public static int myStaticVariable = 10;
  
      public static void main(String[] args) {
          MyClass obj1 = new MyClass();
          MyClass obj2 = new MyClass();
  
          // Both objects share the same static variable
          obj1.myStaticVariable = 20;
  
          System.out.println("obj1 static variable: " + obj1.myStaticVariable);
          System.out.println("obj2 static variable: " + obj2.myStaticVariable);
      }
  }
```

  - `Static Method:`static method is a method that belongs to the class rather than to any specific instance of the class. This means you can call a static method without creating an instance of the class.
  - `No Access to Instance Variables `: Static methods cannot access instance variables directly because they don't belong to any instance. However, they can access static variables.
  - Cannot Use `this` Keyword Since static methods are not tied to any particular instance, they cannot use the this keyword to refer to the current instance.
  - Can Call other `static` methods directly.
    
  ```java
       public class MyClass {
      
            static void myStaticMethod() {
                System.out.println("This is a static method.");
            }
        
            public static void main(String[] args) {
                MyClass.myStaticMethod();
              }
            }
  ```
```java
public class MyClass {
    private static int count = 0; // Static variable

    public void incrementCount() {
        count++; // Accessing and modifying the static variable
    }

    public int getCount() {
        return count; // Accessing the static variable
    }
}
```
 ```java
      public class Main {  
      public static void main(String[] args) {
        MyClass.incrementCount();
        System.out.println(MyClass.getCount());
      }
  }
```
  - `Static Class:` In Java, classes themselves cannot be declared as static. They are loaded into memory when the program starts, and each instance of the class has its own memory. However, nested static classes are allowed. These nested classes belong to the outer class and can be instantiated without requiring an instance of the outer class.
    
 ```java
     public class OuterClass {
          static class NestedStaticClass {
              void display() {
                  System.out.println("This is a static nested class.");
              }
          }
      
          public static void main(String[] args) {
              OuterClass.NestedStaticClass nested = new OuterClass.NestedStaticClass();
              nested.display();
          }
     }
  ```

### 9. Final
- `Final Attribute (Variable):` A final attribute cannot be reassigned once initialized.
  
  ```java
    class MyClass {
        // Final attribute
        final int constant = 10;
    
        // Method attempting to change the value of constant
        public void changeValue() {
            // This would result in a compilation error
            // constant = 20;
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            // Instantiate MyClass
            MyClass obj = new MyClass();
            // Access constant attribute
            System.out.println("Constant value: " + obj.constant);
        }
    }
  ```

- `Final Method:` A final method cannot be overridden in subclasses.
  
  ```java
      class Parent {
        // Final method
            public final void finalMethod() {
                // Method implementation
            }
        }
        
        public class Child extends Parent {
            // Attempting to override finalMethod will result in a compilation error
            // public void finalMethod() { }
            
            public static void main(String[] args) {
                // Instantiate Child class
                Child child = new Child();
                // Call finalMethod
                child.finalMethod();
            }
        }
  ```
- `Final Class:` When a class is declared as final, it means that it cannot be subclassed. This prevents other classes from inheriting from it.
  
   ```java
      final class FinalClass {
            // Class members and methods
        }
        
        public class Main {
            public static void main(String[] args) {
                // Instantiate FinalClass
                FinalClass obj = new FinalClass();
                // Access methods or members of FinalClass
            }
        }
   ```


