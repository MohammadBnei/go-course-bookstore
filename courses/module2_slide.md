# Module 2: Templ HTML Tutorial

---

## Conditionals in Templ

---

- **If Statements**
  - Use `if` to conditionally render HTML based on a boolean expression.
  - Supports `else` and `elif` (else if) for additional conditions.
  - Example:
    ```go
    if condition {
      <p>Condition is true</p>
    } else {
      <p>Condition is false</p>
    }
    ```

---

- **Switch Statements**
  - Use `switch` for multiple conditional branches.
  - Simplifies complex `if-else` chains.
  - Example:
    ```go
    switch value {
    case "A":
      <p>Value is A</p>
    case "B":
      <p>Value is B</p>
    default:
      <p>Value is unknown</p>
    }
    ```

---

## Loops in Templ

---

- **For Loops**
  - Use `for` to iterate over a block of code multiple times.
  - Can iterate over slices, arrays, or maps.
  - Example:
    ```go
    for i := 0; i < 5; i++ {
      <p>Iteration { i }</p>
    }
    ```

---

- **For with Range**
  - Use `for range` to iterate over elements in a collection.
  - Provides index and value for each iteration.
  - Example:
    ```go
    for index, value := range collection {
      <p>Index: { index }, Value: { value }</p>
    }
    ```

---

## GOBIN and Go Install

---

- **GOBIN Environment Variable**
  - Specifies the directory where Go installs binaries.
  - Default is `$GOPATH/bin` if not set.

---

- **Using Go Install**
  - Installs Go binaries to the directory specified by `GOBIN`.
  - Command: `go install <package>@latest`
  - Example:
    ```bash
    go install github.com/a-h/templ/cmd/templ@latest
    ```

---

- **Checking GOBIN**
  - Verify `GOBIN` with `echo $GOBIN` (Unix) or `echo %GOBIN%` (Windows).

---

## Go Modules and Project Setup

---

- **Go Modules**
  - Manage dependencies and versions for Go projects.
  - Use `go mod init <module-name>` to create a new module.

---

- **Project Structure**
  - Organize code in a directory with a `go.mod` file.
  - Example:
    ```bash
    mkdir projectname
    cd projectname
    go mod init github.com/yourusername/projectname
    ```

---

- **Managing Dependencies**
  - Use `go get <package>` to add dependencies.
  - modules with name as github.com/yourusername/projectname, pushed to github, are available 
  - Track dependencies in `go.mod` and `go.sum`.

---

## Maps in Go

---

- **Definition**
  - Maps are key-value pairs, similar to dictionaries in other languages.
  - Syntax: `map[keyType]valueType`

---

- **Creating and Using Maps**
  - Initialize with `make(map[keyType]valueType)`.
  - Access values with `map[key]`.
  - Example:
    ```go
    book := map[string]string{
      "Title": "Go Programming",
      "Author": "John Doe",
    }
    <p>Title: { book["Title"] }</p>
    ```

---

- **Common Operations**
  - Add or update: `map[key] = value`
  - Delete: `delete(map, key)`
  - Check existence: `value, exists := map[key]`

---

## Summary

- **Templ Features**
  - Use conditionals and loops for dynamic HTML rendering.
  - Embed Go expressions directly in templates.

- **Go Environment**
  - Set up `GOBIN` for binary installations.
  - Use Go modules for dependency management.

- **Data Structures**
  - Utilize maps for flexible data representation.
  - Integrate maps with templ components for dynamic content.