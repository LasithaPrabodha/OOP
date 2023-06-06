## Object Oriented Programming
Object-oriented programming (OOP) is a programming paradigm or approach that organizes software design around objects, which are instances of classes. It provides a way to structure and design programs by representing real-world objects as software objects. OOP emphasizes the concept of encapsulation, where data and the methods that operate on that data are bundled together into objects.

In OOP, a class is a blueprint or template for creating objects. It defines the properties (attributes or data) and behaviors (methods or functions) that objects of that class possess. An object is an instance of a class, created using the class definition, and it can have its own unique state and behavior while still belonging to a certain class.

Let's explore the main principles of object-oriented programming (OOP) and how they apply to C#:

1. Encapsulation:
    Encapsulation is the concept of bundling data and related behaviors (methods) together within an object. In C#, you can achieve encapsulation using classes. The class acts as a container for data members (fields) and member functions (methods). You can define access modifiers such as public, private, protected, or internal to control the visibility and accessibility of these members. Encapsulation helps in hiding the internal implementation details of an object and provides a clear interface for interacting with it.
    <br>

    Example in C#:
    ```csharp
    public class BankAccount
    {
        private decimal balance;  // Private field

        public void Deposit(decimal amount)
        {
            // Method to deposit funds
            balance += amount;
        }

        public decimal GetBalance()
        {
            // Method to retrieve balance
            return balance;
        }
    }
    ```

2. Inheritance:
    Inheritance allows you to create new classes (derived or child classes) based on existing classes (base or parent classes). The derived classes inherit the properties and behaviors of the base classes, and you can extend or modify them as needed. In C#, you can use the `: ` symbol to denote inheritance.
    <br>
    
    Example in C#:
    ```csharp
    public class Animal  // Base class
    {
        public void Eat()
        {
            Console.WriteLine("Animal is eating.");
        }
    }

    public class Dog : Animal  // Derived class
    {
        public void Bark()
        {
            Console.WriteLine("Dog is barking.");
        }
    }
    ```

3. Polymorphism:
    Polymorphism refers to the ability of objects to take on multiple forms or to be treated as instances of their base classes. In C#, you can achieve polymorphism through method overriding and method overloading. Method overriding allows derived classes to provide their own implementation of a method defined in the base class. Method overloading allows multiple methods with the same name but different parameters to coexist within a class.
    <br>

    Example in C#:
    ```csharp
    public class Shape
    {
        public virtual void Draw()
        {
            Console.WriteLine("Drawing a shape.");
        }
    }

    public class Circle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("Drawing a circle.");
        }
    }

    public class Rectangle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("Drawing a rectangle.");
        }
    }
    ```

4. Abstraction:
    Abstraction involves representing complex systems by providing simplified views or models. In C#, you can use abstract classes and interfaces to achieve abstraction. Abstract classes cannot be instantiated and are used as base classes for derived classes. They can have both abstract and non-abstract methods. Interfaces define a contract of methods and properties that implementing classes must adhere to.
    <br>
    
    Example in C#:
    ```csharp
    public abstract class Shape
    {
        public abstract void Draw();
    }

    public interface IResizable
    {
        void Resize(int width, int height);
    }
    ```

These principles form the foundation of object-oriented programming and are widely used in C# to create modular, reusable, and maintainable code.