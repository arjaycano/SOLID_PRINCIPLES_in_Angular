![SOLID PRINCIPLES in Angular](https://github.com/user-attachments/assets/74737929-994c-47ea-87ee-b36741d8418a)
# Activity 25: SOLID PRINCIPLES in Angular
## SOLID Principles:
Are a set of guidelines for writing clean, maintainable, and reusable code.

1. S - Single Responsibility Principle (SRP)
is a fundamental principle of software engineering which states that a class or module should have only one reason to change. In other words, it should have only one responsibility. Violating this principle can lead to code that is difficult to maintain and understand.

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

2. Open/Closed Principle (OCP)
states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, we should be able to add new functionality without modifying existing code. This principle helps in reducing code coupling, improving code scalability, and making the code more reusable. OCP can be applied using inheritance and interfaces. For example, we can create a base component or service that contains common functionality and then create child components or services that inherit from the base component or service. We can also create interfaces for components or services that define a set of methods or properties that must be implemented.

### Violating the Open/Closed Principle:
Consider, we have a component that displays a list of users. The users are retrieved and displayed in a table. The table has three columns: name, email, and phone number. We have created a UserListComponent to display this list. Initially, the component looks like this:

![5](https://github.com/user-attachments/assets/d1d75844-c277-43b4-83fd-7631f91a48ab)

In the template file user-list.component.html, we have the following code:

![6](https://github.com/user-attachments/assets/79bc26f3-0efc-412f-aa6e-25c88f0f1f3b)

Everything works fine, and we can see the list of users displayed in a table with three columns.

Now, suppose we want to add a new feature to the application, which is to allow users to view additional details for each user. We want to display the user’s address, city, and state. We can simply modify the UserListComponent to add these columns to the table. Here’s how we can do it:

![7](https://github.com/user-attachments/assets/fdae54d9-fd74-4a11-bf79-44fc8044ad8c)
![8](https://github.com/user-attachments/assets/325e82bc-5d2d-4feb-ae68-60c9bb471980)

This code violates the OCP because we have modified the existing component to add new functionality. If we want to add more features to the application, we will have to keep modifying the UserListComponent, which makes it difficult to maintain and scale.

### Fixing the violation:
To fix the violation of the OCP, we need to separate the concerns of displaying the list of users and displaying the details of each user. We can create a new component called UserDetailComponent to display the additional details for each user. Here’s how we can do it:

![9](https://github.com/user-attachments/assets/4a1ae7db-70c5-4202-b2d4-7b3147f8d72a)

In the UserListComponent, we can now use the UserDetailComponent to display the additional details for each user. Here’s how we can do it:

![10](https://github.com/user-attachments/assets/d06fd202-5a6b-422d-869a-9f0fbd759a28)
![11](https://github.com/user-attachments/assets/c7648e30-e945-491a-8dcc-1d624246292c)
![11 1](https://github.com/user-attachments/assets/01dbd17d-ea9a-4150-b7f3-2be1c61897e2)

In this new implementation, the UserListComponent is responsible for displaying the list of users, while the UserDetailComponent is responsible for displaying the details of each user. The UserListComponent doesn’t need to be modified to add new functionality because the UserDetailComponent can be easily extended to display additional details.

3. Liskov Substitution Principle (LSP)
is a fundamental concept in software engineering that is essential for designing and implementing maintainable and extensible systems. LSP states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. Violating the LSP can lead to unexpected behavior and bugs.

### Violating LSP:

![12](https://github.com/user-attachments/assets/743655a9-8cee-4b25-bdb6-1cea8e154921)

In this example, Ostrich is a subclass of Animal that overrides the move() method to reflect the fact that ostriches cannot fly. However, when we pass an instance of Ostrich to the moveAnimal() function, we get unexpected behavior because the move() method of Ostrich does not behave the same way as the move() method of Animal. This violates the LSP because Ostrich is not a true substitute for Animal.

To fix the violation, we can modify the Ostrich class to behave more like Animal:

![13](https://github.com/user-attachments/assets/e09a5724-1e7c-4148-9ab9-39879f7ff222)

In this updated implementation, we have added a fly() method to the Ostrich class that throws an error because ostriches cannot fly. This ensures that Ostrich behaves like Animal and can be used as a substitute for it without affecting the correctness of the program.

The Liskov Substitution Principle is an important principle in software engineering that helps us design maintainable and extensible systems. Violating the LSP can lead to unexpected behavior and bugs, but these violations can be fixed by ensuring that subclasses behave like their superclasses.

4. Interface Segregation Principle (ISP)
is a software development principle that states that a software component should not be forced to depend on interfaces that it does not use. In other words, clients should not be forced to depend on methods they do not use. This principle helps to reduce coupling between components and makes code more modular, flexible, and maintainable. ISP can be violated when a component has a dependency on a service that provides more methods than the component needs. This can lead to unnecessary coupling between the component and the service, making it difficult to modify either component without affecting the other. Additionally, it can cause performance issues as the component may be forced to load unnecessary methods from the service. To demonstrate this, let’s consider an example where a component needs to retrieve data from a service. The service provides several methods, including ones that are not required by the component.

![14](https://github.com/user-attachments/assets/38a0c192-fbd3-4002-ae6c-edf094e376de)

The component only needs to retrieve items from the service, so it should only depend on the getItems method. However, if the component is written as follows:

![15](https://github.com/user-attachments/assets/0c067fc8-aab5-4a05-8eb2-4a2782e1bf0f)

The component is depending on the DataService interface, which includes methods that are not used by the component. This can lead to unnecessary coupling and performance issues.

To fix this, we can create a new interface that only includes the getItems method and have the service implement this interface. The component can then depend on this new interface instead of the original DataService interface.

![16](https://github.com/user-attachments/assets/40568025-414f-4942-8b35-3952000af57a)

Now, the component only depends on the ItemsService interface, which includes only the getItems method. This helps to reduce coupling and improves performance.

The Interface Segregation Principle (ISP) is an important software development principle that helps to reduce coupling between components and makes code more modular, flexible, and maintainable. Violating ISP can lead to unnecessary coupling and performance issues. To fix this, we can create new interfaces that include only the methods needed by a component and have services implement these interfaces instead of larger interfaces. This can help to improve code quality, reduce coupling, and improve performance.
