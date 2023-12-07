
# Spring MVC Interview Questions and Answers

## 1. What is Spring MVC?

Spring MVC (Model-View-Controller) is a framework for building web applications in Java. It's part of the larger Spring framework and follows the MVC design pattern, promoting a clean separation of concerns.

## 2. Explain the components of the Spring MVC architecture.

- **Model:** Represents the application data and business logic.
- **View:** Renders the model to the user interface.
- **Controller:** Handles user input, processes requests, and manages the flow of data between the model and view.

## 3. How does Spring MVC handle requests?

Spring MVC uses a DispatcherServlet as the front controller. It receives all incoming requests, delegates processing to the appropriate controllers, and manages the overall flow of the request through the application.

Example:
```java
@WebServlet("/app/*")
public class MyDispatcherServlet extends DispatcherServlet {
    // Configuration and customization here
}
```

## 4. Explain the role of @Controller annotation in Spring MVC.

The `@Controller` annotation is used to mark a class as a Spring MVC controller. It identifies the class as a Spring bean, allowing the framework to recognize and manage it. Controllers handle user requests and define request mappings.

Example:
```java
@Controller
@RequestMapping("/products")
public class ProductController {
    // Controller methods and mappings
}
```

## 5. What is the purpose of the @RequestMapping annotation?

The `@RequestMapping` annotation is used to map a URL pattern to a method in a controller. It defines the endpoint where the method should respond, allowing for flexible and customizable handling of incoming requests.

Example:
```java
@Controller
@RequestMapping("/products")
public class ProductController {

    @RequestMapping("/list")
    public String listProducts(Model model) {
        // Logic to populate the model with product data
        return "productList";
    }
}
```

## 6. Explain the difference between @RequestParam and @PathVariable in Spring MVC.

- **@RequestParam:** Used to extract parameters from the query string or form data in a URL. It is commonly used for simple request parameters.
- **@PathVariable:** Extracts values from URI templates, particularly useful for extracting values from the URI path itself.

Example:
```java
@RequestMapping("/products")
public String getProductById(@RequestParam Long id, Model model) {
    // Logic to retrieve and display product details
    return "productDetails";
}
```

## 7. What is the purpose of the ModelAndView class in Spring MVC?

`ModelAndView` is a container that holds both the model and the view in Spring MVC. It allows a controller to pass data to the view and specify the view name. This separation of concerns enhances flexibility and testability.

Example:
```java
@RequestMapping("/products")
public ModelAndView getProductDetails(@RequestParam Long id) {
    // Logic to retrieve product details
    ModelAndView modelAndView = new ModelAndView("productDetails");
    modelAndView.addObject("product", productService.getProductById(id));
    return modelAndView;
}
```

## 8. How does Spring MVC support form handling?

Spring MVC provides the `@ModelAttribute` annotation to bind form data to the model. It simplifies form handling by automatically populating model attributes from form parameters and vice versa.

Example:
```java
@Controller
@RequestMapping("/user")
public class UserController {

    @PostMapping("/save")
    public String saveUser(@ModelAttribute User user) {
        // Logic to save the user
        return "redirect:/user/profile";
    }
}
```

## 9. Explain the purpose of the @ResponseBody annotation.

The `@ResponseBody` annotation in Spring MVC is used to indicate that a method's return value should be serialized directly into the HTTP response body. It is commonly used for returning data in JSON or XML format.

Example:
```java
@Controller
@RequestMapping("/api")
public class ApiController {

    @GetMapping("/user/{id}")
    @ResponseBody
    public User getUserById(@PathVariable Long id) {
        // Logic to retrieve user data
        return userService.getUserById(id);
    }
}
```

## 10. What is the difference between @ModelAttribute and @SessionAttributes in Spring MVC?

- **@ModelAttribute:** Binds a method parameter or method-level attribute to a model attribute, making it available to the view.
- **@SessionAttributes:** Specifies attributes that should be stored in the session between requests, maintaining state across multiple requests.

Example:
```java
@Controller
@RequestMapping("/cart")
@SessionAttributes("cart")
public class ShoppingCartController {

    @ModelAttribute("cart")
    public Cart getCart() {
        // Logic to create or retrieve the cart
        return new Cart();
    }
}
```

## 11. How does Spring MVC handle file uploads?

Spring MVC supports file uploads through the `MultipartFile` interface. By using the `@RequestParam` annotation with the `MultipartFile` type, controllers can easily handle file uploads.

Example:
```java
@PostMapping("/upload")
public String handleFileUpload(@RequestParam("file") MultipartFile file) {
    // Logic to process the uploaded file
    return "uploadSuccess";
}
```

