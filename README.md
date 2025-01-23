# JWT Authentication API

This project is a Node.js-based API for user authentication and authorization using JSON Web Tokens (JWT). It includes features such as user registration, login, token refresh, and role-based access control.

## Project Structure

```
.env
.gitignore
config/
  allowedOrigins.js
  corsOptions.js
  roles_list.js
controllers/
  authController.js
  employeesController.js
  logoutController.js
  refreshTokenController.js
  registerController.js
logs/
  errLog.txt
  reqLog.txt
middleware/
  credentials.js
  errorHandler.js
  logEvents.js
  verifyJWT.js
  verifyRoles.js
model/
  employees.json
  users.json
package.json
public/
  css/
    style.css
  img/
  text/
    data.txt
routes/
  api/
    employees.js
  auth.js
  logout.js
  refresh.js
  register.js
  root.js
server.js
views/
  404.html
  index.html
```

## Features

- **User Registration**: Allows new users to register by providing a username and password.
- **User Login**: Authenticates users and provides JWT tokens for session management.
- **Token Refresh**: Provides a mechanism to refresh JWT tokens.
- **Role-Based Access Control**: Restricts access to certain endpoints based on user roles.
- **Logging**: Logs requests and errors for monitoring and debugging.

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/Ashim-Stha/jwt-auth-api.git
   cd jwt-auth-api
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Create a `.env` file in the root directory and add the following environment variables:
   ```
   ACCESS_TOKEN_SECRET=youraccesstokensecret
   REFRESH_TOKEN_SECRET=yourrefreshtokensecret
   ```

4. Start the server:
   ```sh
   npm run dev
   ```

## API Endpoints

### Public Routes

- `POST /register` - Register a new user ( `registerController.handleNewUser` )
- `POST /auth` - Authenticate a user and get access and refresh tokens ( `authController.handleLogin` )
- `GET /refresh` - Refresh the access token ( `refreshTokenController.handleRefreshToken` )
- `GET /logout` - Logout a user ( `logoutController.handleLogout` )

### Protected Routes

- `GET /employees` - Get all employees (requires valid JWT) ( `employeesController.getAllEmployees` )
- `POST /employees` - Create a new employee (requires Admin or Editor role) ( `employeesController.createNewEmployee` )
- `PUT /employees` - Update an employee (requires Admin or Editor role) ( `employeesController.updateEmployee` )
- `DELETE /employees` - Delete an employee (requires Admin role) (
`employeesController.deleteEmployee` )
- `GET /employees/:id` - Get a specific employee by ID (requires valid JWT) ( `employeesController.getEmployee` )

## Middleware

- `logger` - Logs all incoming requests 
- `errorHandler`- Handles errors and logs them 
- `verifyJWT` - Verifies JWT in the request headers
- `verifyRoles` - Verifies user roles for protected routes 
- `credentials` - Handles CORS credentials
  
## Configuration

- CORS configuration is handled in `corsOptions.js`
- Allowed origins are specified in `allowedOrigins.js`
- User roles are defined in `roles_list.js`


## Logging

- Request logs are stored in `reqLog.txt`
- Error logs are stored in `errLog.txt`
