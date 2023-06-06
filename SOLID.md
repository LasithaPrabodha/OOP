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

    In this example, the `PaymentProcessor` class depends on the abstraction (`IPaymentGateway`) instead of concrete implementations. This allows for easier swapping of payment gateways (e.g., `PayPal

    Gateway` or `StripeGateway`) and promotes loose coupling between the `PaymentProcessor` and the specific payment gateway implementation.

    These code examples demonstrate how the SOLID principles can be implemented in C# to create maintainable, extensible, and loosely coupled code. Applying these principles helps to improve code quality, flexibility, and ease of maintenance in real-world scenarios.