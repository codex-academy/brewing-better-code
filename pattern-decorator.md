# Decorator Pattern: A Coffee Example

## Introduction

The **Decorator Pattern** allows behavior to be added to individual objects, dynamically. This is useful when you need to extend the functionality of certain objects without affecting others, and it adheres to the **Open/Closed Principle** of software design, meaning objects should be open for extension but closed for modification.

In this tutorial, we will explore the Decorator Pattern using a coffee ordering system as an example. Imagine you're at a coffee shop, and you start with a simple black coffee. However, as you add different options like milk, sugar, or cream, the coffee evolves while still being a coffee at its core.

## The Problem

Let's consider a basic coffee order. We want to implement the following options:

- A base coffee.
- The ability to add extras like milk, sugar, and cream.

One solution might be to create subclasses for each possible combination of coffee and extras. For example, you could create classes like `CoffeeWithMilk`, `CoffeeWithSugar`, `CoffeeWithMilkAndSugar`, and so on. But this approach becomes unmanageable as the number of combinations grows.

### How Can the Decorator Pattern Help?

The Decorator Pattern lets us add extras to our coffee dynamically, without creating a new subclass for every combination. Instead of subclasses, we create **decorators** that add functionality to the base coffee.

## Coffee Example Using TypeScript

Let's implement this idea in TypeScript.

### Step 1: Create a Base Coffee Class

We will first define the `Coffee` interface and implement a basic `SimpleCoffee` class:

```typescript
interface Coffee {
  cost(): number;
  description(): string;
}

class SimpleCoffee implements Coffee {
  cost(): number {
    return 5; // Base price for a simple coffee
  }

  description(): string {
    return "Simple coffee";
  }
}
```

### Step 2: Create Coffee Decorators

Now, we can create decorators for the extras like milk, sugar, and cream.
Each decorator will implement the `Coffee` interface and wrap an instance of a `Coffee` object, adding its own functionality on top.

```typescript
class MilkDecorator implements Coffee {
  private coffee: Coffee;

  constructor(coffee: Coffee) {
    this.coffee = coffee;
  }

  cost(): number {
    return this.coffee.cost() + 1.5; // Milk adds $1.50 to the base price
  }

  description(): string {
    return `${this.coffee.description()}, with milk`;
  }
}

class SugarDecorator implements Coffee {
  private coffee: Coffee;

  constructor(coffee: Coffee) {
    this.coffee = coffee;
  }

  cost(): number {
    return this.coffee.cost() + 0.5; // Sugar adds $0.50 to the base price
  }

  description(): string {
    return `${this.coffee.description()}, with sugar`;
  }
}

class CreamDecorator implements Coffee {
  private coffee: Coffee;

  constructor(coffee: Coffee) {
    this.coffee = coffee;
  }

  cost(): number {
    return this.coffee.cost() + 1.0; // Cream adds $1.00 to the base price
  }

  description(): string {
    return `${this.coffee.description()}, with cream`;
  }
}
```

Each decorator class (`MilkDecorator`, `SugarDecorator`, and `CreamDecorator`) takes an instance of a Coffee object as input and adds functionality, like updating the description and price. This allows you to "decorate" the base coffee object with additional features like milk, sugar, or cream without modifying the base class itself.

### Step 3: Put It All Together

Let's see how we can order a coffee with different combinations of extras:

```typescript
// Start with a simple coffee
let myCoffee: Coffee = new SimpleCoffee();
console.log(myCoffee.description()); // Simple coffee
console.log(myCoffee.cost());        // 5

// Add milk
myCoffee = new MilkDecorator(myCoffee);
console.log(myCoffee.description()); // Simple coffee, with milk
console.log(myCoffee.cost());        // 6.5

// Add sugar
myCoffee = new SugarDecorator(myCoffee);
console.log(myCoffee.description()); // Simple coffee, with milk, with sugar
console.log(myCoffee.cost());        // 7.0

// Add cream
myCoffee = new CreamDecorator(myCoffee);
console.log(myCoffee.description()); // Simple coffee, with milk, with sugar, with cream
console.log(myCoffee.cost());        // 8.0
```

## Step 4: Explanation

Each decorator wraps the Coffee object and adds its own behavior. For example, the `MilkDecorator` adds milk and increases the cost, 
while preserving the ability to add more decorators like `SugarDecorator` or `CreamDecorator`. 
This allows us to build complex combinations of coffee orders without needing an explosion of subclasses.

### Advantages of the Decorator Pattern

**Flexibility:** The `Decorator Pattern` allows us to add responsibilities to objects at runtime, offering more flexibility than subclassing.
**Scalability:** You can add as many decorators as needed without having to modify the existing code.
**Single Responsibility:** Each decorator has a single responsibility, making it easier to manage and understand.

## Step 5: Tests to Write Using MochaJS & TypeScript

Here is a list of tests that should be written to ensure the functionality of the coffee ordering system, using **MochaJS** and **TypeScript**.

- **Test Basic Coffee**: 
  - Ensure a `SimpleCoffee` returns the correct description and cost.

- **Test Coffee with Milk**: 
  - Verify that adding milk to a coffee updates the description and cost.

- **Test Coffee with Sugar**: 
  - Check that adding sugar to a coffee updates the description and cost.

- **Test Coffee with Cream**: 
  - Confirm that adding cream to a coffee updates the description and cost.

- **Test Coffee with Multiple Extras**:
  - Ensure that adding milk, sugar, and cream to a coffee updates both the description and cost accurately.

- **Test Order of Decorators**:
  - Ensure the order of applying decorators does not affect the final result (the description and cost should remain the same regardless of the order of decorators).


## Conclusion

The `Decorator Pattern` is a powerful design pattern that helps manage complex behavior dynamically without bloating your codebase with numerous subclasses. In the coffee shop example, it allowed us to create a system where customers can add extras like milk, sugar, and cream to their orders easily and flexibly.

Next time you're designing a system with many combinations or optional features, consider using the Decorator Pattern to keep your code simple and scalable.




