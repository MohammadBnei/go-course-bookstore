# Module 3: Working with Data in Go

---

## Go's Basic Data Structures

---

- **Arrays and Slices**
  - **Arrays**
    - Fixed size, defined at compile time.
    - Example: `var arr [3]int = [3]int{1, 2, 3}`
  - **Slices**
    - Dynamic size, more flexible than arrays.
    - Built on top of arrays.
    - Example: `var numbers = []int{1, 2, 3}`

---

- **Maps**
  - **Definition**
    - Collection of key-value pairs.
    - Keys must be unique and of a comparable type.
  - **Usage**
    - Initialize with `make(map[keyType]valueType)`.
    - Access values with `map[key]`.
  - **Example**
    ```go
    var book = map[string]string{"Title": "Go Programming", "Author": "John Doe"}
    ```

---

- **Structs**
  - **Definition**
    - Composite data type grouping variables under a single name.
    - Useful for representing complex data models.
  - **Example**
    ```go
    type Book struct {
        Title  string
        Author string
        Price  float64
    }
    ```

---

## Managing Data in Go

---

- **JSON Encoding/Decoding**
  - **Encoding**
    - Convert Go data structures to JSON using `json.Marshal`.
  - **Decoding**
    - Convert JSON to Go data structures using `json.Unmarshal`.
    - Requires a pointer to the data structure.
  - **Example**
    ```go
    var books []Book
    err := json.Unmarshal(data, &books)
    ```

---

- **File I/O**
  - **Reading Files**
    - Use `os.ReadFile` to read file content into memory.
  - **Writing Files**
    - Use `os.WriteFile` to write data to a file.
  - **Example**
    ```go
    data, err := os.ReadFile("books.json")
    ```

---

## Pointers in JSON Unmarshalling

---

- **Pointers Overview**
  - **Definition**
    - A pointer holds the memory address of a value.
  - **Usage in Unmarshalling**
    - `json.Unmarshal` requires a pointer to modify the original data structure.
  - **Example**
    ```go
    var books []Book
    err := json.Unmarshal(data, &books) // &books is a pointer to the slice
    ```

---

- **Why Use Pointers?**
  - **Modify Original Data**
    - Allows functions to modify the original data structure.
  - **Efficiency**
    - Avoids copying large data structures.
  - **Example**
    ```go
    func loadBooks(data []byte, books *[]Book) error {
        return json.Unmarshal(data, books)
    }
    ```

---

## Summary

- **Data Structures**
  - Arrays, slices, maps, and structs are fundamental in Go.
  - Use structs to model complex data.

- **Data Management**
  - JSON encoding/decoding for data interchange.
  - File I/O for persistent storage.

- **Pointers**
  - Passing variables through their memory addresses.
  - Enable direct data manipulation.
