# The Builder Pattern

Explanation: The Builder pattern allows you to construct complex objects step by step. It separates the construction of a complex object from its representation so that the same construction process can create different representations.

## Step 1: Implement the Builder Pattern

To implement the Builder Pattern follow the steps below.

### Create the Coffee class:

The Coffee class represents the complex object that we will build.

```typescript
// src/Coffee.ts
export class Coffee {
    public type: string;
    public size: string;
    public sugar: number;
    public milk: boolean;

    constructor() {
        this.type = '';
        this.size = '';
        this.sugar = 0;
        this.milk = false;
    }
}
```

**Explanation**: The Coffee class contains all the properties that define a cup of coffee. These properties will be set using the builder.

### Create the CoffeeBuilder class:

The `CoffeeBuilder` class provides methods to set each property of the Coffee object.

```typescript
// src/CoffeeBuilder.ts
import { Coffee } from './Coffee';

export class CoffeeBuilder {
    private coffee: Coffee;

    constructor() {
        this.coffee = new Coffee();
    }

    public setType(type: string): CoffeeBuilder {
        this.coffee.type = type;
        return this;
    }

    public setSize(size: string): CoffeeBuilder {
        this.coffee.size = size;
        return this;
    }

    public addSugar(sugar: number): CoffeeBuilder {
        this.coffee.sugar = sugar;
        return this;
    }

    public addMilk(): CoffeeBuilder {
        this.coffee.milk = true;
        return this;
    }

    public build(): Coffee {
        return this.coffee;
    }
}
```

**Explanation**: The `CoffeeBuilder` class provides a fluent interface to build a Coffee object step by step. Each method sets a property of the Coffee object and returns the builder itself.

### Create the Director class (optional):

The `CoffeeDirector` class can be used to construct a Coffee object with a specific configuration.

```typescript

// src/CoffeeDirector.ts
import { CoffeeBuilder } from './CoffeeBuilder';

export class CoffeeDirector {
    private builder: CoffeeBuilder;

    constructor(builder: CoffeeBuilder) {
        this.builder = builder;
    }

    public makeEspresso(): CoffeeBuilder {
        return this.builder.setType('Espresso').setSize('Small').addSugar(1).addMilk();
    }

    public makeLatte(): CoffeeBuilder {
        return this.builder.setType('Latte').setSize('Large').addSugar(2).addMilk();
    }
}
```

**Explanation:** The CoffeeDirector class simplifies the process of creating specific types of coffee by providing predefined configurations.

## Step 2: Write Unit Tests

Testing the Builder pattern involves verifying that the builder correctly constructs the complex object with the desired properties.

Test that your builder pattern implementation is doing the following:

* can build a basic coffee with or without milk etc as specified
* can use the director to make an Espresso
* can use the director to make a Latte

