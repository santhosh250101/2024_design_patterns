Factory Method Design Pattern in Java: Explained with Example
The Factory Method design pattern is a creational pattern that defines an interface for creating objects, but lets subclasses decide which class to instantiate. In simpler words, it separates the object creation logic from the object usage, allowing you to add new object types without modifying the existing code.

Key Components:

Factory Interface: Declares a method (createProduct()) that returns a product object.
Concrete Factories: Implement the createProduct() method to create specific types of products.
Product Interface: Defines the common interface for all product objects.
Concrete Products: Implement the Product interface and define the actual functionalities.
Benefits of Factory Method:

Flexibility: Allows you to easily add new product types by implementing new Concrete Factories without modifying the existing code.
Code Reusability: The core logic of creating products is reused across different factory implementations.
Maintainability: Easier to manage changes in product creation as they are isolated within their corresponding Concrete Factories.
Reduced Coupling: Decouples the code that creates objects from the code that uses them.
Example:

Let's imagine you're building a pizza delivery service application. You have different types of pizzas (Margherita, Pepperoni, Veggie) and need to create them based on user orders.

1. Product Interface:

public interface Pizza {
    String getName();
    void prepare();
}
2. Concrete Products:

public class MargheritaPizza implements Pizza {
    @Override
    public String getName() {
        return "Margherita Pizza";
    }

    @Override
    public void prepare() {
        System.out.println("Preparing a Margherita Pizza.");
    }
}

public class PepperoniPizza implements Pizza {
    @Override
    public String getName() {
        return "Pepperoni Pizza";
    }

    @Override
    public void prepare() {
        System.out.println("Preparing a Pepperoni Pizza.");
    }
}

// ... Other pizza types (VeggiePizza, etc.)
3. Factory Interface:

public interface PizzaFactory {
    Pizza createPizza();
}
4. Concrete Factories:

public class MargheritaFactory implements PizzaFactory {
    @Override
    public Pizza createPizza() {
        return new MargheritaPizza();
    }
}

public class PepperoniFactory implements PizzaFactory {
    @Override
    public Pizza createPizza() {
        return new PepperoniPizza();
    }
}

// ... Other factory implementations (VeggieFactory, etc.)
5. Usage:

public class Order {
    public static void main(String[] args) {
        // User orders a Margherita Pizza
        PizzaFactory factory = new MargheritaFactory();
        Pizza pizza = factory.createPizza();
        pizza.prepare(); // Output: "Preparing a Margherita Pizza."

        // User orders a Pepperoni Pizza
        factory = new PepperoniFactory();
        pizza = factory.createPizza();
        pizza.prepare(); // Output: "Preparing a Pepperoni Pizza."
    }
}
In this example:

Pizza is the product interface defining the common functionality of all pizzas.
MargheritaPizza, PepperoniPizza, etc. are concrete products implementing the Pizza interface.
PizzaFactory is the factory interface defining the method to create pizzas.
MargheritaFactory, PepperoniFactory, etc. are concrete factories that implement the PizzaFactory interface and return specific pizza objects.
The Order class demonstrates how to use different factories to create different types of pizzas.
This way, we can add new pizza types by creating new concrete product and factory classes, without modifying the existing Order class. This enhances code flexibility, maintainability, and reusability.

Remember, this is a simplified example. The complexity of the real-world implementation may involve more advanced scenarios like handling different toppings, sizes, etc. but the core concept of the Factory Method pattern remains the same.

Model
gemini-1.5-flash-001
Region 
us-central1 (Iowa)
Temperature 
0

2
2
Output token limit 
1

8192
8192
Add stop sequence
Press Enter after each sequence
We want your feedback .
