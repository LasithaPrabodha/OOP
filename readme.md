## Object Oriented Programming
Object-oriented programming (OOP) is a programming paradigm or approach that organizes software design around objects, which are instances of classes. It provides a way to structure and design programs by representing real-world objects as software objects. OOP emphasizes the concept of encapsulation, where data and the methods that operate on that data are bundled together into objects.

In OOP, a class is a blueprint or template for creating objects. It defines the properties (attributes or data) and behaviors (methods or functions) that objects of that class possess. An object is an instance of a class, created using the class definition, and it can have its own unique state and behavior while still belonging to a certain class.

Classes interact with each other to accomplish one or more features of an application. You can define the relationship between classes while designing the classes of your application. These relationships define how classes or objects interact with each other, share information, and collaborate to achieve a specific functionality.

Let's explore each relationship with realistic examples in C#:

1. Inheritance:
    Inheritance represents an "is-a" relationship between classes. The derived class inherits properties and behaviors from the base class. Let's consider an example:

    ```csharp
    public class Animal
    {
        public string Name { get; set; }
        public virtual void MakeSound()
        {
            Console.WriteLine("The animal makes a sound.");
        }
    }

    public class Dog : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("The dog barks.");
        }
    }
    ```

    In this example, the `Dog` class inherits from the `Animal` class. The `Dog` class extends the behavior of the `Animal` class and overrides the `MakeSound` method with its specific implementation.
    <br>

2. Aggregation:
    Aggregation represents a "has-a" relationship between classes, where one class contains a collection of other objects. Let's consider an example where a `Department` class contains a collection of `Employee` objects:

    ```csharp
    public class Department
    {
        public string Name { get; set; }
        public List<Employee> Employees { get; set; }
    }

    public class Employee
    {
        public string Name { get; set; }
        // Other employee properties
    }
    ```

    In this example, the `Department` class has an aggregation relationship with the `Employee` class. The `Department` class has a collection of `Employee` objects stored in the `Employees` property.
    <br>
    
3. Composition (Part-Whole):
    Composition represents a strong form of aggregation, where one class (the whole) is composed of one or more instances of another class (the part). The part objects cannot exist independently of the whole object. Let's consider an example:

    ```csharp
    public class Car
    {
        private Engine engine;

        public Car()
        {
            engine = new Engine();
        }
    }

    public class Engine
    {
        // Engine properties and methods
    }
    ```

    In this example, the `Car` class is composed of an `Engine` object. The `Car` class owns the `Engine` instance, and the `Engine` instance cannot exist independently of the `Car` instance.
    <br>
    
4. Dependency:
    Dependency represents a relationship where one class depends on another class. Let's consider an example where a `Customer` class depends on a `Logger` class:

    ```csharp
    public class Customer
    {
        private Logger logger;

        public Customer(Logger logger)
        {
            this.logger = logger;
        }

        public void DoSomething()
        {
            logger.Log("Customer is doing something.");
        }
    }

    public class Logger
    {
        public void Log(string message)
        {
            Console.WriteLine(message);
        }
    }
    ```

    In this example, the `Customer` class depends on the `Logger` class. The `Customer` class receives an instance of the `Logger` class through its constructor, allowing it to use the logging functionality provided by the `Logger` class.
    <br>
    
5. Realization/Implementation:
    Realization represents the relationship between an interface and a class that implements that interface. Let's consider an example where a `Shape` interface is realized by a `Circle` class:

    ```csharp
    public interface Shape
    {
        void Draw();
    }

    public class Circle : Shape
    {
        public void Draw()
        {
            Console.WriteLine("Drawing a circle.");
        }
    }
    ```

    In this example, the `Circle` class realizes the `Shape` interface by implementing the `Draw` method defined in the interface.
    <br>
    
6. Association (Bi-Directional):
    Association represents a relationship between classes where one class is related to another class. Let's consider an example where a `Student` class is associated with a `School` class,

    and the `School` class also maintains a reference to the associated `Student` objects:

    ```csharp
    public class Student
    {
        public string Name { get; set; }
        public School School { get; set; }
    }

    public class School
    {
        public string Name { get; set; }
        public List<Student> Students { get; set; }
    }
    ```

    In this example, the `Student` class is associated with the `School` class, and the `School` class maintains a list of associated `Student` objects. This allows navigation between the `Student` and `School` objects in both directions.
    <br>
    
