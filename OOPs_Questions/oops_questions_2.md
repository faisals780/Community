# Java OOP Practice Questions — Set 2 (Level Up)

---

## Question 1 — Encapsulation + Getters/Setters
*(Focus: return values from getters, not void)*

You are building a profile system for an e-commerce app.

- Create a class called `UserProfile` with private variables `String username`, `String email`, and `int age`
- Add a constructor that takes all three values
- Add proper getter methods — `getUsername()`, `getEmail()`, `getAge()` — each must **return** the value, not print it
- Add a setter `setEmail(String email)` that updates the email, but only if the new email contains `"@"` — otherwise print `"Invalid email"`
- In the `main` method, create a `UserProfile` object, print all details using getters, try setting a valid and an invalid email, and print the email again after each attempt

---

## Question 2 — Inheritance + super()
*(Focus: correct use of super(), no empty constructors, primitive types)*

You are building a system for a sports club.

- Create a parent class called `Player` with variables `String playerName`, `int jerseyNumber`, and a method `displayInfo()` that returns a `String` containing the player's name and jersey number
- Create two child classes — `Footballer` with an additional variable `String position`, and `Cricketer` with an additional variable `boolean isWicketKeeper` (use primitive `boolean`, not `Boolean`)
- Each child class must use `super(playerName, jerseyNumber)` in its constructor
- Each child class must override `displayInfo()` — call `super.displayInfo()` and append its own info
- In the `main` method, create one `Footballer` and one `Cricketer` object, and print their info

---

## Question 3 — Polymorphism + Runtime behavior
*(Focus: meaningful method logic, not empty overrides)*

You are designing a payment gateway that supports multiple payment methods.

- Create a parent class called `PaymentMethod` with a method `pay(double amount)` that prints `"Processing generic payment of Rs." + amount`
- Create three child classes — `CreditCard`, `UPI`, and `NetBanking` — each overriding `pay()` with their own specific message and a 2% convenience fee calculation for `CreditCard` only
- In the `main` method, create an array of type `PaymentMethod` containing all three objects, loop through the array calling `pay(5000)` on each

---

## Question 4 — Abstraction + Spelling discipline
*(Focus: correct spellings, return types, no redundant code)*

You are building a document editor that supports multiple file formats.

- Create an abstract class called `Document` with variables `String fileName` and `int pageCount`, an abstract method `export()` that returns a `String`, and a non-abstract method `getSummary()` that returns a `String` containing the file name and page count
- Create two concrete classes — `PDFDocument` and `WordDocument` — each implementing `export()` returning their own specific export message
- In the `main` method, create objects of both classes, print `getSummary()` and `export()` for each — all printing must happen in `main`, not inside the methods

---

## Question 5 — Interfaces + using parameters
*(Focus: actually using method parameters, no redundant public keyword)*

You are designing a system for a music streaming app.

- Create an interface called `Playable` with methods `play(String songName)` and `pause()`
- Create another interface called `Downloadable` with a method `download(String songName, String quality)`
- Create a class called `MusicPlayer` that implements both interfaces
- `play()` should print the song name being played, `pause()` should print a pause message, `download()` should print the song name and quality being downloaded
- In the `main` method, create a `MusicPlayer` object and test all three methods with actual values

---

## Question 6 — Constructor Overloading + validation
*(Focus: meaningful constructors with logic, not just print statements)*

You are building an order management system for a restaurant.

- Create a class called `Order` with variables `String itemName`, `int quantity`, and `double price`
- Add three constructors — one that takes only `itemName` and sets quantity to `1` and price to `0.0`, one that takes `itemName` and `quantity`, and one that takes all three
- Each constructor must print a different message describing what was set
- Add a method `getOrderTotal()` that **returns** `quantity * price`
- In the `main` method, create three `Order` objects using each constructor, and print the total for each using `getOrderTotal()`

---

## Question 7 — Static Members + correct counter logic
*(Focus: counter increments in constructor, not in getter)*

You are building a ticket booking system for a cinema.

- Create a class called `Ticket` with variables `String movieName`, `String seatNumber`, and a static variable `int totalTicketsBooked`
- Every time a new `Ticket` object is created via the constructor, `totalTicketsBooked` must automatically increase — **not** inside the getter
- Add a static method `getTotalTicketsBooked()` that only **returns** the count
- Add a non-static method `getTicketInfo()` that **returns** a `String` with the movie name and seat number
- In the `main` method, book 4 tickets, print each ticket's info using `getTicketInfo()`, and print the total count using the static method

---

## Question 8 — Method Overloading + return types
*(Focus: correct return types, meaningful logic in each overload)*

You are building a utility class for a geometry app.

- Create a class called `ShapeCalculator` with an overloaded method `calculateArea()`
- The method should work for three shapes — a circle that takes `double radius` and returns area as `double`, a rectangle that takes `int length` and `int width` and returns area as `int`, and a triangle that takes `double base` and `double height` and returns area as `double`
- Use `Math.PI` for circle area calculation
- In the `main` method, call all three versions and print the results with proper labels

---

## Question 9 — Composition (Has-A)
*(Focus: composition not inheritance, proper object inside object)*

You are building a system for a hospital.

- Create a class called `Doctor` with variables `String doctorName` and `String specialization`, and a method `getDoctorInfo()` that **returns** a `String` with both values
- Create a class called `Appointment` with variables `String patientName`, `String date`, and a `Doctor` object inside it — **do not use `extends`**
- Add a constructor that takes `patientName`, `date`, and a `Doctor` object
- Add a method `getAppointmentDetails()` that **returns** a `String` containing patient name, date, and doctor info by calling `getDoctorInfo()`
- In the `main` method, create a `Doctor` object, pass it into an `Appointment` object, and print the appointment details

---

## Question 10 — Putting It All Together
*(Focus: combining all concepts cleanly — abstract class, interface, composition, static, polymorphism)*

You are building a mini employee management system for a company.

- Create an abstract class called `Staff` with private variables `String staffName` and `int staffId`, a static variable `int totalStaff` that increments in the constructor, a getter `getStaffName()` that returns the name, a getter `getStaffId()` that returns the id, a static method `getTotalStaff()` that returns the count, and an abstract method `getRole()` that returns a `String`
- Create an interface called `Payable` with a method `calculateSalary()` that returns a `double`
- Create a class called `Department` with variables `String departmentName` and a `Staff` object inside it — use composition, not inheritance
- Create two concrete classes — `Manager` and `Intern` — both extending `Staff` and implementing `Payable`
- `Manager` has an additional variable `double baseSalary` and `calculateSalary()` returns `baseSalary * 1.3`
- `Intern` has an additional variable `double stipend` and `calculateSalary()` returns `stipend`
- In the `main` method, create a `Manager` and an `Intern`, assign each to a `Department` using composition, print their names, roles, salaries, and the total staff count
