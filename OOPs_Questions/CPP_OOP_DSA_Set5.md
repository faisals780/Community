# C++ OOP + Data Structures Practice Questions — Set 5

> **Language:** C++ only  
> **STL Headers you will need:** `<vector>`, `<stack>`, `<queue>`, `<list>`, `<set>`, `<unordered_set>`, `<string>`, `<sstream>`  
> **Key C++ Notes:**
> - Use `std::string` instead of Java's `String`
> - Use `std::vector` instead of `ArrayList`
> - Use `std::stack` instead of Java's `Stack`
> - Use `std::queue` instead of Java's `Queue`
> - Use `std::list` instead of Java's `LinkedList`
> - Use `std::unordered_set` instead of Java's `HashSet`
> - Use `std::vector` (thread-safe alternative) instead of Java's `Vector`
> - Use `std::ostringstream` instead of Java's `StringBuilder`
> - Use pure `virtual` methods instead of Java's `abstract` methods
> - Use `virtual` destructor in every base class
> - Interfaces are simulated using abstract classes with all pure virtual methods
> - Use `nullptr` instead of Java's `null`
> - Use `override` keyword when overriding virtual methods

---

## Question 1 — Encapsulation + ostringstream + vector (Easy)

You are building a **note-taking app**.

- Create a class called `Note` with a private `std::string` noteId, a private `std::string` title, and a private `std::ostringstream` for the note content
- Add a constructor that takes `noteId` and `title` only — content should start empty
- Add a method `appendContent(std::string text)` that adds text to the existing content — do not replace, only append to it
- Add a method `clearContent()` that resets the content to empty — think about how to clear an `ostringstream`
- Add a method `getContent()` that returns the current content as a `std::string`
- Add getter methods for `noteId` and `title`
- Create a class called `NoteBook` with a private `std::string` ownerName and a private `std::vector` that holds multiple `Note` objects
- Add a constructor that takes `ownerName`
- Add a method `addNote(Note note)` that adds a note to the vector
- Add a method `getNoteById(std::string noteId)` that loops through the vector and returns a pointer to the matching `Note` — return `nullptr` if not found
- Add a method `getAllNotes()` that returns a reference to the vector
- In `main`, create a `NoteBook`, add 3 `Note` objects, append content to each note at least twice, find one note by id using `getNoteById()`, clear its content, append something new to it, then print all notes' title and content

---

## Question 2 — Encapsulation + stack + ostringstream (Easy)

You are building a **code editor with an undo feature**.

- Create a class called `CodeEditor` with a private `std::string` fileName, a private `std::ostringstream` for current code content, and a private `std::stack` that stores `std::string` snapshots of previous states
- Add a constructor that takes only `fileName` — content starts empty
- Add a method `typeCode(std::string code)` that first saves the current content as a snapshot into the stack, then appends the new code to content
- Add a method `undo()` that restores the last saved snapshot from the stack and sets it as the current content — if stack is empty return `"Nothing to undo"` — think about how to reset an `ostringstream` and write a new string into it
- Add a method `getCurrentCode()` that returns current content as a `std::string`
- Add a getter for `fileName`
- In `main`, create a `CodeEditor`, type code 3 times, call `undo()` twice, and print the current code after each undo — observe how content rolls back

---

## Question 3 — Inheritance + vector + ostringstream (Medium)

You are building a **vehicle rental system**.

- Create a parent class called `Vehicle` with private `std::string` vehicleId, private `std::string` brand, and private `int` year
- Add a constructor that takes all three values, getter methods for all, and a `virtual` method `getVehicleInfo()` that returns a `std::string` containing vehicleId, brand, and year
- Add a `virtual` destructor to `Vehicle`
- Create two child classes — `Car` with an additional private `int` numberOfDoors and `Bike` with an additional private `std::string` bikeType
- Each child class must call the parent constructor using initializer list syntax
- Each child class must override `getVehicleInfo()` using the `override` keyword — call the parent version and append its own specific info
- Create a class called `RentalAgency` with a private `std::string` agencyName and a private `std::vector` that holds `Vehicle*` pointers — use pointers so polymorphism works correctly
- Add a constructor, an `addVehicle(Vehicle* v)` method, and a method `getRentalCatalog()` that uses `std::ostringstream` to build and return a combined `std::string` of all vehicles' info
- In `main`, create 2 `Car` objects and 2 `Bike` objects using `new`, add all to `RentalAgency`, print the full rental catalog, and delete all allocated objects at the end