7. Generalization/Specialization:
    Generalization represents a relationship where multiple classes share common characteristics, and a generalized superclass captures those commonalities. Specialization, also known as inheritance, represents the relationship where classes inherit from a generalized superclass and add specific features or behaviors. Let's consider an example:

    ```csharp
    public abstract class Vehicle
    {
        public string Brand { get; set; }
        public abstract void Drive();
    }

    public class Car : Vehicle
    {
        public override void Drive()
        {
            Console.WriteLine("Driving a car.");
        }
    }

    public class Bike : Vehicle
    {
        public override void Drive()
        {
            Console.WriteLine("Riding a bike.");
        }
    }
    ```

    In this example, the `Vehicle` class captures common properties and behaviors shared by different types of vehicles. The `Car` and `Bike` classes specialize the `Vehicle` class by inheriting from it and providing their specific implementations of the `Drive` method.

These examples demonstrate how the different relationships can be implemented in C# to model real-world scenarios and create well-structured and maintainable object-oriented code.

## Four pillars of OOP
Now let's explore the main principles of object-oriented programming (OOP) and how they apply to C#:

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

## SOLID Design Principles
The SOLID principles are a set of five design principles that provide guidelines for writing clean, maintainable, and extensible code. These principles were introduced by Robert C. Martin (also known as Uncle Bob) and have become fundamental concepts in object-oriented programming. The acronym "SOLID" stands for the following five principles:

1. Single Responsibility Principle (SRP):
    This principle states that a class should have only one reason to change, meaning it should have a single responsibility. Each class should be focused on doing one thing and doing it well. By adhering to this principle, you can achieve better code organization, maintainability, and testability.
    <br>
    
    Ex: Logging System
    In a logging system, you can have separate classes for logging and file management. The Logger class is responsible for handling log messages, while the FileManager class is responsible for managing log files. Each class has a single responsibility, making the code easier to understand and maintain.
    <br>

    Let's illustrate Single Responsibility Principle in C#:
    
    ```cs
    public class Logger
    {
        public void Log(string message)
        {
            // Logging implementation
        }
    }

    public class FileManager
    {
        public void ManageFiles()
        {
            // File management implementation
        }
    }
    ```

    In this example, the `Logger` class is responsible for logging messages, and the `FileManager` class is responsible for managing files. Each class has a single responsibility, making the code more modular and maintainable.
    <br>

2. Open-Closed Principle (OCP):
    The Open-Closed Principle states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, you should be able to extend the behavior of a system without modifying its existing code. This principle promotes the use of abstractions, interfaces, and inheritance to achieve flexibility and avoid code modification.
    <br>
    
    Ex: Plugin Architecture
    In a plugin architecture, you can define an interface for plugins and have a plugin manager that loads and executes plugins. The plugin manager is open for extension, as new plugins can be added without modifying the manager's code. This allows for the dynamic addition of functionality without impacting the existing system.
    <br>

    Let's illustrate Open-Closed Principle in C#:

    ```cs
    public interface IPlugin
    {
        void Execute();
    }

    public class PluginManager
    {
        private List<IPlugin> plugins;

        public PluginManager()
        {
            plugins = new List<IPlugin>();
        }

        public void AddPlugin(IPlugin plugin)
        {
            plugins.Add(plugin);
        }

        public void ExecutePlugins()
        {
            foreach (IPlugin plugin in plugins)
            {
                plugin.Execute();
            }
        }
    }
    ```

    In this example, the `PluginManager` class is open for extension as it can accept any plugin that implements the `IPlugin` interface. New plugins can be added without modifying the `PluginManager` class, allowing for the dynamic addition of functionality.
    <br>

