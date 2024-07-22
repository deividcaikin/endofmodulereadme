# Shopping Security System Project
<br>
-----
This project is a Python implementation for managing a shopping database, including user registration, login with multi-factor authentication (MFA), role management, and product management. The project uses MySQL as the database and is designed to be run in a Jupyter Notebook environment together with local installation of MySql database with login details. It also provides unit testing capabilities.

Main focus of this project is to show encryption and MFA capabilities with fully functional DB and data exchange capabilities.

As this project is implemented using local DB and Jupyter Notebook most of the code references will be specified as "Run code 'SECTION 6', 'SECTION 7' etc."

-----

## Libraries Required
<br>
-----
Before running the project, make sure you have the following Python libraries installed:
- MySQL Connector library
- Password validator library
- MFA Authentication simulation library
- Encryption library
- Email validation library

With according commands (SECTION 1):
```sh
!pip install mysql-connector-python --upgrade
!pip install password-validator
!pip install pyotp
!pip install bcrypt
!pip install email-validator
```
## Database Setup Required
<br>
-----
Ensure Latest MySQL version is set up locally with a database called shopping_db. The following connection details are used in the project(SECTION 2):

```python
host = "localhost"
user = "deividcaikin"
password = "password123"
database = "shopping_db"

sqlConn = SQLConnection(host, user, password, database)
connection = sqlConn.connection
```

-----

## Successful execution of code
<br>
-----
As soon as database connection is setup all the code can be simply ran by running SECTION 1 - 9 in Jupyter Notebook .ipynb file, as each section separately provides details required.
-----



## SQLConnection Class
<br>
-----
The SQLConnection class (SECTION 3) is responsible for connecting to the MySQL database and executing queries. It handles:

- Establishing a connection to the database
- Closing the connection
- Executing queries with and without results
- Executing insert operations

-----

## Table Creation Queries (Implemented within python jupyter notebook)
<br>
-----
SECTION 4 provides 3 tables creation: users, roles and products. Run this SECTION to either recreate or newly create tables if deleted during testing.

