# products-api-oop-tut

This repository holds my weekly lab work for **5COSC019W Object Oriented Programming** at the University of Westminster (studied through the Informatics Institute of Technology, IIT).

## Please note

This is **coursework for a university module**. It is not a product, a client project or something I am building or maintaining for real use. I created it only to complete the tutorials for the module, and it is kept here so my tutor and marker can see the work.

Because of that:

- The code follows the lab guides closely, so it is simple on purpose.
- Nothing here is production ready. There is no database, no authentication and no proper error handling.
- I do not plan to add features, accept contributions or provide support.

## What is in here

The project starts as a small Spring Boot REST API and grows a little each week. At the moment it covers up to Tutorial 3.

| Tutorial | Topic | What it adds |
|---|---|---|
| 1 | Getting started | Spring Boot project, first endpoints |
| 2 | Encapsulation and UML | `Product`, `Customer` and `Address` classes, with UML diagrams |
| 3 | Collections, generics and the service layer | `ProductService` holding a `List<Product>`, with endpoints to read, create, delete and search products |

### Tutorial 3 endpoints

Products are kept in memory, so the list is empty every time the app restarts.

| Method | Path | What it does |
|---|---|---|
| GET | `/products` | Returns all products |
| GET | `/products/{id}` | Returns one product by id |
| POST | `/products` | Creates a product. The service assigns the id, so send only `name` and `price` |
| DELETE | `/products/{id}` | Deletes a product by id |
| GET | `/products/search?name=...` | Returns products whose name contains the text |

A known gap, left in on purpose for now: asking for an id that does not exist returns status 200 with an empty body, when it should be a 404. The module covers this properly in a later lecture.

### Project structure

```
src/main/java/uk/ac/westminster/products_api/
    Product.java             the data class
    ProductService.java      holds the list and the rules (no HTTP code)
    ProductController.java   handles the web requests and calls the service
docs/uml/
    Product.puml             PlantUML source for the class diagram
    Product.png              the rendered class diagram
```

The controller depends on the service, and the service holds `Product` objects. Nothing points back from the service to the controller.

## Running it

You need Java and Maven (the Maven wrapper is included).

```
./mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`. You can also run `ProductsApiApplication` from IntelliJ.

Then open Swagger UI at <http://localhost:8080/swagger-ui.html> to try the endpoints.

## Built with

- Java
- Spring Boot
- springdoc OpenAPI (Swagger UI)
- PlantUML for the class diagrams

## Author

K. Sasiru Virajith, Software Engineering student at the University of Westminster through IIT.