3. Liskov Substitution Principle (LSP):
    The Liskov Substitution Principle defines that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. In other words, derived classes should be able to substitute their base classes seamlessly. This principle ensures that the behavior of the base class is preserved in the derived classes, allowing for polymorphism and avoiding unexpected issues.
    <br>
    
    Ex: Shape Hierarchy
    In a shape hierarchy, you can have a base Shape class and derived classes like Circle, Rectangle, and Triangle. The LSP ensures that these derived classes can be substituted for the base Shape class without breaking the behavior of the system. For example, you can have a method that accepts a Shape parameter and still work correctly when passed a Circle, Rectangle, or Triangle object.
    <br>

    Let's illustrate Liskov Substitution Principle in C#:

    ```cs
    public class Shape
    {
        public virtual double CalculateArea()
        {
            // Common area calculation logic
        }
    }

    public class Rectangle : Shape
    {
        public override double CalculateArea()
        {
            // Rectangle-specific area calculation logic
        }
    }

    public class Circle : Shape
    {
        public override double CalculateArea()
        {
            // Circle-specific area calculation logic
        }
    }
    ```

    In this example, the `Shape` class has a virtual method `CalculateArea()` that can be overridden in derived classes such as `Rectangle` and `Circle`. The LSP ensures that you can treat instances of these derived classes as instances of the base `Shape` class without affecting the correctness of the program.
    <br>


4. Interface Segregation Principle (ISP):
    The Interface Segregation Principle states that clients should not be forced to depend on interfaces they do not use. It promotes the idea of creating specific interfaces that are tailored to the needs of clients. This principle helps to avoid the problem of "fat" interfaces that force clients to implement unnecessary methods and allows for more cohesive and decoupled code.
    <br>

    Ex: Printer Interface
    In a printer system, you can define separate interfaces for printing, scanning, and faxing functionalities. Different types of printers can implement specific interfaces based on their capabilities. This way, clients can depend only on the interfaces they need, avoiding the burden of implementing unnecessary methods.
    <br>

    Let's illustrate Interface Segregation Principle in C#:

    ```cs
    public interface IPrinter
    {
        void Print();
    }

    public interface IScanner
    {
        void Scan();
    }

    public class AllInOnePrinter : IPrinter, IScanner
    {
        public void Print()
        {
            // Printing implementation
        }

        public void Scan()
        {
            // Scanning implementation
        }
    }
    ```

    In this example, separate interfaces (`IPrinter` and `IScanner`) are defined for printing and scanning functionalities. The `AllInOnePrinter` class implements both interfaces, but clients can depend on the specific interface they need (`IPrinter` or `IScanner`), avoiding unnecessary dependencies.
    <br>

5. Dependency Inversion Principle (DIP):
    The Dependency Inversion Principle states that high-level modules should not depend on low-level modules; both should depend on abstractions. It also states that abstractions should not depend on details; details should depend on abstractions. This principle promotes loose coupling and dependency injection, allowing for more flexible and testable code.

    By adhering to the SOLID principles, developers can create code that is easier to understand, maintain, and extend. These principles help to manage complexity, improve code quality, and facilitate the creation of robust software systems.
    <br>

    Ex: Payment Processor
    In a payment processing system, you can have a high-level PaymentProcessor class that depends on an abstract IPaymentGateway interface. Concrete payment gateways, such as PayPalGateway or StripeGateway, implement this interface. By depending on the abstraction (IPaymentGateway) instead of concrete implementations, the PaymentProcessor adheres to the DIP. This allows for easier swapping of payment gateways and promotes loose coupling.
    <br>

    Let's illustrate Dependency Inversion Principle in C#:

    ```cs
    public interface IPaymentGateway
    {
        void ProcessPayment(decimal amount);
    }

    public class PaymentProcessor
    {
        private IPaymentGateway paymentGateway;

        public PaymentProcessor(IPaymentGateway paymentGateway)
        {
            this.paymentGateway = paymentGateway;
        }

        public void ProcessPayment(decimal amount)
        {
            paymentGateway.ProcessPayment(amount);
        }
    }

    public class PayPalGateway : IPaymentGateway
    {
        public void ProcessPayment(decimal amount)
        {
            // PayPal payment processing logic
        }
    }

    public class StripeGateway : IPaymentGateway
    {
        public void ProcessPayment(decimal amount)
        {
            // Stripe payment processing logic
        }
    }
    ```

    In this example, the `PaymentProcessor` class depends on the abstraction (`IPaymentGateway`) instead of concrete implementations. This allows for easier swapping of payment gateways (e.g., `PayPalGateway` or `StripeGateway`) and promotes loose coupling between the `PaymentProcessor` and the specific payment gateway implementation.

    These code examples demonstrate how the SOLID principles can be implemented in C# to create maintainable, extensible, and loosely coupled code. Applying these principles helps to improve code quality, flexibility, and ease of maintenance in real-world scenarios.