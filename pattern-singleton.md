# Singleton Pattern Tutorial: The Coffee Factory

## Introduction

In this tutorial, we’ll learn about the Singleton design pattern using the example of a coffee factory. The Singleton pattern ensures that a class has only one instance and provides a global point of access to that instance. This is useful for managing shared resources, like a coffee factory, where only one instance should handle all coffee production.

## Objective

You will implement a `CoffeeFactory` class as a singleton and write unit tests using Mocha with ts-mocha to verify its behavior.

## Step-by-Step Guide

### Step 1: Set Up the CoffeeFactory Class

1. **Create a new file `CoffeeFactory.ts` and define the Singleton class.**

   ```typescript
   // CoffeeFactory.ts
   class CoffeeFactory {
     private static instance: CoffeeFactory;

     // Private constructor to prevent instantiation
     private constructor() {}

     // Method to get the singleton instance
     public static getInstance(): CoffeeFactory {
       if (!CoffeeFactory.instance) {
         CoffeeFactory.instance = new CoffeeFactory();
       }
       return CoffeeFactory.instance;
     }

     // Example method to simulate brewing coffee
     public brewCoffee(type: string): string {
       return `Brewing a cup of ${type}`;
     }
   }

   export default CoffeeFactory;
