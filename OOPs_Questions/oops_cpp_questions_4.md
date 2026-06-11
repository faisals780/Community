# C++ OOP + Data Structures Practice Questions — Set 4

> **C++ vs Java — Key Differences for Data Structures:**
> - `ArrayList` → `std::vector<T>` (include `<vector>`)
> - `Stack` → `std::stack<T>` (include `<stack>`) — LIFO — use `push()`, `pop()`, `top()`, `empty()`
> - `Queue` → `std::queue<T>` (include `<queue>`) — FIFO — use `push()`, `pop()`, `front()`, `empty()`
> - `LinkedList` → `std::list<T>` (include `<list>`) — maintains insertion order
> - `String` → `std::string` (include `<string>`)
> - `null` → `nullptr`
> - Looping through containers: `for (auto& item : container)` or traditional loop
> - Always add virtual destructors in abstract/parent classes
> - Use `std::to_string()` to convert numbers to strings

---

## Question 1 — Encapsulation + std::vector (Easy)

You are building a playlist manager for a music app.

- Create a class called `Playlist` with a private `std::string` for the playlist name and a private `std::vector<std::string>` that holds song names
- Add a constructor `Playlist(std::string playlistName)` using initializer list
- Add a method `addSong(std::string songName)` that adds a song using `push_back()`
- Add a method `removeSong(std::string songName)` that finds and removes a song — loop through the vector, find it, use `erase()` to remove it
- Add a method `getPlaylistName()` that returns the playlist name
- Add a method `getAllSongs()` that returns a `std::string` containing all songs separated by a comma — loop through the vector and concatenate
- In `main()`, create a `Playlist` object, add 3 songs, remove 1 song, and print all remaining songs

---

## Question 2 — Encapsulation + std::stack (Easy)

You are building a browser history manager.

- Create a class called `BrowserHistory` with a private `std::string` for the browser name and a private `std::stack<std::string>` for the history
- Add a constructor `BrowserHistory(std::string browserName)` using initializer list
- Add a method `visitPage(std::string url)` that pushes url to the stack using `push()`
- Add a method `goBack()` that removes and returns the last visited url using `pop()` and `top()` — if stack is empty, return `"No history found"` — remember: `pop()` removes but returns nothing, use `top()` before `pop()` to get the value
- Add a method `getBrowserName()` that returns the browser name
- Add a method `getHistorySize()` that returns the number of urls using `size()`
- In `main()`, create a `BrowserHistory` object, visit 3 pages, go back twice, and print the returned urls and history size after each `goBack()` call

---

## Question 3 — Inheritance + std::vector (Easy)

You are building a library management system.

- Create a parent class called `LibraryItem` with private `std::string itemId` and private `std::string title`, a constructor using initializer list, and getter methods `getItemId()` and `getTitle()` that return their values
- Add a `virtual` method `getItemInfo()` that returns a `std::string` containing item id and title
- Create two child classes — `Book` with an additional private `std::string author` and `Magazine` with an additional private `int issueNumber`
- Each child class must call the parent constructor in initializer list — `: LibraryItem(itemId, title)`
- Each child class must override `getItemInfo()` using `override` keyword — call `LibraryItem::getItemInfo()` and append its own info — method must return a `std::string`
- Add a `virtual` destructor `~LibraryItem() {}` in the parent class
- Create a class called `Library` with a private `std::string` library name and a private `std::vector<LibraryItem*>` that holds pointers to `LibraryItem` objects
- Add a constructor `Library(std::string libraryName)` using initializer list
- Add a method `addItem(LibraryItem* item)` that adds an item pointer using `push_back()`
- Add a method `getAllItems()` that returns all items
- In `main()`, create 2 `Book*` objects and 1 `Magazine*` object using `new`, add all to a `Library`, loop through using `getAllItems()` and print each item's info, then `delete` all pointers at the end

---

## Question 4 — Abstraction + std::queue (Medium)

You are building a customer support ticket system.

- Create an abstract class called `SupportTicket` with private `std::string ticketId`, private `std::string customerName`, and private `std::string issueDescription`, a constructor using initializer list that takes all three values, getter methods for all three that return their values, and a pure virtual method `getPriority()` that returns a `std::string`
- Add a non-abstract method `getTicketSummary()` that returns a `std::string` containing ticket id, customer name, issue description, and priority — it must call `getPriority()` internally
- Add a `virtual` destructor `~SupportTicket() {}` in the abstract class
- Create two concrete classes — `UrgentTicket` where `getPriority()` returns `"HIGH"` and `NormalTicket` where `getPriority()` returns `"LOW"`
- Each concrete class must call `super(ticketId, customerName, issueDescription)` in initializer list
- Create a class called `TicketQueue` with a private `std::queue<SupportTicket*>` that holds pointers to tickets
- Add a method `addTicket(SupportTicket* ticket)` that adds a ticket using `push()`
- Add a method `processNextTicket()` that removes and returns the next ticket — use `front()` to get and `pop()` to remove, return the pointer, if queue is empty return `nullptr`
- Add a method `getQueueSize()` that returns the number of tickets using `size()`
- In `main()`, create 2 `UrgentTicket*` and 2 `NormalTicket*` objects using `new`, add to queue, process them one by one, print each ticket's summary, and `delete` all pointers at the end

