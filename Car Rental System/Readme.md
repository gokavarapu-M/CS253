# Car Rental Management System

## Overview

This project is a Car Rental Management System that allows users to rent cars, manage user data, and handle car availability. It consists of various classes to represent cars, users, and databases for managing them. The system supports different types of users, including customers, employees, and managers.

## Classes

### Car

Represents a car in the system.

#### Attributes:

- `Company`: The company of the car.
- `Model`: The model of the car.
- `regNo`: The registration number of the car.
- `Condition`: The condition of the car (available, rented, etc.).
- `rented_to`: The ID of the user to whom the car is rented.
- `due_date`: The due date for returning the car.

#### Functions:

- `Car(string company, string model, string regNo, string condition)`: Constructor to initialize a car.
- `bool Check_availability()`: Checks if the car is available.
- `bool Car_Rent(string &userID, int days)`: Rents the car to a user for a specified number of days.
- `void Show_duedate()`: Shows the due date for the car.
- `bool operator==(const Car &c) const`: Overloaded equality operator.
- `bool operator<(const Car &c) const`: Overloaded less than operator for sorting cars in database.
- `void Rented()`: Marks the car as rented.
- `void Display()`: Displays the car's details.

### Car_DB

Manages the collection of cars in the system.

#### Functions:

- `void Add(Car car)`: Adds a new car to the database.
- `void Delete(Car car)`: Deletes a car from the database.
- `void Delete(string regNo)`: Deletes a car by its registration number.
- `bool Contains(string regNo)`: Checks if a car is in the database.
- `bool Rent_Car(string &userID, string regNo, int days)`: Rents a car to a user.
- `void Update(Car car, string condition, int dueDate)`: Updates the car's condition and due date.
- `void Update(Car car)`: Updates the car's details.
- `Car Search(string regNo)`: Searches for a car by its registration number.
- `void Display()`: Displays all cars in the database.
- `void Check_availability()`: Checks the availability of all cars.

### User (Base Class)

Represents a user in the system. Base class for `Customer`, `Employee`, and `Manager`.

#### Attributes:

- `ID`: User's ID.
- `password`: User's password.
- `fineamt`: User's fine amount.
- `max_cars`: Maximum number of cars a user can rent.
- `rented_cars`: Set of cars rented by the user.
- `type`: Type of user (Customer, Employee, Manager).
- `name`: Name of the user.
- `rent_days`: Number of days the user has rented cars.

#### Functions:

- `virtual ~User() {}`: Virtual destructor for proper cleanup.
- `int Calculate_fine(int days)`: Calculates the fine for late returns.
- `void Clear_fine_amount(int amount)`: Clears the user's fine amount.
- `void Return_cars(int days)`: Returns the cars rented by the user.
- `bool operator==(const User &u)`: Overloaded equality operator.
- `void Show_cars()`: Shows the cars rented by the user.
- `bool Check_password(string pwd)`: Checks if the password is correct.
- `void Show_dues()`: Shows the user's due amount.
- `void Rent_Car()`: Rents a car.
- `void Logout()`: Logs the user out.
- `void Display()`: Displays the user's details.
- `virtual void Help()`: Provides help information for the user.

### Derived User Classes

#### Employee

Derived from `User`.

- `Employee(string id, string name, string password)`: Constructor to initialize an employee.
- `void Help()`: Provides help information for the employee.

#### Customer

Derived from `User`.

- `Customer(string id, string name, string password)`: Constructor to initialize a customer.
- `void Help()`: Provides help information for the customer.

#### Manager

Derived from `User`.

- `Manager()`: Constructor to initialize a manager.
- `void Add_Car()`: Adds a new car to the car database.
- `void Delete_Car()`: Deletes a car from the car database.
- `void Add_User()`: Adds a new user to the user database.
- `void Delete_User()`: Deletes a user from the user database.
- `void Change_day()`: Changes the current day in the system.
- `void Help()`: Provides help information for the manager.
- `void Check_rent()`: Checks the rent status of cars.
- `void User_Cars()`: Displays the cars rented by users.

### User_DB

Manages the collection of users in the system.

#### Functions:

- `void Add(User *user)`: Adds a new user to the database.
- `bool Delete(User *user)`: Deletes a user from the database.
- `bool Delete(string id)`: Deletes a user by their ID.
- `User *Search(string id)`: Searches for a user by their ID.
- `bool Contains(string id)`: Checks if a user is in the database.
- `void Update(string id, string password)`: Updates a user's password.
- `void Display()`: Displays all users in the database.

## Helper Functions

- `void Login()`: Handles user login.
- `void Show_today()`: Displays the current day in the system.

## Variables

- `TODAY`: Represents the current day in the system.
- `program_terminate`: Variable to stop the program.

## How to Run

1. **Compile the code** using your preferred C++ compiler. For example:

   ```sh
   g++ -o car_rental main.cpp
   ```

2. **Run the executable**:

   ```sh
   ./car_rental
   ```

3. **Interact with the system** as prompted. Use the login function to log in as different users and perform various operations like renting cars, adding users, and managing the car database.
