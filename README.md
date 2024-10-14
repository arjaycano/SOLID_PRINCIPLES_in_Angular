![SOLID PRINCIPLES in Angular](https://github.com/user-attachments/assets/74737929-994c-47ea-87ee-b36741d8418a)
# Activity 25: SOLID PRINCIPLES in Angular
## SOLID Principles:
Are a set of guidelines for writing clean, maintainable, and reusable code.

1. S - Single Responsibility Principle (SRP):
Is a fundamental principle of software engineering which states that a class or module should have only one reason to change. In other words, it should have only one responsibility. Violating this principle can lead to code that is difficult to maintain and understand.

### Violation of SRP:
Consider a component that displays a list of products and allows the user to filter them by category. Here’s an example of what the code might look like:

![1](https://github.com/user-attachments/assets/7469b527-d7ef-474f-8346-eea1b8855339)

This component violates the SRP because it has two responsibilities: displaying the list of products and filtering them by category. This violates the “one reason to change” principle, as changes to the filtering behavior may affect the component’s rendering logic and vice versa.

To fix this violation, we can refactor the component into two separate components, each with its own responsibility.

### Fixing the Violation:
First, we’ll create a new component that displays the list of products:

![2](https://github.com/user-attachments/assets/54dd98f3-f3cb-40a6-b217-494194256d80)

This component is now responsible only for displaying the list of products. We’ve removed the category filtering logic to a new component.

Next, we’ll create a new component that handles the category filtering:

![3](https://github.com/user-attachments/assets/058a9624-9220-49a5-94a4-f2234264f19b)

This component is now responsible only for handling the category filtering. It updates the selected category and calls the getProductsByCategory() method of the ProductService to update the list of products.

Finally, we’ll update the app.component.html file to include both components:

![4](https://github.com/user-attachments/assets/2c5a5723-cdb9-4aa5-8c26-bc3a40a7cc61)
![4 1](https://github.com/user-attachments/assets/5d5bfcb5-1563-47b8-934a-76b13c9d7d1d)

The app-product-filter component emits a categorySelected event when a new category is selected. This event is handled by the app-product-list component, which calls its filterByCategory() method with the selected category.

By splitting the responsibilities into two separate components, we’ve successfully refactored our code to comply with the Single Responsibility Principle. Each component now has a single responsibility, making our code more modular and easier to maintain.

In addition to complying with the SRP, this refactoring also follows the Separation of Concerns principle, which advocates for dividing a software system into separate modules, each addressing a separate concern.

Adhering to the SRP is crucial for writing maintainable, extensible, and reusable code. By keeping each module’s responsibilities separated, we can avoid coupling and ensure that any changes to one module do not affect others unnecessarily.
