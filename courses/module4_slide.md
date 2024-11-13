# Module 4: Struct Methods and Interfaces

---

## Struct Methods in Go

- **Defining Methods**
  - **Methods vs. Functions**
    - Methods are functions with a special receiver argument.
    - They are associated with a specific type, typically a struct.
  - **Syntax**
    - Defined using the `func` keyword, with the receiver specified before the method name.
  - **Example**
    ```go
    type Book struct {
        Title  string
        Author string
    }

    func (b Book) GetTitle() string {
        return b.Title
    }
    ```

- **Pointer Receivers**
  - **Definition**
    - Methods can have pointer receivers to modify the struct's fields.
  - **Benefits**
    - Allows methods to change the struct's state.
    - Avoids copying the struct on each method call.
  - **Example**
    ```go
    func (b *Book) SetTitle(title string) {
        b.Title = title
    }
    ```

- **Value vs. Pointer Receivers**
  - **Value Receivers**
    - Used when the method does not modify the struct.
  - **Pointer Receivers**
    - Used when the method needs to modify the struct or for efficiency with large structs.
  - **Example**
    ```go
    func (b Book) PrintTitle() {
        fmt.Println(b.Title)
    }
    ```

---

## Interfaces in Go

- **Interface Basics**
  - **Definition**
    - An interface is a type that specifies a set of method signatures.
  - **Purpose**
    - Enables polymorphism by allowing different types to implement the same interface.
  - **Example**
    ```go
    type Printer interface {
        Print()
    }
    ```

- **Implementing Interfaces**
  - **Implicit Implementation**
    - A type implements an interface by defining all its methods.
    - No explicit declaration needed.
  - **Example**
    ```go
    type Book struct {
        Title string
    }

    type Printer interface {
        Print()
    }

    // Only with this line, Book implements Printer
    func (b Book) Print() {
        fmt.Println(b.Title)
    }
    ```

- **Using Interfaces**
  - **Polymorphism**
    - Interfaces allow functions to accept any type that implements the interface.
  - **Example**
    ```go
    func PrintDetails(p Printer) {
        p.Print()
    }
    ```

---

## Practical Applications

- **Struct Methods**
  - **Encapsulation**
    - Use methods to encapsulate behavior related to a struct.
  - **Example**
    ```go
    type Account struct {
        balance float64
    }

    func (a *Account) Deposit(amount float64) {
        a.balance += amount
    }
    ```

- **Interfaces**
  - **Decoupling**
    - Use interfaces to decouple code and improve testability.
  - **Example**
    ```go
    type Notifier interface {
        Notify(message string)
    }

    type EmailNotifier struct{}

    func (e EmailNotifier) Notify(message string) {
        fmt.Println("Sending email:", message)
    }
    ```

- **Design Patterns**
  - **Strategy Pattern**
    - Use interfaces to define interchangeable algorithms.
  - **Example**
    ```go
    type SortStrategy interface {
        Sort([]int)
    }
    ```

---

## Summary

- **Struct Methods**
  - Use methods to define behavior for structs.
  - Choose between value and pointer receivers based on the method's needs.

- **Interfaces**
  - Define interfaces to specify behavior without dictating implementation.
  - Implement interfaces implicitly by defining required methods.

- **Applications**
  - Use methods and interfaces to encapsulate behavior and achieve polymorphism.
  - Apply interfaces to design patterns for flexible and maintainable code.