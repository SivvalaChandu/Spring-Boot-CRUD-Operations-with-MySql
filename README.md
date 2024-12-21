# CRUD Application with MySQL and Spring Boot

This is a simple Spring Boot application that demonstrates CRUD (Create, Read, Update, Delete) operations on a `User` entity using a MySQL database. The application uses Spring Data JPA for database interaction and exposes a RESTful API for managing users.


---

## Technologies Used

- **Spring Boot**: A Java-based framework for building production-grade applications.
- **Spring Data JPA**: For seamless integration with relational databases.
- **MySQL**: The database used for storing user information.
- **Lombok**: A Java library to reduce boilerplate code (e.g., getters, setters, constructors).
- **Jakarta Persistence API (JPA)**: For ORM and database interactions.
- **Spring Web**: To create RESTful APIs.
  
---

## Project Setup

1. **Clone the Repository:**

   Clone the project repository to your local machine:

   ```
   https://github.com/SivvalaChandu/Spring-Boot-CRUD-Operations-with-MongoDB
   ```

## Database Configuration

   MySQL Database Configuration:

   In `src/main/resources/application.properties`, configure the MySQL database connection:

```
    spring.datasource.url=jdbc:mysql://localhost:3306/your_db_name
    spring.datasource.username=your_mysql_username
    spring.datasource.password=your_mysql_password
    spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
    spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

### Create MySQL Database:

Ensure that a database exists in MySQL with the name specified in application.properties or if not it will create a new one:

   ``` CREATE DATABASE your_db_name;```

## API Endpoints
#### 1. Create a User

    URL: `/api/users`

    Method: `POST`

    Request Body:
```
{
    "id": "user123",
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com"
}

```
Response:

   Status: `201 Created` \
   Body:
```
    {
        "id": "user123",
        "firstName": "John",
        "lastName": "Doe",
        "email": "john.doe@example.com"
    }
```
#### 2. Get All Users

   URL: `/api/users`

   Method: `GET`

   Response:
        Status: `200 OK` \
        Body:
```
    [
        {
            "id": "user123",
            "firstName": "John",
            "lastName": "Doe",
            "email": "john.doe@example.com"
        },
        {
            "id": "user456",
            "firstName": "Jane",
            "lastName": "Doe",
            "email": "jane.doe@example.com"
        }
    ]
```

#### 3. Get User by ID

   URL: `/api/users/{id}`

   Method: `GET`

   Response: \
     Success: 
       Status: `200 OK` \
       Body:

```
        {
            "id": "user123",
            "firstName": "John",
            "lastName": "Doe",
            "email": "john.doe@example.com"
        }
```

   Failure (User Not Found):

   Status: `404 Not Found` \
   Body: ```User not found```

#### 4. Update User

   URL: `/api/users/{id}`

   Method: `PUT`

   Request Body:
```
{
    "firstName": "Johnathan",
    "lastName": "Doe",
    "email": "johnathan.doe@example.com"
}
```
Response:

   Success: \
        Status: 200 OK \
        Body:
```
        {
            "id": "user123",
            "firstName": "Johnathan",
            "lastName": "Doe",
            "email": "johnathan.doe@example.com"
        }
```
   Failure (User Not Found): \
         Status: `400 Bad Request` \
         Body: `User update failed: User not found or invalid data`

#### 5. Delete User

   URL: `/api/users/{id}`

   Method: `DELETE`

   Response: \
        Status: `200 OK` \
        Body: `User deleted Successfully.`


## Access the Application:

The application will be accessible at:
` http://localhost:8080 `

### Test the API:
Use any REST client (e.g., Postman) to test the endpoints mentioned above.