---

## Question 5 — Interface + std::list (Medium)

You are building a task management system.

- Create a pure abstract class called `Manageable` with pure virtual methods `getTaskId()` that returns `std::string`, `getStatus()` that returns `std::string`, and `updateStatus(std::string newStatus)` that returns `std::string`, and a `virtual` destructor
- Create a class called `Task` that inherits from `Manageable` with private `std::string taskId`, private `std::string taskName`, and private `std::string status`
- Add a constructor `Task(std::string taskId, std::string taskName)` using initializer list that sets id and name, and sets status to `"PENDING"` by default
- Implement all interface methods — `updateStatus()` should update the status and return `"Status updated to: " + newStatus`
- Create a class called `TaskManager` with a private `std::string` manager name and a private `std::list<Task*>` that holds `Task*` pointers
- Add a constructor `TaskManager(std::string managerName)` using initializer list
- Add a method `addTask(Task* task)` that adds a task using `push_back()`
- Add a method `getTaskById(std::string taskId)` that loops through the list using range-based for loop and returns the `Task*` with matching id — if not found return `nullptr`
- Add a method that loops through all tasks and returns a combined `std::string` of all task summaries
- In `main()`, create 3 `Task*` objects, add all to `TaskManager`, update the status of one task using `getTaskById()`, loop through all tasks and print their id, name, and status, then `delete` all pointers at the end

---

## Question 6 — Polymorphism + std::vector (Medium)

You are building a zoo animal feeding system.

- Create a parent class called `Animal` with private `std::string animalName`, private `std::string animalId`, and private `int age`
- Add a constructor `Animal(std::string animalId, std::string animalName, int age)` using initializer list and getter methods for all three
- Add a `virtual` method `getFeedingSchedule()` that returns `"Generic feeding schedule for " + animalName`
- Create three child classes — `Lion` with an additional private `std::string preyType`, `Elephant` with an additional private `int dailyFoodKg`, and `Parrot` with an additional private `std::string favoriteFruit`
- Each child class must call parent constructor in initializer list
- Each child class must override `getFeedingSchedule()` using `override` keyword — call `Animal::getFeedingSchedule()` and append its own specific feeding info
- Add a `virtual` destructor `~Animal() {}` in the parent class
- Create a class called `Zoo` with a private `std::string` zoo name and a private `std::vector<Animal*>` that holds pointers to `Animal` objects
- Add a constructor `Zoo(std::string zooName)` and an `addAnimal(Animal* animal)` method
- Add a method `getFeedingReport()` that loops through all animals and returns a combined `std::string` of all feeding schedules
- In `main()`, create one of each animal using `new`, add to zoo, print the full feeding report, and `delete` all pointers at the end

---

## Question 7 — Static + Composition + std::vector (Medium)

You are building an order management system for a restaurant.

- Create a class called `MenuItem` with private `std::string itemName`, private `double price`, and a static `int totalMenuItems` that increments in the constructor
- Add a constructor `MenuItem(std::string itemName, double price)` using initializer list
- Add getter methods that return values
- Add a static method `getTotalMenuItems()` that returns the count
- Initialize the static variable outside the class: `int MenuItem::totalMenuItems = 0;`
- Create a class called `Order` with private `std::string orderId`, private `std::string customerName`, and a private `std::vector<MenuItem*>` that holds `MenuItem*` pointers
- Add a constructor `Order(std::string orderId, std::string customerName)` using initializer list and a static `int totalOrders` that increments in the constructor
- Add a method `addItem(MenuItem* item)` that adds an item
- Add a method `getOrderTotal()` that loops through all items and returns the total price as a `double`
- Add a method `getOrderSummary()` that returns a `std::string` containing order id, customer name, and total price — it must call `getOrderTotal()` internally and use `std::to_string()` to convert to string
- Add a static method `getTotalOrders()` that returns total orders count
- Initialize static members outside the class
- In `main()`, create 3 `MenuItem*` objects, create 2 `Order` objects, add different items to each order, print summary for each order, and print total menu items and total orders, then `delete` all `MenuItem*` pointers at the end

---

## Question 8 — Abstract + Interface + std::stack (Medium-Hard)

You are building an undo-redo system for a text editor.