They are run via Jupyter Notebook as many times as needed, as it provides the ability to recreate tables if they are deleted during testing process.
```mysql
CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    role_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS roles (
    id INT AUTO_INCREMENT PRIMARY KEY,
    role_name VARCHAR(255) NOT NULL
);

CREATE TABLE IF NOT EXISTS products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
-----
## Data creation
<br>
-----
SECTION 7 is responsible for creating test data for Product and Roles. It was used to test whether the set up of data is correct.
-----
## Data gathering and collection
<br>
-----
An example of data gathering with UserManipulation, RoleManipulation and ProductManipulation classes and collection in classes User, Role and Product is shown is SECTION 9 where examples are provided of how to get and set the data.
-----

## User Management
<br>
-----
Run SECTION 5 code to build classes UserManipulation, User

### UserManipulation Class
<br>
-----
Handles database actions related to users such as registration, login, retrieving user details, updating user information, and deleting users.

### User Class
<br>
-----
Stores user data for convenience and provides methods to retrieve user information.

-----

## Role Management
<br>
-----
Run SECTION 5 code to build classes RoleManipulation, Role
### RoleManipulation Class
<br>
-----
Handles database actions related to roles such as creating roles, retrieving all roles, and retrieving roles by ID or type.

### Role Class
<br>
-----
Stores role data for convenience and provides methods to retrieve role information.

### RoleName Enum
<br>
-----
Defines role names and allows for easy expansion.


-----

## Product Management
<br>
-----
Run SECTION 5 code to build classes ProductManipulation, Product
### ProductManipulation Class
<br>
-----
Handles database actions related to products such as creating products, retrieving product details, updating product information, and deleting products.

### Product Class
<br>
-----
Stores product data for convenience and provides methods to retrieve product information.

-----
## Multi-Factor Authentication (MFA)
<br>
-----
The MFA class implements MFA using PyOTP. It generates and verifies time-based one-time passwords (TOTPs).

-----

## User Processing
<br>
-----
Run SECTION 5 code to build class MFA.

The UserProcessing class handles user registration and login processes, including password validation, email validation, and MFA verification.

-----

## TESTING 
<br>
-----
SECTION 8 is responsible for running tests. Running that section will provide details if tests have passed. Test cases should be setup appropriately for your test data.
## Test SQL Connectivity

### Class: TestSQLConnection
<br>
-----
- testCreateServerConnection: Verifies successful database connection.
- testCloseConnection: Ensures the database connection can be closed properly.

## Test User Management

### Class: TestUserManipulation
<br>
-----
- testLoginUser: Tests the user login functionality.
- testGetUserById: Verifies retrieval of user details by user ID.
- testGetUserByEmail: Ensures user details can be retrieved by email.
- testGetAllUsers: Checks if all users can be retrieved.
- testUpdateUser: Tests updating user details.

## Test Role Management

### Class: TestRoleManipulation
<br>
-----
- testCreateRole: Ensures a new role can be created.
- testGetAllRoles: Verifies retrieval of all roles.
- testGetRoleById: Tests retrieval of role details by role ID.
- testGetRoleByType: Ensures retrieval of role details by role type.

## Test Product Management

### Class: TestProductManipulation
<br>
-----
- testCreateProduct: Verifies that a product can be created.
- testGetAllProducts: Ensures all products can be retrieved.
- testGetProductById: Tests retrieval of product details by product ID.
- testGetProductByName: Verifies retrieval of product details by product name.
- testUpdateProduct: Ensures product details can be updated.

## Test Multi-Factor Authentication

### Class: TestMFA
<br>
-----
- testVerifyPin: Tests the verification of a generated PIN.
- testShowPin: Verifies the generation of a PIN.

## Test User Functional

### Class: TestUserFunctional
<br>
-----
- testRegistrationLogin: Tests the full registration and login process.
- testFailedRegistration: Verifies registration failure with duplicate email.
- testRegistrationWrongEmailFormat: Ensures registration fails with incorrect email format.
- testRegistrationPassNodigits: Tests registration failure with password missing digits.
- testRegistrationPassNotEnoughLength: Verifies registration failure with a short password.
- testLoginWithWrongEmailAndPass: Ensures login fails with incorrect email and password.
- testLoginWithWrongPass: Tests login failure with incorrect password.

## Test Data Classes

### User Class

### Class: TestUser
<br>
-----
- testGetDataPlain: Tests plain data retrieval of a user.
- testGetDataPlainNoDates: Verifies plain data retrieval without dates.
- testGetDataDictionary: Ensures dictionary format data retrieval.
- testGetRoleName: Tests retrieval of the role name associated with the user.

### Role Class

### Class: TestRole
<br>
-----
- testGetDataPlain: Tests plain data retrieval of a role.
- testGetDataDictionary: Verifies dictionary format data retrieval.

### Product Class

### Class: TestProduct
<br>
-----
- testGetDataPlain: Tests plain data retrieval of a product.
- testGetDataPlainNoDates: Verifies plain data retrieval without dates.
- testGetDataDictionary: Ensures dictionary format data retrieval.


## References to Libraries
<br>
-----

MySql. (2024) MySQL Connector/Python Developer Guide. Available from: https://dev.mysql.com/doc/connector-python/en/ [Accessed 20 July 2024]

Batra, T. (2020) password-validator 1.0. Available from: https://pypi.org/project/password-validator/ [Accessed 20 July 2024]

kislyuk & nathforge (2023) pyotp 2.9.0. Available from: https://pypi.org/project/pyotp/ [Accessed 20 July 2024]

Kehrer, P. (2024) bcrypt 4.1.3. Available from: https://pypi.org/project/bcrypt/#description [Accessed 20 July 2024]

Tauberer, J. (2024) email-validator 2.2.0. Available from: https://pypi.org/project/email-validator/#description [Accessed 20 July 2024]

-----