---

## Question 4 — Abstract class + queue + list (Medium)

You are building a **food delivery order system**.

- Create an abstract class called `DeliveryOrder` with private `std::string` orderId, private `std::string` customerAddress, and private `double` totalAmount
- Add a constructor that takes all three values, getter methods for all, and a pure virtual method `getDeliveryType()` that returns a `std::string`
- Add a `virtual` destructor
- Add a non-pure virtual method `getOrderSummary()` that returns a `std::string` containing orderId, customerAddress, totalAmount, and delivery type — it must call `getDeliveryType()` internally
- Create two concrete classes — `ExpressDelivery` where `getDeliveryType()` returns `"EXPRESS"` and `StandardDelivery` where `getDeliveryType()` returns `"STANDARD"`
- Each concrete class must call the parent constructor using initializer list syntax
- Create a class called `DeliveryQueue` with a private `std::queue` that holds `DeliveryOrder*` pointers
- Add a method `placeOrder(DeliveryOrder* order)` that adds an order to the queue
- Add a method `dispatchNext()` that removes and returns the next order pointer — return `nullptr` if queue is empty
- Add a method `getPendingCount()` that returns the number of orders waiting as an `int`
- In `main`, add 2 `ExpressDelivery` and 2 `StandardDelivery` orders using `new`, dispatch them one by one, print each order's summary and remaining pending count after each dispatch, and delete all objects at the end

---

## Question 5 — Abstract class as Interface + unordered_set + vector (Medium)

You are building a **student course enrollment system**.

- Create an abstract class called `Enrollable` that acts as an interface — it should have pure virtual methods `getStudentId()` that returns a `std::string`, `enroll(std::string courseCode)` that returns a `std::string` message, and `getEnrolledCourses()` that returns a `const std::unordered_set<std::string>&`
- Add a virtual destructor to `Enrollable`
- Create a class called `Student` that inherits from `Enrollable` with private `std::string` studentId, private `std::string` studentName, and a private `std::unordered_set<std::string>` that holds enrolled course codes — use `unordered_set` so duplicate course enrollments are automatically prevented
- Add a constructor `Student(std::string studentId, std::string studentName)`
- Implement all methods — `enroll()` should add the course to the set and return `"Enrolled in: " + courseCode` if added, or `"Already enrolled in: " + courseCode` if it was already present — think about what `unordered_set::insert()` returns
- Add a getter for `studentName`
- Create a class called `CourseRegistry` with a private `std::string` registryName and a private `std::vector` that holds `Student*` pointers
- Add a method `registerStudent(Student* s)` that adds a student
- Add a method `getStudentById(std::string studentId)` that returns matching `Student*` — return `nullptr` if not found
- Add a method `getAllStudents()` that returns a reference to the vector
- In `main`, create 3 students using `new`, try enrolling the same course twice for one student, add all to `CourseRegistry`, print each student's name and enrolled courses, and delete all objects at the end

---

## Question 6 — Polymorphism + vector + ostringstream (Medium)

You are building an **employee payroll system**.

