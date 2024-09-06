# Introduction to Design Patterns: Brewing Better Code with Coffee Examples

Welcome to this hands-on tutorial on design patterns! In this series, we will demystify some of the most commonly used design patterns in software development through the engaging and familiar theme of coffee. 

## What Are Design Patterns?

Design patterns are reusable solutions to common problems in software design. They help you structure your code in a way that is both efficient and maintainable. By learning and applying design patterns, you can make your code more flexible, easier to understand, and simpler to manage.

## Why Coffee?

We’ll use coffee as a metaphor to explain each design pattern because it’s a relatable and fun way to visualize complex concepts. Each pattern will be illustrated through scenarios involving coffee-making, from brewing methods to customizing your drink. 

## Patterns Covered

1. **Singleton Pattern**: We will explore how to ensure that there is only one instance of a coffee factory responsible for brewing our drinks. This pattern helps manage resources efficiently by controlling access to a single instance.

2. **Decorator Pattern**: Learn how to dynamically add features such as milk, sugar, or an extra espresso shot to your coffee. This pattern allows you to enhance the functionality of objects at runtime without altering their structure.

3. **Visitor Pattern**: Discover how to apply operations like calculating discounts or prices to different types of coffee without modifying the coffee classes. This pattern helps you add new operations to existing object structures with minimal changes.

4. **Strategy Pattern**: Switch between different brewing strategies, such as using an espresso machine or a French press, to make the perfect cup of coffee. This pattern allows you to choose the appropriate algorithm at runtime based on the context.

5. **Builder Pattern**: Construct customized coffee orders step by step, ensuring that every cup is made just the way you like it. This pattern provides a flexible solution for creating complex objects with multiple configurations.

## How It Works

For each pattern, we will:
- Implement a practical example using coffee-related scenarios.
- Write unit tests to ensure the correct implementation and behavior.
- Provide detailed explanations to help you understand the pattern's purpose and application.

By the end of this tutorial, you’ll have a solid grasp of these design patterns and be able to apply them to your own projects with confidence.

Let’s get started and brew some better code!

## Coding & Unit Tests

Fork this repository into your GitHub profile.

* Create a `src` & `test` folder
* Setup TypeScript for your project
* Use `ts-mocha` to setup the unit tests using Mocha.

Work in this order:

* Next do the [Singleton Pattern](pattern-singleton.md)
* Start with the [Strategy Pattern](./pattern-strategy.md)
* Next will be the [Builder Pattern](pattern-builder.md)
* Then work on the [Decorator Pattern](pattern-decorator.md)
* Followed by the [Visitor Pattern](pattern-visitor.md)

Currently there are only 3 patterns in this repo for you to work on, 2 more will be added.
Once those are added get the instructions in your local repo by syncing your repo to the [upstream repo](https://stackoverflow.com/questions/52981111/how-can-i-merge-changes-from-an-upstream-branch-to-my-forks-branch).
