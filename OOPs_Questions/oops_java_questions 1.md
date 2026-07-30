# Java OOP Practice Questions

---

## Question 1 — Encapsulation

You work at a bank and need to digitize their account system.

- Create a class called `BankAccount` with private variables `String ownerName` and `double balance`
- The balance cannot be directly accessed or modified from outside the class
- Add a `deposit(double amount)` method that adds money to the balance
- Add a `withdraw(double amount)` method that deducts money, but if the withdrawal amount exceeds the balance, print a warning message
- Add a `getBalance()` method to view the current balance
- In the `main` method, create a `BankAccount` object, perform a few deposits and withdrawals, and print the balance at the end

---

## Question 2 — Inheritance

You are building a system for a vehicle rental company.

- Create a parent class called `Vehicle` with variables `String brand`, `int speed`, and a method `displayInfo()` that prints the brand and speed
- Create two child classes — `Car` with an additional variable `int numberOfDoors`, and `Bike` with an additional variable `boolean hasSidecar`
- Each child class should have its own `displayInfo()` method that first calls the parent's method and then prints its own additional info
- In the `main` method, create one `Car` object and one `Bike` object, and call `displayInfo()` on both

---

## Question 3 — Polymorphism

You are designing a notification system for an app.

- Create a parent class called `Notification` with a method `send()` that prints `"Sending a generic notification"`
- Create three child classes — `EmailNotification`, `SMSNotification`, and `PushNotification` — each overriding the `send()` method to print their own specific message
- In the `main` method, create an array of type `Notification` and store all three objects in it
- Loop through the array and call `send()` on each — observe how each object behaves differently

---

## Question 4 — Abstraction

You are building a payment processing system.

- Create an abstract class called `Payment` with an abstract method `processPayment(double amount)` and a non-abstract method `printReceipt()` that prints `"Receipt generated"`
- Create two concrete classes — `CreditCardPayment` and `UPIPayment` — each implementing `processPayment()` with their own logic
- In the `main` method, create objects of both classes and call both methods on each

---

## Question 5 — Interface

You are creating a smart home system.

- Create an interface called `SmartDevice` with methods `turnOn()` and `turnOff()`
- Create another interface called `VoiceControlled` with a method `respondToVoice(String command)`
- Create a class called `SmartSpeaker` that implements both interfaces
- In the `main` method, create a `SmartSpeaker` object and test all three methods

---

## Question 6 — Constructor Overloading

You are building a student registration system.

- Create a class called `Student` with variables `String name`, `int age`, and `String course`
- Add three constructors — one that takes only `name`, one that takes `name` and `age`, and one that takes all three values
- Each constructor should print a message like `"Student registered with name only"` or `"Student fully registered"` based on which constructor is used
- In the `main` method, create three `Student` objects using each constructor and observe the output

---

## Question 7 — Static Members

You are building a system to track how many employees have been hired at a company.

- Create a class called `Employee` with variables `String name`, `int id`, and a static variable `int totalEmployees` that keeps count
- Every time a new `Employee` object is created, `totalEmployees` should automatically increase
- Add a static method `getTotalEmployees()` that returns the count
- In the `main` method, create a few `Employee` objects and print the total count using the static method

---

## Question 8 — Method Overloading

You are creating a simple calculator class.

- Create a class called `Calculator` with an overloaded method `add()`
- The method should work with two integers, three integers, and two double values
- In the `main` method, call all three versions of `add()` and print the results

---

## Question 9 — Composition (Has-A Relationship)

You are building a system for a library.

- Create a class called `Author` with variables `String name` and `String nationality`
- Create a class called `Book` with variables `String title`, `int year`, and an object of type `Author` inside it (this is composition)
- Add a method `displayBookInfo()` in the `Book` class that prints the book's title, year, and the author's name and nationality
- In the `main` method, create an `Author` object, pass it into a `Book` object, and call `displayBookInfo()`

---

## Question 10 — Putting It All Together

You are designing a mini zoo management system using all OOP concepts.

- Create an abstract class called `Animal` with variables `String name`, `int age`, and an abstract method `makeSound()`
- Add a non-abstract method `displayInfo()` that prints the animal's name and age
- Create two child classes — `Lion` and `Parrot` — each overriding `makeSound()` with their own sound
- Create an interface called `Trainable` with a method `performTrick()`
- Make `Parrot` implement the `Trainable` interface
- In the `main` method, create a list of `Animal` objects containing both a `Lion` and a `Parrot`, loop through them calling `displayInfo()` and `makeSound()`, and separately call `performTrick()` on the `Parrot`
