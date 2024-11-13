# Module 4: Project Tutorial

## Enhancing the Bookstore Project with Struct Methods and Interfaces

**Objective:** Implement struct methods and interfaces to manage book data and introduce a notification system.

### **Step 1: Define Struct Methods for Book Management**

- **Create a Book Struct with Methods**
  - Define a `Book` struct with fields for `Title`, `Author`, and `Price`.
  - Implement methods to encapsulate behavior related to books.

  ```go
  package main

  import "fmt"

  type Book struct {
      Title  string
      Author string
      Price  float64
  }

  // Method to display book details
  func (b Book) Display() {
      fmt.Printf("Title: %s, Author: %s, Price: $%.2f\n", b.Title, b.Author, b.Price)
  }

  // Method to apply a discount to the book price
  func (b *Book) ApplyDiscount(discount float64) {
      b.Price -= b.Price * discount / 100
  }
  ```

- **Use Struct Methods in the Application**
  - Create instances of `Book` and use the methods to display details and apply discounts.

```go
func main() {
    book := Book{"The Go Programming Language", "Alan A. A. Donovan", 44.95}
    book.Display()
    book.ApplyDiscount(10)
    book.Display()
}
```

### **Step 2: Implement Interfaces for Notifications**

- **Define a Notifier Interface**
  - Create an interface `Notifier` with a method `Notify`.

```go
type Notifier interface {
    Notify(message string)
}
```

- **Implement the Notifier Interface**
  - Create a `EmailNotifier` struct that implements the `Notifier` interface.

  ```go
  type EmailNotifier struct {
      Email string
  }

  func (e EmailNotifier) Notify(message string) {
      fmt.Printf("Sending email to %s: %s\n", e.Email, message)
  }
  ```

- **Use the Notifier Interface in the Application**
  - Implement a function that accepts a `Notifier` and sends a notification.

```go
func SendNotification(n Notifier, message string) {
    n.Notify(message)
}

func main() {
    emailNotifier := EmailNotifier{"user@example.com"}
    SendNotification(emailNotifier, "Your order has been shipped!")
}
```

### **Step 3: Integrate Methods and Interfaces into the Bookstore**

- **Enhance Bookstore Functionality**
  - Use struct methods to manage book data, such as applying discounts during sales.
  - Implement a notification system to inform users about new arrivals or promotions.

- **Example Integration**
  - Apply a discount to all books and notify users about the sale.

```go
func main() {
    books := []Book{
        {"The Go Programming Language", "Alan A. A. Donovan", 44.95},
        {"Go in Action", "William Kennedy", 39.99},
    }

    for i := range books {
        books[i].ApplyDiscount(10)
        books[i].Display()
    }

    emailNotifier := EmailNotifier{"user@example.com"}
    SendNotification(emailNotifier, "A 10% discount has been applied to all books!")
}
```

### Exercises

#### Exercise 1: Enhance Book Management

- **Objective:** Improve the `Book` struct with additional methods for better management.
- **Tasks:**
  1. Add a method `IsBestseller` that returns `true` if the book's sales exceed a certain threshold (e.g., 1000 copies).
  2. Implement a method `UpdateStock` that adjusts the stock level of a book.
  3. Test these methods by creating a few `Book` instances and simulating stock updates and bestseller checks.

#### Exercise 2: Implement a Notification System

- **Objective:** Develop a notification system to inform users about bookstore events.
- **Tasks:**
  1. Define a new struct `SMSNotifier` with a field for the phone number.
  2. Implement the `Notifier` interface for `SMSNotifier` with a `Notify` method that simulates sending an SMS.
  3. Use both `EmailNotifier` and `SMSNotifier` in the `SendNotification` function to notify users about a new book arrival.

#### Exercise 3: Apply Discounts with Interfaces

- **Objective:** Use interfaces to manage discounts across different book categories.
- **Tasks:**
  1. Define an interface `Discountable` with a method `ApplyDiscount`.
  2. Ensure the `Book` struct implements the `Discountable` interface.
  3. Create a function `ApplyCategoryDiscount` that takes a slice of `Discountable` items and applies a category-specific discount (e.g., 10% for fiction, 5% for non-fiction).

#### Exercise 4: Polymorphic Book Descriptions

- **Objective:** Use interfaces to provide detailed descriptions of books.
- **Tasks:**
  1. Define a new interface `Describable` with a method `Describe` that returns a string description.
  2. Implement the `Describable` interface for the `Book` struct, including details like title, author, and price.
  3. Create a function `PrintBookDescriptions` that takes a slice of `Describable` items and prints their descriptions, simulating a catalog display.

#### Exercise 5: Advanced Bookstore Features

- **Objective:** Implement advanced features to enhance the bookstore's functionality.
- **Tasks:**
  1. Add a method `ApplyBulkDiscount` to the `Book` struct that applies a discount based on the quantity purchased.
  2. Implement logic to apply a 5% discount for 5-10 books, 10% for 11-20 books, and 15% for more than 20 books.
  3. Simulate a bulk purchase scenario and test the discount application.
