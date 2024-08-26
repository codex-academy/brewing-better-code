# Strategy Pattern Tutorial: Brewing Coffee with Different Methods

## Introduction

In this tutorial, we'll explore the Strategy design pattern using coffee brewing methods as an example. The Strategy pattern allows you to define a family of algorithms, encapsulate each one, and make them interchangeable. This pattern is particularly useful for choosing the appropriate algorithm (or strategy) at runtime.

## Objective

You will implement different coffee brewing strategies and use them interchangeably to brew coffee. You’ll also write unit tests using Mocha with ts-mocha to verify the correct behavior of your strategies.

## Step-by-Step Guide

### Step 1: Define the Strategy Interface

1. **Create a new file `BrewingStrategy.ts` to define the strategy interface.**

   ```typescript
   // BrewingStrategy.ts
   export interface BrewingStrategy {
     brew(): string;
   }


## Step 2: Implement Concrete Strategies

Create concrete strategy classes for different brewing methods.

Espresso Strategy

```typescript
Copy code
// EspressoStrategy.ts
import { BrewingStrategy } from './BrewingStrategy';

export class EspressoStrategy implements BrewingStrategy {
  public brew(): string {
    return 'Brewing espresso using an espresso machine.';
  }
}
```


French Press Strategy

```typescript

// FrenchPressStrategy.ts
import { BrewingStrategy } from './BrewingStrategy';

export class FrenchPressStrategy implements BrewingStrategy {
  public brew(): string {
    return 'Brewing coffee using a French press.';
  }
}
```

## Step 3: Define the Context

Create a CoffeeContext class that uses the strategy.

```typescript

// CoffeeContext.ts
import { BrewingStrategy } from './BrewingStrategy';

export class CoffeeContext {
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

## Step 4: Write Unit Tests

Create a new file CoffeeContext.test.ts for the unit tests.

```typescript

import { expect } from 'chai';
import { CoffeeContext } from './CoffeeContext';
import { EspressoStrategy } from './EspressoStrategy';
import { FrenchPressStrategy } from './FrenchPressStrategy';

describe('CoffeeContext Strategy Pattern', () => {
  it('should brew coffee using Espresso strategy', () => {
    const espressoStrategy = new EspressoStrategy();
    const context = new CoffeeContext(espressoStrategy);
    const result = context.brewCoffee();
    expect(result).to.equal('Brewing espresso using an espresso machine.');
  });

  it('should brew coffee using French Press strategy', () => {
    const frenchPressStrategy = new FrenchPressStrategy();
    const context = new CoffeeContext(frenchPressStrategy);
    const result = context.brewCoffee();
    expect(result).to.equal('Brewing coffee using a French press.');
  });

  it('should switch strategies at runtime', () => {
    const espressoStrategy = new EspressoStrategy();
    const frenchPressStrategy = new FrenchPressStrategy();
    const context = new CoffeeContext(espressoStrategy);

    let result = context.brewCoffee();
    expect(result).to.equal('Brewing espresso using an espresso machine.');

    context.setStrategy(frenchPressStrategy);
    result = context.brewCoffee();
    expect(result).to.equal('Brewing coffee using a French press.');
  });
});
```

## Step 5: Run the Tests

Create some tests using Mocha with ts-mocha.

Make sure that your tests are



## Conclusion

Great job! You’ve implemented the Strategy pattern using different coffee brewing methods and verified its behavior with unit tests. The Strategy pattern provides a flexible way to switch between different algorithms or behaviors at runtime, making your code more adaptable and maintainable.