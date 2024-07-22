# Shopping Database Project

This project is a Python implementation for managing a shopping database, including user registration, login with multi-factor authentication (MFA), role management, and product management. The project uses MySQL as the database and is designed to be run in a Jupyter Notebook environment together with local instalation of MySql database with login details. It also provides unit testing capabilities.

-----

## Libraries Required

Before running the project, make sure you have the following Python libraries installed:
- MySQL Connector library
- Password validator library
- MFA Authentication simulation library
- Encryption library
- Email validation library

With according commands:
- !pip install mysql-connector-python --upgrade
- !pip install password-validator
- !pip install pyotp
- !pip install bcrypt
- !pip install email-validator

-----

## Database Setup Required

Ensure Latest MySQL version is set up locally with a database called shopping_db. The following connection details are used in the project:

host = "localhost"
user = "deividcaikin"
password = "password123"
database = "shopping_db"

-----

##SQLConnection Class

The SQLConnection class is responsible for connecting to the MySQL database and executing queries. It handles:

- Establishing a connection to the database
- Closing the connection
- Executing queries with and without results
- Executing insert operations

-----

##Table Creation Queries (Implemented within python jupyter notebook)
They are run via Jupyter Notebook as many times as needed, as it provides the ability to recreate tables if they are deleted during testing proccess

-----

##User Management

###UserManipulation Class
Handles database actions related to users such as registration, login, retrieving user details, updating user information, and deleting users.

###User Class

Stores user data for convenience and provides methods to retrieve user information.

-----

##Role Management

###RoleManipulation Class
Handles database actions related to roles such as creating roles, retrieving all roles, and retrieving roles by ID or type.

###Role Class

Stores role data for convenience and provides methods to retrieve role information.

###RoleName Enum

Defines role names and allows for easy expansion.


-----

##Product Management

###ProductManipulation Class
Handles database actions related to products such as creating products, retrieving product details, updating product information, and deleting products.

###Product Class

Stores product data for convenience and provides methods to retrieve product information.

-----
##Multi-Factor Authentication (MFA)

The MFA class implements MFA using PyOTP. It generates and verifies time-based one-time passwords (TOTPs).

-----

##User Processing

The UserProccessing class handles user registration and login processes, including password validation, email validation, and MFA verification.

-----

##Test SQL Connectivity

###Class: TestSQLConnection

- testCreateServerConnection: Verifies successful database connection.
- testCloseConnection: Ensures the database connection can be closed properly.

##Test User Management

###Class: TestUserManipulation

- testLoginUser: Tests the user login functionality.
- testGetUserById: Verifies retrieval of user details by user ID.
- testGetUserByEmail: Ensures user details can be retrieved by email.
- testGetAllUsers: Checks if all users can be retrieved.
- testUpdateUser: Tests updating user details.

##Test Role Management

###Class: TestRoleManipulation

- testCreateRole: Ensures a new role can be created.
- testGetAllRoles: Verifies retrieval of all roles.
- testGetRoleById: Tests retrieval of role details by role ID.
- testGetRoleByType: Ensures retrieval of role details by role type.

##Test Product Management

###Class: TestProductManipulation

- testCreateProduct: Verifies that a product can be created.
- testGetAllProducts: Ensures all products can be retrieved.
- testGetProductById: Tests retrieval of product details by product ID.
- testGetProductByName: Verifies retrieval of product details by product name.
- testUpdateProduct: Ensures product details can be updated.

##Test Multi-Factor Authentication

###Class: TestMFA

- testVerifyPin: Tests the verification of a generated PIN.
- testShowPin: Verifies the generation of a PIN.

##Test User Functional

###Class: TestUserFunctional

- testRegistrationLogin: Tests the full registration and login process.
- testFailedRegistration: Verifies registration failure with duplicate email.
- testRegistrationWrongEmailFormat: Ensures registration fails with incorrect email format.
- testRegistrationPassNodigits: Tests registration failure with password missing digits.
- testRegistrationPassNotEnoughLength: Verifies registration failure with a short password.
- testLoginWithWrongEmailAndPass: Ensures login fails with incorrect email and password.
- testLoginWithWrongPass: Tests login failure with incorrect password.

##Test Data Classes

###User Class

##Class: TestUser

- testGetDataPlain: Tests plain data retrieval of a user.
- testGetDataPlainNoDates: Verifies plain data retrieval without dates.
- testGetDataDictionary: Ensures dictionary format data retrieval.
- testGetRoleName: Tests retrieval of the role name associated with the user.

###Role Class

### Class: TestRole

- testGetDataPlain: Tests plain data retrieval of a role.
- testGetDataDictionary: Verifies dictionary format data retrieval.

###Product Class

###Class: TestProduct

- testGetDataPlain: Tests plain data retrieval of a product.
- testGetDataPlainNoDates: Verifies plain data retrieval without dates.
- testGetDataDictionary: Ensures dictionary format data retrieval.

