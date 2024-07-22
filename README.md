# User Login API with Email and OTP Authentication

This project implements a secure and efficient API system for user authentication using email and One-Time Password (OTP). Users can register, request an OTP, and verify the OTP to gain access.

## Setup

### Clone the repository:
```bash
git clone https://github.com/lalitkumarjangid/secure-user-registeration
```

Install dependencies:
```bash

npm install
```
## Set up environment variables:
Create a .env file in the root directory with the following content:
```bash
MONGODB_URI=mongodb://localhost:27017/user_login_api
JWT_SECRET=your_jwt_secret_key
PORT=4000
```
## Start the server:
```bash

node server.js
```





API Endpoints
1. User Registration

Endpoint: POST /api/register
Request Body:
```bash
{
  "email": "user@example.com"
}
```
Successful Response:
```bash
{
  "message": "Registration successful. Please verify your email."
}
```

cURL Example:
```bash
curl -X POST http://localhost:3000/api/register \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'
```

2. Request OTP

Endpoint: POST /api/request-otp
Request Body:
```bash
{
  "email": "user@example.com"
}
```
Successful Response:

```bash
{
  "message": "OTP sent to your email."
}
```
cURL Example:
```bash
curl -X POST http://localhost:3000/api/request-otp \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'
```
Note: Check the server console to see the mock email output with the OTP.

3. Verify OTP

Endpoint: POST /api/verify-otp
Request Body:
```bash
{
  "email": "user@example.com",
  "otp": "123456"
}
```
Successful Response:
```bash
{
  "message": "Login successful.",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
cURL Example:
```bash
curl -X POST http://localhost:3000/api/verify-otp \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "otp": "123456"}'
```
Note: Replace "123456" with the actual OTP received in the mock email output.

### Testing the API
Follow these steps to test the full authentication flow:

Register a new user using the /api/register endpoint.
Request an OTP for the registered user using the /api/request-otp endpoint.
Check your server console output to find the OTP that was "sent" to the user's email.
Use this OTP in the /api/verify-otp endpoint to verify the OTP and receive a JWT token.

# Notes

The OTP is valid for 10 minutes after it's generated.
For security testing, you can try:

Registering the same email twice
Requesting an OTP for a non-existent user
Verifying with an incorrect or expired OTP