## 12. Explain the purpose of the @ExceptionHandler annotation.

The `@ExceptionHandler` annotation in Spring MVC is used to define methods that handle exceptions thrown by controller methods. It allows for centralized exception handling, improving code maintainability.

Example:
```java
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(Exception.class)
    public ModelAndView handleException(Exception ex) {
        ModelAndView modelAndView = new ModelAndView("error");
        modelAndView.addObject("errorMessage", "An error occurred: " + ex.getMessage());
        return modelAndView;
    }
}
```

## 13. What is the role of the ViewResolver in Spring MVC?

The `ViewResolver` in Spring MVC is responsible for mapping view names to actual view implementations. It allows for the decoupling of view names specified by controllers from the actual view technology used.

Example:
```java
@Bean
public ViewResolver viewResolver() {
    InternalResourceViewResolver resolver = new InternalResourceViewResolver();
    resolver.setPrefix("/WEB-INF/views/");
    resolver.setSuffix(".jsp");
    return resolver;
}
```

## 14. How does Spring MVC support internationalization and localization?

Spring MVC provides the `LocaleResolver` interface for resolving user locales. By configuring a `LocaleResolver` bean, developers can enable internationalization and localization in their applications.

Example:
```java
@Bean
public LocaleResolver localeResolver() {
    SessionLocaleResolver resolver = new SessionLocaleResolver();
    resolver.setDefaultLocale(Locale.US);
    return resolver;
}
```

## 15. Explain the purpose of the @RequestMapping method attribute in Spring MVC.

The `method` attribute of the `@RequestMapping` annotation is used to specify the HTTP method (GET, POST, PUT, DELETE, etc.) that a controller method can handle. It helps in creating RESTful APIs and ensures proper request mapping.

Example:
```java
@RequestMapping(value = "/update", method = RequestMethod.PUT)
public String updateProduct(@RequestBody Product product) {
    // Logic to update the product
    return "productUpdated";
}
```

## 16. What is the purpose of the RedirectAttributes interface in Spring MVC?

The `RedirectAttributes` interface is used to add flash attributes for a redirect scenario. Flash attributes are stored temporarily

 and survive only until the next request, making them suitable for one-time use during redirects.

Example:
```java
@PostMapping("/save")
public String saveProduct(Product product, RedirectAttributes redirectAttributes) {
    // Logic to save the product
    redirectAttributes.addFlashAttribute("message", "Product saved successfully");
    return "redirect:/products";
}
```

## 17. Explain the difference between ModelAndView and Model in Spring MVC.

- **ModelAndView:** Contains both the model data and the view name.
- **Model:** Represents the model data without specifying the view name. The view name is resolved separately.

Example (ModelAndView):
```java
@RequestMapping("/user/{id}")
public ModelAndView getUser(@PathVariable Long id) {
    ModelAndView modelAndView = new ModelAndView("userDetails");
    modelAndView.addObject("user", userService.getUserById(id));
    return modelAndView;
}
```

Example (Model):
```java
@RequestMapping("/user/{id}")
public String getUser(@PathVariable Long id, Model model) {
    model.addAttribute("user", userService.getUserById(id));
    return "userDetails";
}
```

## 18. How does Spring MVC support validation?

Spring MVC supports validation through the `@Valid` annotation and the `Validator` interface. By annotating method parameters with `@Valid`, the framework automatically applies validation rules defined by the associated `Validator`.

Example:
```java
@PostMapping("/save")
public String saveUser(@Valid @ModelAttribute("user") User user, BindingResult result) {
    // Validation logic and handling errors
    if (result.hasErrors()) {
        return "registrationForm";
    }
    userService.saveUser(user);
    return "redirect:/user/profile";
}
```

## 19. What is the purpose of the @InitBinder annotation?

The `@InitBinder` annotation in Spring MVC is used to customize the data binding process. It allows developers to register custom editors or validators for specific fields in the request.

Example:
```java
@InitBinder
public void initBinder(WebDataBinder binder) {
    SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
    binder.registerCustomEditor(Date.class, new CustomDateEditor(dateFormat, true));
}
```

## 20. Explain the Spring MVC interceptors and their use.

Spring MVC interceptors are used to intercept and process HTTP requests before they reach the controller. They can be used for tasks such as logging, authentication, or modifying the request attributes.

Example:
```java
public class MyInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) {
        // Pre-processing logic
        return true; // Continue processing the request
    }

    // Other methods for postHandle and afterCompletion
}
```

## 21. What is the purpose of the @ResponseStatus annotation in Spring MVC?

