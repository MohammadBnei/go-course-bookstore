# Module 3: Working with Data in Go

## Part 1: Theoretical Concepts

- **Go's Basic Data Structures**
  - **Arrays and Slices**
    - Arrays have a fixed size, while slices are dynamic and more commonly used.
    - Slices are built on top of arrays and provide flexibility in size.
    - Example: `var numbers = []int{1, 2, 3}`

  - **Maps**
    - Maps are collections of key-value pairs, similar to dictionaries.
    - Keys must be unique and of a comparable type.
    - Example: `var book = map[string]string{"Title": "Go Programming", "Author": "John Doe"}`

  - **Structs**
    - Structs are composite data types that group together variables under a single name.
    - Useful for representing complex data models.
    - Example: 
      ```go
      type Book struct {
          Title  string
          Author string
          Price  float64
      }
      ```

- **Managing Data in Go**
  - **JSON Encoding/Decoding**
    - Use the `encoding/json` package to work with JSON data.
    - `json.Marshal` encodes Go data structures into JSON.
    - `json.Unmarshal` decodes JSON into Go data structures.

  - **File I/O**
    - Use the `os` and `io/ioutil` packages for reading and writing files.
    - `ioutil.ReadFile` reads the entire content of a file into memory.
    - `ioutil.WriteFile` writes data to a file.

  - **Data Validation**
    - Validate data to ensure it meets certain criteria before processing.
    - Use custom validation functions or third-party libraries.

## Part 2: Project Tutorial

- **Define a Book Struct**
  - Create a `Book` struct to represent book data in the project.

  ```go
  type Book struct {
      Title  string
      Author string
      Price  float64
  }
  ```

- **Load Book Data from JSON**
  - Create a `books.json` file with sample book data.
  - Use `ioutil.ReadFile` and `json.Unmarshal` to load data into a slice of `Book`.

  ```json
  // books.json
  [
      {"Title": "The Go Programming Language", "Author": "Alan A. A. Donovan", "Price": 44.95},
      {"Title": "Go in Action", "Author": "William Kennedy", "Price": 39.99}
  ]
  ```

  ```go
  package main

  import (
      "encoding/json"
      "os"
      "log"
  )

  func loadBooks() ([]Book, error) {
      data, err := os.ReadFile("books.json")
      if err != nil {
          return nil, err
      }

      var books []Book
      err = json.Unmarshal(data, &books)
      if err != nil {
          return nil, err
      }

      return books, nil
  }
  ```

- **Display Book Data**
  - Use the `templ` components created in Module 2 to display the loaded book data.

  ```go
  func main() {
      books, err := loadBooks()
      if err != nil {
          log.Fatalf("Failed to load books: %v", err)
      }

      http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
          components.BookList(books).Render(w)
      })

      http.ListenAndServe(":8080", nil)
  }
  ```

## Part 3: Exercises

- **Exercise 1: Add a New Field to Book**
  - Add a `Genre` field to the `Book` struct.
  - Update the `books.json` file and the `Book` component to display the genre.

- **Exercise 2: Implement Data Validation**
  - Write a function to validate that the `Price` of a book is greater than zero.
  - Use this function when loading books from JSON.

- **Exercise 3: Save Book Data to JSON**
  - Implement a function to save the current list of books back to `books.json`.
  - Use `json.Marshal` and `ioutil.WriteFile` to achieve this.
