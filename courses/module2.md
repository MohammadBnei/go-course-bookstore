# Module 2: Templ HTML Tutorial

## Part 1: Theoretical Concepts

- **Templ Overview**
  - `templ` is a Go package for building HTML components using Go code.
  - It allows embedding Go expressions directly within HTML for dynamic content.
  - Supports server-side rendering without requiring JavaScript.

- **Templ Syntax for Conditionals and Loops**
  - Use `if`, `switch`, and `for` directly in templates for control flow.
  - `if` statements can conditionally render HTML based on boolean expressions.
  - `for` loops iterate over collections, such as slices or maps, to render repeated content.

- **Data Presentation with Templ**
  - Use `{}` to embed data expressions within HTML.
  - Data should be passed as `map[string]string` for simplicity.
  - Ensure data keys match the expected template variables.

## Part 2: Project Tutorial

- **Install Templ**
  - Run `go install github.com/a-h/templ/cmd/templ@latest` to install `templ`.
  - Ensure the `templ` binary is in your system's PATH.

- **Create Templ Components with Conditionals and Loops**
  - Define a `Book` component to display book details with conditional logic.
  - Create a `BookList` component to render a list of books using a loop.

  ```go
  // components/book.templ
  package main

  templ Book(data map[string]string) {
    <div class="book">
      <h2>{ data["Title"] }</h2>
      <p>Author: { data["Author"] }</p>
      if data["Price"] < "40" {
        <p>On Sale!</p>
      }
    </div>
  }

  // components/booklist.templ
  package main

  templ BookList(books []map[string]string) {
    <div class="book-list">
      for _, book := range books {
        @Book(book)
      }
    </div>
  }
  ```

- **Compile Templ Files**
  - Use the command `templ generate` to compile the `.templ` files into Go code.
  - This generates Go files that can be used in your project.

- **Integrate Templ with Go**
  - Render the compiled components in your Go web server.

  ```go
  package main

  import (
      "net/http"
      "github.com/yourusername/bookstore/components"
  )

  func main() {
      books := []map[string]string{
          {"Title": "The Go Programming Language", "Author": "Alan A. A. Donovan", "Price": "44.95"},
          {"Title": "Go in Action", "Author": "William Kennedy", "Price": "39.99"},
      }

      http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
          components.BookList(books).Render(w)
      })

      http.ListenAndServe(":8080", nil)
  }
  ```

## Part 3: Exercises

- **Exercise 1: Add a New Component**
  - Create a `Header` component that displays a navigation bar.
  - Integrate the `Header` component into the `BookList` component.

- **Exercise 2: Conditional Rendering**
  - Modify the `Book` component to display "Bestseller!" if the title contains "Go".
  - Use an `if` statement to implement this logic.

- **Exercise 3: Compile and Test**
  - Use `templ generate` to compile your components.
  - Run your Go server and verify the output in the browser.
