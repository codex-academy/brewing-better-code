# Introduction to the Visitor Pattern

The `Visitor Pattern` is a behavioral design pattern that allows you to add further operations to objects without modifying their classes. Instead of embedding the logic within the objects themselves, you define a separate visitor that performs actions on them. This pattern is especially useful when dealing with groups of objects that may need different types of operations or behavior added over time, all without altering the underlying object structures.

In this tutorial, we will explore the `Visitor Pattern` through a coffee shop example. Imagine you run a coffee shop offering different types of coffee, and over time, you need to apply new operations like calculating discounts or measuring calories. Instead of hardcoding these operations inside each coffee type (which would make the code less flexible), you can define visitors that handle these operations externally.

By the end of this tutorial, you'll see how to:

* Implement the Visitor Pattern using TypeScript.
* Apply visitors to objects like `Espresso, Latte, and Cappuccino` to perform operations such as discount calculation and calorie counting.
* Extend your codebase with new operations while keeping your coffee objects clean and easy to maintain.

Let's dive in and see how the Visitor Pattern helps us create a flexible and extensible coffee shop system!

## Step 1: Define the Coffee Interface and Coffee Types

Start by defining the Coffee interface and different types of coffee.

```typescript

interface Coffee {
  accept(visitor: CoffeeVisitor): void;
}

class Espresso implements Coffee {
  accept(visitor: CoffeeVisitor): void {
    visitor.visitEspresso(this);
  }

  cost(): number {
    return 3.0;
  }

  calories(): number {
    return 50;
  }
}

class Latte implements Coffee {
  accept(visitor: CoffeeVisitor): void {
    visitor.visitLatte(this);
  }

  cost(): number {
    return 4.5;
  }

  calories(): number {
    return 150;
  }
}

class Cappuccino implements Coffee {
  accept(visitor: CoffeeVisitor): void {
    visitor.visitCappuccino(this);
  }

  cost(): number {
    return 4.0;
  }

  calories(): number {
    return 100;
  }
}

```

Here, we define a `Coffee` interface with an accept method that accepts a visitor. Each coffee type (e.g., Espresso, Latte, Cappuccino) implements this method and provides other properties, like cost and calories.

## Step 2: Define the Visitor Interface and Concrete Visitors

Next, define the `CoffeeVisitor` interface and different visitors that implement this interface to perform various operations.

```typescript

interface CoffeeVisitor {
  visitEspresso(espresso: Espresso): void;
  visitLatte(latte: Latte): void;
  visitCappuccino(cappuccino: Cappuccino): void;
}

class DiscountVisitor implements CoffeeVisitor {
  visitEspresso(espresso: Espresso): void {
    console.log(`Espresso cost after discount: ${espresso.cost() * 0.9}`);
  }

  visitLatte(latte: Latte): void {
    console.log(`Latte cost after discount: ${latte.cost() * 0.85}`);
  }

  visitCappuccino(cappuccino: Cappuccino): void {
    console.log(`Cappuccino cost after discount: ${cappuccino.cost() * 0.8}`);
  }
}

class CalorieVisitor implements CoffeeVisitor {
  visitEspresso(espresso: Espresso): void {
    console.log(`Espresso has ${espresso.calories()} calories`);
  }

  visitLatte(latte: Latte): void {
    console.log(`Latte has ${latte.calories()} calories`);
  }

  visitCappuccino(cappuccino: Cappuccino): void {
    console.log(`Cappuccino has ${cappuccino.calories()} calories`);
  }
}

```

Here, the CoffeeVisitor interface defines visit methods for each coffee type. The DiscountVisitor and CalorieVisitor classes implement the visitor interface and apply specific operations like applying discounts and calculating calories.

## Step 3: Use the Visitor Pattern

Now, you can create instances of coffee and visitors, and apply the visitors to the coffee objects.

```ts
const espresso = new Espresso();
const latte = new Latte();
const cappuccino = new Cappuccino();

const discountVisitor = new DiscountVisitor();
const calorieVisitor = new CalorieVisitor();

// Apply discount visitor
espresso.accept(discountVisitor);   // Espresso cost after discount: 2.7
latte.accept(discountVisitor);      // Latte cost after discount: 3.825
cappuccino.accept(discountVisitor); // Cappuccino cost after discount: 3.2

// Apply calorie visitor
espresso.accept(calorieVisitor);   // Espresso has 50 calories
latte.accept(calorieVisitor);      // Latte has 150 calories
cappuccino.accept(calorieVisitor); // Cappuccino has 100 calories

```

## Step 4: Tests for the Visitor Pattern Coffee Example

Here is a list of tests that should be written to ensure the functionality of the Visitor Pattern implementation using **MochaJS** and **TypeScript**:

- **Test Espresso with DiscountVisitor**:
  - Ensure `DiscountVisitor` applies the correct discount to an `Espresso`.

- **Test Latte with DiscountVisitor**:
  - Ensure `DiscountVisitor` applies the correct discount to a `Latte`.

- **Test Cappuccino with DiscountVisitor**:
  - Ensure `DiscountVisitor` applies the correct discount to a `Cappuccino`.

- **Test Espresso with CalorieVisitor**:
  - Ensure `CalorieVisitor` correctly calculates the calories for an `Espresso`.

- **Test Latte with CalorieVisitor**:
  - Ensure `CalorieVisitor` correctly calculates the calories for a `Latte`.

- **Test Cappuccino with CalorieVisitor**:
  - Ensure `CalorieVisitor` correctly calculates the calories for a `Cappuccino`.

- **Test Multiple Visitors on Coffee**:
  - Ensure that both `DiscountVisitor` and `CalorieVisitor` can be applied in sequence to each coffee type without issues.


## Summary

The `Visitor` Pattern separates functionality (like discounts or calorie calculations) from the coffee classes themselves.

* Each `Coffee` class accepts a visitor, and the visitor performs operations based on the type of coffee.
* This pattern makes it easy to extend the system with new operations (like adding a new visitor) without modifying the coffee classes.
* This approach keeps your system flexible and maintainable, especially when you need to add new functionalities.
