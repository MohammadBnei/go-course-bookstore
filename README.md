# Go Bookstore Course

Welcome to the Go Bookstore Course! This course is designed to teach you the fundamentals of Go programming through a practical, hands-on approach. By the end of this course, you'll have built a fully functional Bookstore web application.

## Course Overview

The course is divided into several modules, each focusing on different aspects of Go programming:

1. **Module 1: Introduction and Setup**
   - Set up your Go development environment.
   - Create a basic web server.

2. **Module 2: Templ HTML Tutorial**
   - Use Templ to render dynamic HTML content.
   - Learn about conditionals and loops in templates.

3. **Module 3: Working with Data in Go**
   - Manage data using Go's data structures.
   - Parse JSON data and handle file I/O.

4. **Module 4: Functions and Modules**
   - Implement struct methods and interfaces.
   - Enhance the Bookstore project with advanced features.

## Getting Started

### Prerequisites

- **Go**: Install the latest version of Go from [golang.org](https://golang.org).
- **Templ**: Install Templ by running:
  ```bash
  go install github.com/a-h/templ/cmd/templ@latest
  ```

### Setting Up the Project

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/go-bookstore-course.git
   cd go-bookstore-course
   ```

2. **Initialize Go Modules**
   ```bash
   go mod tidy
   ```

3. **Run the Application**
   ```bash
   go run main.go
   ```

## Repository Structure

- **/modules**: Contains the course modules and related documentation.
  - **/module1**: Introduction and Setup
  - **/module2**: Templ HTML Tutorial
  - **/module3**: Working with Data in Go
  - **/module4**: Functions and Modules

- **/components**: Templ components for rendering HTML.
- **/templates**: HTML templates used in the project.
- **/data**: Sample data files (e.g., JSON files for book data).
- **main.go**: Entry point for the Bookstore application.

## Exercises

Each module includes exercises to reinforce the concepts covered. You can find the exercises in the respective module directories. Complete these exercises to enhance your understanding and build a more comprehensive Bookstore application.

## Contributing

Contributions are welcome! If you have suggestions or improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions or feedback, please contact [your email] or open an issue in the repository.

Happy coding!