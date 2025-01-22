
# Case Study: Simple Spring Boot Web Application

This project demonstrates a simple Spring Boot web application. It includes basic functionality to handle HTTP requests and display dynamic content on web pages. This case study provides a detailed explanation of the implementation, purpose, and use cases of the provided code and screens.

---


## Project Overview

This Spring Boot application:
- Maps HTTP requests using a `HelloController` class.
- Passes dynamic data to Thymeleaf templates for rendering.
- Demonstrates how to structure a simple web application.

The project is ideal for beginners exploring Spring Boot and Thymeleaf integration.

---

## File Descriptions

### HelloController.java

This controller contains two endpoints:

- **`/`**: A simple endpoint that returns the string `hello vistula perzyna`.
- **`/greeting`**: An endpoint that accepts a `name` parameter, adds it to the model, and returns the `greeting.html` view.

```java
@GetMapping(value = "/")
public String hello() {
    return "hello vistula perzyna";
}

@GetMapping("/greeting")
public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
    model.addAttribute("name", name);
    return "greeting";
}
```

### greeting.html

A Thymeleaf template that dynamically renders a greeting message using the `name` attribute passed from the controller.

Key elements:
- Displays the greeting message.
- Includes a placeholder image with the path `/images/vistula.png`.

```html
<p th:text="'Hello, ' + ${name} + '!'" />
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc ac risus vitae dui aliquet</p>
<img th:src="@{/images/vistula.png}" alt="logo vistula" width="600" height="600" />
```

## Implementation Details

1. **Controller Layer**
   - The `HelloController` class uses the `@Controller` annotation to define a Spring MVC controller.
   - `@GetMapping` is used to map HTTP GET requests to specific methods.

2. **Dynamic Parameters**
   - The `/greeting` endpoint uses `@RequestParam` to retrieve the `name` parameter from the request and adds it to the `Model`.

3. **Thymeleaf Integration**
   - The `Model` object passes the `name` parameter to the Thymeleaf template.
   - The template dynamically renders content using the `${name}` variable.

---

## Use Case Scenario

### Scenario:
A small university, "Vistula," wants a lightweight web application to demonstrate personalized greetings for visitors and showcase static resources like images or banners.

### Steps:
1. The user visits `/greeting` and provides their name as a query parameter (e.g., `/greeting?name=Kamil`).
2. The server dynamically generates a greeting message, which is rendered in the browser.
3. Static resources, such as the "Vistula" logo, are also displayed on the page.

### Outcome:
The application dynamically adjusts the greeting and provides a visually appealing template for potential further customization.

---


## Running the Application

### Prerequisites
- Java 8+ installed.
- Maven installed (or Gradle as an alternative).
- An IDE like IntelliJ IDEA or Eclipse.

### Steps
1. Clone the repository.
2. Open the project in your IDE.
3. Build the project with:
   ```bash
   mvn clean install
   ```
4. Run the application:
   ```bash
   mvn spring-boot:run
   ```
5. Visit the application in your browser:

   -  [[http://localhost:8080/greeting?name=Vistula](http://localhost:8080/greeting?name=Vistula)]

---

## Technologies Used

- **Spring Boot**: Framework for building web applications.
- **Thymeleaf**: Templating engine for rendering HTML.
- **Java**: Backend programming language.
- **HTML**: Frontend structure.
- **Maven**: Build automation tool.

---

