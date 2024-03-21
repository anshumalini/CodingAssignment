# Coding Assignment Backend

This is a Spring Boot project that provides RESTful endpoints for handling orders. It includes functionality to create new orders and retrieve existing orders.

## Endpoints

### Create Order

- **URL:** `/orders`
- **Method:** `POST`
- **Description:** Creates a new order with the provided details.
- **Request Body:** JSON object containing the order details.
  ```json
  {
    "instrument": "string",
    "quantity": 0,
    "side": "BUY",
    "type": "LIMIT",
    "limitPrice": 0
  }
  ```
- **Response:** Returns a JSON object representing the created order or an error response if the input is invalid or if there is an internal server error.
  ```json
  {
    "id": 1,
    "instrument": "string",
    "quantity": 0,
    "side": "BUY",
    "type": "LIMIT",
    "limitPrice": 0.00
  }
  ```

### Get Orders

- **URL:** `/orders`
- **Method:** `GET`
- **Description:** Retrieves all existing orders from the database.
- **Response:** Returns a JSON array containing the list of orders or a message indicating that no orders were found in the database.

## Error Handling

- If the input for creating an order is invalid, such as missing required fields or incorrect values, a `400 Bad Request` response is returned along with an error message.
- If there is an internal server error while creating an order, a `500 Internal Server Error` response is returned along with an appropriate error message.

## Dependencies

This project relies on the following dependencies:

- Spring Boot Starter Web: For building web applications with Spring MVC.
- Spring Boot Starter Validation: For validating input data.
- Other dependencies might be added based on specific requirements.

## How to Run

1. Clone the repository to your local machine.
2. Make sure you have JDK17 and Maven installed.
3. Navigate to the project directory in the terminal.
4. Run `mvn spring-boot:run` to start the Spring Boot application or in IDE run CodingassignmentbackendApplication.
5. Once the application is running, you can access the endpoints using tools like Postman or cURL.

## Accessing the API

To access the API, follow these steps:

1. **Login with Predefined Username and Password:**
  - Use the predefined username and password to authenticate and obtain a JWT token.
  - Make a POST request to the `/login` endpoint with the following payload:
    ```json
    {
        "username": "user",
        "password": "password"
    }
    ```
  - Upon successful authentication, the API will respond with a JWT token.

2. **Use JWT Token for Authorization:**
  - Copy the JWT token received in the response.
  - In subsequent requests to any API endpoint, include this token in the Authorization header.
  - Set the Authorization header value to `Bearer <your_token>` where `<your_token>` is the JWT token obtained during login.

Example using cURL:
   ```bash
   curl -X GET "http://localhost:8080/orders" -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
   ```

3. **Access API Endpoints:**
  - With the JWT token included in the Authorization header, you can now access any API endpoint that requires authentication.
  - Make sure to include the token in the Authorization header of every request you send to the API.

By following these steps, you will be able to successfully authenticate and access the API endpoints using the provided JWT token.
