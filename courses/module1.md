# Module 1: Introduction and Setup

## Part 1: Theoretical Concepts

- **Go Language Overview**
  - Go is a statically typed, compiled language designed for simplicity and efficiency.
  - Developed by Google, it emphasizes concurrency, scalability, and ease of use.
  - Key features include garbage collection, strong typing, and a rich standard library.

- **Setting Up the Go Environment**
  - Install Go from the official website and set up the environment variables.
  - Use an IDE or text editor like VSCode, GoLand, or Sublime Text for development.
  - Understand the Go workspace structure: `GOPATH`, `GOROOT`, and module support.

- **Basic Go Program Structure**
  - A Go program consists of packages, with `main` being the entry point.
  - Use `package main` and `func main()` to define the executable program.
  - Import necessary packages using the `import` statement.

## Part 2: Project Tutorial

- **Initialize the Bookstore Project**
  - Create a new directory for the project: `mkdir bookstore && cd bookstore`.
  - Initialize a new Go module: `go mod init bookstore`.
  - Create a basic Go file: `touch main.go`.

- **Set Up a Basic Web Server**
  - Import the `net/http` package to handle HTTP requests.
  - Define a simple handler function to respond with "Welcome to Bookstore".
  - Start the server on a specified port using `http.ListenAndServe`.

  ```go
  package main

  import (
      "fmt"
      "net/http"
  )

  func main() {
      http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
          fmt.Fprintln(w, "Welcome to Bookstore")
      })
      http.ListenAndServe(":8080", nil)
  }
  ```

- **Run the Server**
  - Open a terminal and navigate to the project directory.
  - Run the server using `go run main.go`.
  - Open a web browser and visit `http://localhost:8080` to see the welcome message.

## Part 3: Exercises

- **Exercise 1: Modify the Welcome Message**
  - Change the welcome message to include your name, e.g., "Welcome to [Your Name]'s Bookstore".

- **Exercise 2: Add a New Route**
  - Create a new route `/about` that displays "About the Bookstore".

- **Exercise 3: Customize the Port**
  - Modify the server to listen on a different port, such as `9090`.

- **Exercise 4: Add a Health Check Endpoint**
  - Implement a `/health` endpoint that returns a simple "OK" message.
  - This endpoint will be used to check if the server is running.

- **Exercise 5: Basic Request Logging**
  - Add basic logging to print a message to the console each time a request is received.
  - Include the request method and URL path in the log message.