- Create a pure abstract class called `Executable` with pure virtual methods `execute()` that returns `std::string` and `undo()` that returns `std::string`, and a `virtual` destructor
- Create an abstract class called `TextCommand` that inherits from `Executable` with private `std::string commandName` and private `std::string targetText`, a constructor using initializer list that takes both values, getter methods that return their values, and a pure virtual method `getDescription()` that returns `std::string`
- Add a `virtual` destructor in `TextCommand`
- Create two concrete classes — `TypeCommand` with constructors and methods where `execute()` returns `"Typed: " + targetText` and `undo()` returns `"Removed: " + targetText`, and `DeleteCommand` where `execute()` returns `"Deleted: " + targetText` and `undo()` returns `"Restored: " + targetText`
- Each concrete class must implement `getDescription()` returning its own description
- Create a class called `TextEditor` with a private `std::string` editor name and two private `std::stack<Executable*>` — one for undo history and one for redo history
- Add a constructor `TextEditor(std::string editorName)`
- Add a method `executeCommand(TextCommand* cmd)` that executes the command by calling `execute()`, prints the result, and pushes it to the undo stack
- Add a method `undo()` that checks if undo stack is not empty, pops from undo stack using `top()` and `pop()`, calls `undo()` on the command, prints the result, and pushes the command to redo stack — if undo stack is empty, print `"Nothing to undo"`
- Add a method `redo()` that checks if redo stack is not empty, pops from redo stack, calls `execute()` on the command, prints the result, and pushes it back to undo stack — if redo stack is empty, print `"Nothing to redo"`
- In `main()`, create a `TextEditor*`, execute 3 commands using pointers, undo 2 times, redo 1 time, observe the output, and `delete` all pointers at the end

---

## Question 9 — Composition + std::list + Interface (Hard)

You are building a social media feed system.

- Create a pure abstract class called `Postable` with pure virtual methods `getPostId()` that returns `std::string`, `getContent()` that returns `std::string`, and `getLikes()` that returns `int`, and a `virtual` destructor
- Create a class called `Post` that inherits from `Postable` with private `std::string postId`, private `std::string content`, and private `int likes`
- Add a constructor `Post(std::string postId, std::string content)` using initializer list that sets id and content, and sets likes to `0`
- Add a method `addLike()` that increments likes by 1
- Implement all interface methods to return their values
- Add a `virtual` destructor `~Post() {}`
- Create a class called `UserProfile` with private `std::string userId`, private `std::string username`, and a private `std::list<Post*>` that holds `Post*` pointers
- Add a constructor `UserProfile(std::string userId, std::string username)` using initializer list
- Add getters for id and username that return values
- Add a method `createPost(std::string postId, std::string content)` that creates a new `Post*` using `new` and adds it to the list
- Add a method `getPostById(std::string postId)` that loops through the list and returns the `Post*` with matching id — return `nullptr` if not found
- Add a method `getAllPosts()` that returns the list of posts
- Create a class called `SocialFeed` with a private `std::vector<UserProfile*>` that holds `UserProfile*` pointers
- Add a method `addUser(UserProfile* user)` that adds a user
- Add a method `getUserById(std::string userId)` that returns a `UserProfile*` by id
- Add a method `getFeedSummary()` that loops through all users and all their posts and returns a combined `std::string` of all post contents and their likes using `std::to_string()` for likes
- In `main()`, create 2 `UserProfile*` objects, each with 2 posts, add likes to some posts, add both users to `SocialFeed*`, print the full feed summary, and `delete` all pointers at the end

---

## Question 10 — Putting It All Together (Hard)

You are building a mini hospital management system.

- Create an abstract class called `Person` with private `std::string personId`, private `std::string name`, and private `int age`, a constructor using initializer list that takes all three, getter methods that return values, and a pure virtual method `getRole()` that returns `std::string`, and a `virtual` destructor
- Create a pure abstract class called `Schedulable` with pure virtual methods `addAppointment(std::string appointment)` that returns `std::string` and `getAppointments()` that returns a `std::vector<std::string>`, and a `virtual` destructor
- Create a class called `Doctor` that inherits from `Person` and `Schedulable` with an additional private `std::string specialization` and a private `std::vector<std::string>` for appointments using multiple inheritance — `: public Person, public Schedulable`
- `getRole()` returns `"Doctor"`, `addAppointment()` adds to the vector and returns `"Appointment added: " + appointment`, `getAppointments()` returns the appointments vector
- Add a `virtual` destructor `~Doctor() {}`
- Create a class called `Patient` that inherits from `Person` with an additional private `std::string diagnosis` and a private `std::vector<std::string>` that holds medical history entries
- `getRole()` returns `"Patient"`, add a method `addMedicalHistory(std::string entry)` that adds to the vector, and `getMedicalHistory()` that returns the vector
- Add a `virtual` destructor `~Patient() {}`
- Create a class called `Appointment` with private `std::string appointmentId`, a private `Doctor*` pointer, a private `Patient*` pointer, and private `std::string date` — use composition for both Doctor and Patient
- Add a constructor that takes all four values using initializer list
- Add a method `getAppointmentDetails()` that returns a `std::string` containing appointment id, date, doctor name and specialization, and patient name and diagnosis
- Create a class called `Hospital` with private `std::string` hospital name, a private `std::vector<Doctor*>` for doctors, a private `std::vector<Patient*>` for patients, and a private `std::vector<Appointment*>` for appointments
- Add methods `addDoctor(Doctor* d)`, `addPatient(Patient* p)`, `addAppointment(Appointment* a)` that add to their respective vectors
- Add a method `getHospitalReport()` that returns a `std::string` with hospital name, all doctors' info, all patients' info, and all appointments' details
- In `main()`, create 2 `Doctor*` objects, 2 `Patient*` objects, 2 `Appointment*` objects, add appointments to doctors using `addAppointment()`, add everything to `Hospital*`, print the full hospital report, and `delete` all pointers at the end
