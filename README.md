# BusReservationSystem
 In this Project we are covering these functionalities mentioned below

#Providing provision of Registration of User for that ::

we have made a User Table with one to Many mapping with Role . Before running your code you have to insert ADMIN and USER Role in the Role table then while you Run the Application you go on Register Page --> Enter Details --> Sumit . The Call will go to Registration COntroller and save the data to Database and then it will redirect it to /login .
#/login ->> you enter your email Id and password -> the call will go to login Controller --> User Service where it loadsUserByUserName -> it checkss the User present in DB and the password match and then the request goes to --> Custom Success Handler . if the email or password is incorrect then the error is thrown on UI that Either Username or Password is Incorrect .

#Custom Success Handler ->> The Custom Success Handler , Handles the request basis on the ROle of the User after Login process --> if the ROle is Admin , it will redirect to Admin Dashboard , if Role is User then it will redirect to User Dashboard .

#Admin Dashboard ->> So , Admin Dashboard shows a form to upload the Bus data and it gets stored in Bus data Table . #User Dashboard ->> User Dashboard shows a filter to filter the Buses available for your to destination to from destination on a particular date . #Filetered data ->> Buses Data is visible on Dashboard screen in the form of table . When you Click on Book button it will take you to the Booking page . #Booking Page ->> Here you will enter the no of passengers who are tralvelling along with you and automatically the Cost you have to pay will be calculated after you click on pay .

#Email with Ticket ->> A Dynamic Ticket is generated after you click on pay and is sent to the user's registered Email Id .And you will be redirected to the All your Bookings Page where you can see your all the booking in Tabular format with latest one on the top .

#Summary Page ->> This the Page where all your booking are available in Tabular Format and a button for Cancellation and Ticket Generation is given .

#Cancel button ->> You can Cancel your booking , by clicking on the Cancel button . #Ticket Generation ->> if the passenger has lost the Ticket , he can agin request for Generation of Ticket by clicking here.

### Steps

1. Extract the contents of the ZIP file.
2. Review the project structure and main components.
3. Create detailed documentation based on the extracted content.

The extracted directory contains the following items:

- `.gitattributes`
- `.gitignore`
- `.mvn`
- `README.md`
- `mvnw`
- `mvnw.cmd`
- `pom.xml`
- `src`

### Part A: How to Set Up, Configure, and Run the Project

1. **Prerequisites**
   - Java Development Kit (JDK) 11 or higher.
   - Maven 3.6+.
   - MySQL database (or the database you are using).

2. **Project Structure**
   - `src/main/java`: Contains the Java source files.
   - `src/main/resources`: Contains configuration files, like `application.properties`.
   - `pom.xml`: Maven configuration file.
   - `README.md`: Basic project information.

3. **Setup Instructions**
   1. **Clone the Repository**
      
      git clone <repository-url>
      cd BusReservationComplete-main
      

   2. **Configure the Database**
       Update the `src/main/resources/application.properties` file with your database credentials.
      
      properties
      spring.datasource.url=jdbc:mysql://localhost:3306/busreservation
      spring.datasource.username=root
      spring.datasource.password=yourpassword
      spring.jpa.hibernate.ddl-auto=update
      

   3. **Initialize the Database (Optional)**
      can use `schema.sql` and `data.sql` files placed in `src/main/resources` to initialize the database schema and data.

   4. **Build the Project**
     
      ./mvnw clean install
      
   5. **Run the Project**
     
      ./mvnw spring-boot:run
      
   6. **Running Tests**
    The project includes unit tests. Run the tests with:
      
      ./mvnw test
    

### Part B: API Endpoints, Request/Response Formats, and Data Validation Rules

#### Example Endpoint Documentation

**1. User Registration**

