# Java Fundamentals for Spring Boot

## Introduction
This documentation aims to provide an overview of fundamental Java concepts necessary for working with Spring Boot.

## Table of Contents
- [What is JDK, JRE and JVM in Java](#what-is-JDK-JRE-and-JVM-in-java)
- [How to Execute a Java Program](#how-to-execute-java-program)
- [Loops](#loops)
- [Conditional Statements](#conditional-statements)
- [Classes and Objects](#classes-and-objects)
- [Interfaces](#interfaces)
- [Exception Handling](#exception-handling)

## What is JDK, JRE and JVM in Java
1. **JDK(Java Development Kit)**
   - The JDK(Java Development Kit) is a superset of the JRE and contains everything that is in the JRE, plus tools such as the compiler, debugger, JavaDoc, keytool etc necessary for developing and running Java programs or applications.
     
     ![Java JDK JRE and JVM](https://github.com/douaeelh2/Java-Documentation/assets/127549220/ab43eb26-79a7-4936-8ace-10da5a248a51)

2. **JVM (Java Virtual Machine)**
   - JVM is a very important component of Java programming language. When you run the Java program, the Java compiler first compiles your Java code to bytecode. Then, the JVM translates bytecode into native machine code (set of instructions that a computer's CPU executes directly).
   - JVM is called virtual because it provides an interface that does not depend on the underlying operating system and machine hardware.

3. **3. JRE(Java Runtime Environment)**
   - The Java Runtime Environment (JRE) provides the libraries, the Java Virtual Machine, and other components to run applets and applications written in the Java programming language.
JRE doesn’t contain any development tools such as Java compiler, debugger, JShell, etc.
   - If you just want to execute a java program, you can install only JRE. You don’t need JDK because there is no development or compilation of java source code is required.


## How to Execute a Java Program
1. **Writing the Source Code:** 
   - Begin by writing your Java program using a text editor or an Integrated Development Environment (IDE) such as Eclipse, Netbeans, or IntelliJ IDEA. Save the Java source code in files with the .java extension.

2. **Compilation:** 
   - Compile your Java source code into bytecode using a Java compiler included in the Java Development Kit (JDK). You can compile your code using the javac command-line tool or built-in features of an IDE. Compilation converts your Java source code into .class files containing Java bytecode.

3. **Runtime Environment (JRE):** 
   - To execute the Java bytecode, install the Java Runtime Environment (JRE), which includes the Java Virtual Machine (JVM) and standard Java class libraries. The JRE provides an environment for executing Java bytecode.

4. **Running the Program:** 
   - Once the JRE is installed, run your Java program using the java command followed by the name of the class containing the main() method in your terminal or command prompt.


## Polymorphism
- **Overloading:**
   - Overloading occurs when a class has multiple methods with the same name but different parameter lists. Overloaded methods can have different return types but must have different parameter lists.
   ```java
   class Calculator {
       // Example of method overloading
   }