- Create a parent class called `Employee` with private `std::string` employeeId, private `std::string` employeeName, and private `double` baseSalary
- Add a constructor, getter methods, and a `virtual` method `getPayDetails()` that returns `"Base salary for " + employeeName + ": " + std::to_string(baseSalary)`
- Add a `virtual` destructor
- Create three child classes — `FullTimeEmployee` with an additional private `double` bonus, `PartTimeEmployee` with an additional private `int` hoursWorked and private `double` hourlyRate, and `Contractor` with an additional private `double` contractAmount
- Each child class must call the parent constructor using initializer list syntax
- Each child class must override `getPayDetails()` using `override` — call the parent version and append its own pay breakdown info
- Create a class called `PayrollSystem` with a private `std::string` companyName and a private `std::vector` that holds `Employee*` pointers — use `vector` here (C++ equivalent of Java's Vector is also `std::vector`, just use it with a comment)
- Add a constructor, an `addEmployee(Employee* e)` method, and a method `generatePayrollReport()` that uses `std::ostringstream` to build and return a report of all employees' pay details
- In `main`, create one of each employee type using `new`, add to `PayrollSystem`, print the full payroll report, and delete all objects at the end

---

## Question 7 — Multiple Inheritance + unordered_set + list (Hard)

You are building a **university department management system**.

- Create an abstract class called `Trackable` that acts as an interface with pure virtual methods `getId()` that returns a `std::string` and `getSummary()` that returns a `std::string` — add a virtual destructor
- Create an abstract class called `UniversityMember` with private `std::string` memberId and private `std::string` memberName, a constructor that takes both, getter methods, and a pure virtual method `getRole()` that returns a `std::string` — add a virtual destructor
- Create a class called `Professor` that inherits from both `UniversityMember` and `Trackable` — use multiple inheritance — with an additional private `std::string` subject and a private `std::unordered_set<std::string>` that holds research topics
- `getRole()` returns `"Professor"`, `getId()` returns memberId, `getSummary()` returns a combined `std::string` of name, subject, and all research topics
- Add a method `addResearchTopic(std::string topic)` — since it is an `unordered_set`, duplicate topics are ignored automatically
- Create a class called `GradStudent` that inherits from both `UniversityMember` and `Trackable` with an additional private `std::string` thesisTopic and a private `std::string` supervisorId
- `getRole()` returns `"Graduate Student"`, `getId()` returns memberId, `getSummary()` returns name, thesis topic, and supervisor id
- Create a class called `Department` with a private `std::string` departmentName, a private `std::list` of `Professor*` pointers, and a private `std::list` of `GradStudent*` pointers
- Add methods `addProfessor(Professor* p)`, `addGradStudent(GradStudent* g)`, and a method `getDepartmentReport()` that uses `std::ostringstream` to build and return a full report using each member's `getSummary()` method
- In `main`, create 2 professors using `new` with multiple research topics (include duplicates to show unordered_set filtering), create 2 grad students, add all to a `Department`, print the full department report, and delete all objects at the end

---

## Question 8 — Static members + Composition + queue + ostringstream (Hard)

You are building an **airport check-in system**.

- Create a class called `Passenger` with private `std::string` passengerId, private `std::string` passengerName, private `std::string` destination, and a `static int` totalPassengers that increments in the constructor
- Add a constructor, getter methods, and a `static` method `getTotalPassengers()` that returns the count
- Create a class called `Flight` with private `std::string` flightId, private `std::string` origin, private `std::string` destination, and a `static int` totalFlights that increments in the constructor
- Add a constructor, getter methods, a `static` method `getTotalFlights()`, and a method `getFlightInfo()` that returns a `std::string` with flightId, origin, and destination
- Create a class called `CheckInCounter` with a private `std::string` counterCode, a `Flight` object stored by value — use composition, and a private `std::queue` that holds `Passenger*` pointers
- Add a constructor `CheckInCounter(std::string counterCode, Flight flight)`
- Add a method `joinQueue(Passenger* p)` that adds passenger to the queue
- Add a method `checkInNext()` that removes and returns the next passenger pointer — if queue is empty return `nullptr`
- Add a method `getQueueLength()` that returns remaining passengers as `int`
- Create a class called `Airport` with a private `std::string` airportName and a private `std::vector` of `CheckInCounter` objects stored by value
- Add a method `addCounter(CheckInCounter c)` and a method `getAirportStatus()` that uses `std::ostringstream` to return airport name and each counter's code, flight info, and queue length
- In `main`, create 2 flights, 2 check-in counters, add 3 passengers to each counter using `new`, check in 2 passengers from one counter, print the full airport status and static counts, and delete all passenger objects at the end

---

## Question 9 — Multiple Inheritance + list + unordered_set (Hard)

You are building a **company org chart system**.

- Create an abstract class called `Reportable` that acts as an interface with pure virtual methods `getEmployeeId()` that returns a `std::string` and `getReport()` that returns a `std::string` — add a virtual destructor
- Create an abstract class called `OrgMember` with private `std::string` memberId, private `std::string` memberName, and private `std::string` department, a constructor that takes all three, getter methods, and a pure virtual method `getDesignation()` that returns a `std::string` — add a virtual destructor
- Create a class called `Manager` that inherits from both `OrgMember` and `Reportable` with an additional private `std::string` teamName and a private `std::list<std::string>` that holds directReportIds
- `getDesignation()` returns `"Manager"`, `getEmployeeId()` returns memberId, `getReport()` returns name, team name, department, and all direct report ids
- Add a method `addDirectReport(std::string employeeId)` that adds to the list
- Create a class called `IndividualContributor` that inherits from both `OrgMember` and `Reportable` with an additional private `std::string` skillSet and a private `std::unordered_set<std::string>` that holds certifications — duplicate certifications are ignored automatically
- `getDesignation()` returns `"IC"`, `getEmployeeId()` returns memberId, `getReport()` returns name, skillset, department, and all certifications
- Add a method `addCertification(std::string cert)` that adds to the set
- Create a class called `OrgChart` with a private `std::string` companyName, a private `std::vector` of `Manager*` pointers, and a private `std::vector` of `IndividualContributor*` pointers
- Add methods `addManager(Manager* m)`, `addIC(IndividualContributor* ic)`, and `getOrgReport()` that uses `std::ostringstream` to build and return a complete org chart report
- In `main`, create 2 managers with direct reports, create 3 ICs with certifications using `new` (include duplicate certifications to show unordered_set filtering), add all to `OrgChart`, print the full org report, and delete all objects at the end

---

## Question 10 — Putting It All Together (Hard)

You are building a **mini e-commerce platform**.

- Create an abstract class called `User` with private `std::string` userId, private `std::string` email, and private `int` age, a constructor that takes all three, getter methods, a pure virtual method `getUserType()` that returns a `std::string`, and a virtual destructor
- Create an abstract class called `Transactable` that acts as an interface with pure virtual methods `addTransaction(std::string txnId)` that returns a `std::string` and `getTransactions()` that returns a `const std::vector<std::string>&` — add a virtual destructor
- Create a class called `Buyer` that inherits from both `User` and `Transactable` with an additional private `std::string` shippingAddress and a private `std::vector<std::string>` for transactions
- `getUserType()` returns `"Buyer"`, `addTransaction()` adds to vector and returns `"Transaction recorded: " + txnId`, `getTransactions()` returns the vector
- Add a getter for `shippingAddress`
- Create a class called `Seller` that inherits from `User` with an additional private `std::string` storeName and a private `std::unordered_set<std::string>` that holds product categories — duplicate categories are ignored
- `getUserType()` returns `"Seller"`
- Add a method `addCategory(std::string category)` and a method `getCategories()` that returns a const reference to the set
- Create a class called `Product` with private `std::string` productId, private `std::string` productName, private `double` price, and a `Seller*` pointer — use composition via pointer
- Add a constructor, getter methods, and a method `getProductDetails()` that returns productId, productName, price, and seller's store name
- Create a class called `Order` with private `std::string` orderId, a `Buyer*` pointer, a private `std::list` of `Product*` pointers, and a private `std::string` status — use composition via pointer for Buyer
- Add a constructor `Order(std::string orderId, Buyer* buyer)` that sets status to `"PENDING"` by default
- Add a method `addProduct(Product* p)` that adds to the list
- Add a method `getOrderTotal()` that loops and returns total price as `double`
- Add a method `updateStatus(std::string status)` that updates status
- Add a method `getOrderDetails()` that uses `std::ostringstream` to return orderId, buyer name, status, all product names, and total amount
- Create a class called `Platform` with private `std::string` platformName, a private `std::vector` of `Buyer*` pointers, a private `std::vector` of `Seller*` pointers, and a private `std::vector` of `Order*` pointers
- Add methods `addBuyer(Buyer* b)`, `addSeller(Seller* s)`, `addOrder(Order* o)`
- Add a method `getPlatformReport()` that uses `std::ostringstream` to return platform name, all buyers with their transactions, all sellers with their categories, and all orders with their details
- In `main`, create 2 sellers with product categories using `new` (include duplicates), create 3 products assigned to sellers, create 2 buyers, create 2 orders with multiple products, add transactions to buyers, update one order status, add everything to `Platform`, print the full platform report, and delete all heap-allocated objects at the end

---
