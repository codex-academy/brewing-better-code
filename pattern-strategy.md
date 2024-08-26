# Strategy Pattern Tutorial: Brewing Coffee with Different Methods

## Introduction

The Strategy Pattern is a behavioral design pattern that enables you to define a family of algorithms, encapsulate each one, and make them interchangeable. This pattern is particularly useful when you have multiple ways to perform an action, and you want to be able to switch between them dynamically without altering the client code that uses these algorithms.

In this tutorial, we'll explore how to use the Strategy Pattern in the context of brewing coffee. You might brew coffee using various methods such as an espresso machine, a French press, or a pour-over method. Each of these methods can be treated as a strategy, and the coffee maker (the context) can be configured to use any of these strategies at runtime.

## Objective

You will implement different coffee brewing strategies and a coffee maker that can switch between these strategies. You’ll also write unit tests using Mocha with ts-mocha to verify that the strategies are applied correctly.

## Step-by-Step Guide

### Step 1: Define the Strategy Interface

Create a BrewingStrategy interface that represents the strategy for brewing coffee.

```typescript
// BrewingStrategy.ts
export interface BrewingStrategy {
  brew(): string;
}
```


**Explanation:** The `BrewingStrategy` interface defines a method `brew()`, which all specific brewing strategies will implement. Each strategy will have its own way of brewing coffee, returning a description of the brewing process.

### Step 2: Implement Concrete Strategies

Create classes for different brewing methods that implement the `BrewingStrategy` interface.

**Espresso Strategy**

```typescript

// EspressoStrategy.ts
import { BrewingStrategy } from './BrewingStrategy';

export class EspressoStrategy implements BrewingStrategy {
  public brew(): string {
    return 'Brewing coffee with an espresso machine.';
  }
}
```

Explanation: The `EspressoStrategy` class implements the BrewingStrategy interface and provides the specific brewing process for an espresso machine.

**French Press Strategy**

```typescript

// FrenchPressStrategy.ts
import { BrewingStrategy } from './BrewingStrategy';

export class FrenchPressStrategy implements BrewingStrategy {
  public brew(): string {
    return 'Brewing coffee with a French press.';
  }
}
```

Explanation: The `FrenchPressStrategy` class implements the BrewingStrategy interface and provides the specific brewing process for a French press.

**Pour Over Strategy**

```typescript

// PourOverStrategy.ts
import { BrewingStrategy } from './BrewingStrategy';

export class PourOverStrategy implements BrewingStrategy {
  public brew(): string {
    return 'Brewing coffee with a pour-over method.';
  }
}
```

**Explanation**: The `PourOverStrategy` class implements the `BrewingStrategy` interface and provides the specific brewing process for a pour-over method.

### Step 3: Create the Context Class
Create a CoffeeMaker class that will use a BrewingStrategy to brew coffee.


```typescript

// CoffeeMaker.ts
import { BrewingStrategy } from './BrewingStrategy';

export class CoffeeMaker {
  private strategy: BrewingStrategy;

  constructor(strategy: BrewingStrategy) {
    this.strategy = strategy;
  }

  public setStrategy(strategy: BrewingStrategy): void {
    this.strategy = strategy;
  }

  public brewCoffee(): string {
    return this.strategy.brew();
  }
}
```

**Explanation**: The `CoffeeMaker` class acts as the context that uses a `BrewingStrategy` to brew coffee. It allows you to set different brewing strategies dynamically and use them to brew coffee.

### Step 4: Write Unit Tests

Create a new file `CoffeeMaker.test.ts` for the unit tests.

Here’s a list of tests to be written for the Strategy Pattern tutorial:

**Test Brewing Coffee with Espresso Strategy**

**Description**: Verify that the `CoffeeMaker` correctly brews coffee using the `EspressoStrategy`. The output should match the expected description of brewing with an espresso machine.

**Test Brewing Coffee with French Press Strategy**

**Description**: Ensure that the `CoffeeMaker` brews coffee using the `FrenchPressStrategy`. The returned value should match the expected description of brewing with a French press.

**Test Brewing Coffee with Pour Over Strategy**

**Description**: Check that the CoffeeMaker brews coffee using the `PourOverStrategy`. The output should be the correct description of brewing with a pour-over method.

**Test Switching Brewing Strategies at Runtime**

**Description**: Verify that the `CoffeeMaker` can switch between different brewing strategies at runtime. Test the transitions from `EspressoStrategy` to `FrenchPressStrategy` and then to `PourOverStrategy`, ensuring the correct brewing process is applied at each step.

Each of these tests ensures that the CoffeeMaker properly applies the selected brewing strategy and that the strategies can be switched dynamically without any issues.

## Conclusion

Congratulations! You’ve successfully implemented the Strategy Pattern to brew coffee using different methods. The Strategy Pattern provides a powerful way to encapsulate different algorithms and make them interchangeable. This approach is highly useful in scenarios where you want to provide multiple ways to perform an action and switch between them dynamically.