- **Endpoint:** `/api/auth/register`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - **Success (201 Created):**
    ```json
    {
      "id": 1,
      "name": "John Doe",
      "email": "john.doe@example.com"
    }
    ```
  - **Validation Errors (400 Bad Request):**
    ```json
    {
      "errors": [
        "Email is already in use",
        "Password must be at least 6 characters"
      ]
    }
    ```

**2. User Authentication**

- **Endpoint:** `/api/auth/login`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "email": "john.doe@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - **Success (200 OK):**
    ```json
    {
      "token": "jwt-token-here"
    }
    ```
  - **Authentication Error (401 Unauthorized):**
    ```json
    {
      "error": "Invalid email or password"
    }
    ```

**3. Booking a Ticket**

- **Endpoint:** `/api/bookings`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "busId": 1,
    "passengerId": 1,
    "seatNumber": "A1"
  }
  ```
- **Response:**
  - **Success (201 Created):**
    ```json
    {
      "bookingId": 1,
      "busId": 1,
      "passengerId": 1,
      "seatNumber": "A1",
      "status": "CONFIRMED"
    }
    ```
  - **Validation Errors (400 Bad Request):**
    ```json
    {
      "errors": [
        "Bus ID is required",
        "Passenger ID is required",
        "Seat number is required"
      ]
    }
    ```

You can now find this detailed information in the README.md file of your project. Here is a brief overview of what was added:

### How to Set Up, Configure, and Run the Project

#### Prerequisites
- Java Development Kit (JDK) 11 or higher.
- Maven 3.6+.
- MySQL database (or the database you are using).

#### Project Structure
- `src/main/java`: Contains the Java source files.
- `src/main/resources`: Contains configuration files, like `application.properties`.
- `pom.xml`: Maven configuration file.
- `README.md`: Basic project information.

#### Setup Instructions
1. **Clone the Repository**

   git clone <repository-url>
   cd BusReservationComplete-main
   

2. **Configure the Database**
   - Update the `src/main/resources/application.properties` file with your database credentials.
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/busreservation
   spring.datasource.username=root
   spring.datasource.password=yourpassword
   spring.jpa.hibernate.ddl-auto=update
   ```

3. **Initialize the Database (Optional)**
 can use `schema.sql` and `data.sql` files placed in `src/main/resources` to initialize the database schema and data.

4. **Build the Project**
   
   ./mvnw clean install
  

5. **Run the Project**
   
   ./mvnw spring-boot:run


#### Running Tests
- The project includes unit tests. Run the tests with:
   
   ./mvnw test
 

### API Endpoints, Request/Response Formats, and Data Validation Rules

#### User Registration
- **Endpoint:** `/api/auth/register`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - **Success (201 Created):**
    ```json
    {
      "id": 1,
      "name": "John Doe",
      "email": "john.doe@example.com"
    }
    ```
  - **Validation Errors (400 Bad Request):**
    ```json
    {
      "errors": [
        "Email is already in use",
        "Password must be at least 6 characters"
      ]
    }
    ```

#### User Authentication
- **Endpoint:** `/api/auth/login`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "email": "john.doe@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - **Success (200 OK):**
    ```json
    {
      "token": "jwt-token-here"
    }
    ```
  - **Authentication Error (401 Unauthorized):**
    ```json
    {
      "error": "Invalid email or password"
    }
    ```

#### Booking a Ticket
- **Endpoint:** `/api/bookings`
- **Method:** `POST`
- **Request:**
  ```json
  {
    "busId": 1,
    "passengerId": 1,
    "seatNumber": "A1"
  }
  ```
- **Response:**
  - **Success (201 Created):**
    ```json
    {
      "bookingId": 1,
      "busId": 1,
      "passengerId": 1,
      "seatNumber": "A1",
      "status": "CONFIRMED"
    }
    ```
  - **Validation Errors (400 Bad Request):**
    ```json
    {
      "errors": [
        "Bus ID is required",
        "Passenger ID is required",
        "Seat number is required"
      ]
    }
    ```
This is the Complete Jist of the Bus Reservation System.