The `@ResponseStatus` annotation is used to declare the HTTP status code that a controller method should return. It simplifies the process of setting the status code for a specific response.

Example:
```java
@ResponseStatus(HttpStatus.NOT_FOUND)
public class ResourceNotFoundException extends RuntimeException {
    // Exception details
}
```

## 22. Explain the role of the ContentNegotiatingViewResolver in Spring MVC.

The `ContentNegotiatingViewResolver` in Spring MVC is responsible for selecting the appropriate view based on the requested media type (e.g., JSON, XML, HTML). It helps in supporting content negotiation in RESTful applications.

Example:
```java
@Bean
public ViewResolver contentNegotiatingViewResolver(ContentNegotiationManager manager) {
    ContentNegotiatingViewResolver resolver = new ContentNegotiatingViewResolver();
    resolver.setContentNegotiationManager(manager);
    return resolver;
}
```

## 23. How does Spring MVC handle exception handling using the @ControllerAdvice annotation?

The `@ControllerAdvice` annotation is used to define global exception handlers in Spring MVC. It allows developers to centralize exception handling logic and apply it across multiple controllers.

Example:
```java
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    @ResponseStatus(HttpStatus.NOT_FOUND)
    public ModelAndView handleResourceNotFoundException(ResourceNotFoundException ex) {
        ModelAndView modelAndView = new ModelAndView("error");
        modelAndView.addObject("errorMessage", ex.getMessage());
        return modelAndView;
    }
}
```

## 24. What is the purpose of the @PathVariableMap annotation in Spring MVC?

The `@PathVariableMap` annotation is used to bind all path variables in a request to a `Map<String, String>`. It simplifies handling multiple path variables within a controller method.

Example:
```java
@RequestMapping("/books/{category}/{title}")
public String getBookDetails(@PathVariable Map<String, String> pathVariables, Model model) {
    // Logic to retrieve book details
    model.addAttribute("book", bookService.getBook(pathVariables.get("category"), pathVariables.get("title")));
    return "bookDetails";
}
```

## 25. How does Spring MVC support CORS (Cross-Origin Resource Sharing)?

Spring MVC supports CORS by using the `@CrossOrigin` annotation on controllers or controller methods. It allows developers to specify allowed origins, headers, and methods for cross-origin requests.

Example:
```java
@RestController
@RequestMapping("/api")
@CrossOrigin(origins = "http://localhost:4200")
public class ApiController {

    @GetMapping("/data")
    public ResponseEntity<String> fetchData() {
        // Logic to fetch data
        return ResponseEntity.ok("Data fetched successfully");
    }
}
```

## 26. Explain the purpose of the @PathVariable and @RequestParam annotations in Spring MVC.

- **@PathVariable:** Extracts values from URI templates or path segments.
- **@RequestParam:** Extracts values from the query string or form data.

Example (PathVariable):
```java
@RequestMapping("/books/{id}")
public String getBookById(@PathVariable Long id, Model model) {
    // Logic to retrieve book details
    model.addAttribute("book", bookService.getBookById(id));
    return "bookDetails";
}
```

Example (RequestParam):
```java
@RequestMapping("/books")
public String getBooksByCategory(@RequestParam String category, Model model) {
    // Logic to retrieve books by category
    model.addAttribute("books", bookService.getBooksByCategory(category));
    return "bookList";
}
```

## 27. How does Spring MVC support data binding for complex objects?

Spring MVC supports data binding for complex objects through the `@ModelAttribute` annotation. It automatically binds form data to the corresponding model attributes, simplifying the handling of complex object structures.

Example:
```java
@Controller
@RequestMapping("/order")
public class OrderController {

    @PostMapping("/create")
    public String createOrder(@ModelAttribute Order order) {
        // Logic to create the order
        return "orderConfirmation";
    }
}
```

## 28. Explain the purpose of the RedirectView in Spring MVC.

The `RedirectView` in Spring MVC is a view implementation that performs a redirect to a specified URL. It is useful for redirecting users to another resource or URL after a successful operation.

Example:
```java
@RequestMapping("/submit")
public String submitForm(@ModelAttribute FormData formData, RedirectAttributes redirectAttributes) {
    // Logic to process form data
    redirectAttributes.addFlashAttribute("message", "Form submitted successfully");
    return "redirect:/success";
}
```

## 29. What is the role of the HiddenHttpMethodFilter in Spring MVC?

The `HiddenHttpMethodFilter` in Spring MVC allows clients to perform HTTP PUT and DELETE requests by including a special form field named

@satish_gavhane
