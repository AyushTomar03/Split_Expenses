# Expense Splitting API

This project is a FastAPI application for managing and splitting expenses among users. It allows users to create expenses, and it can split expenses equally, based on exact amounts, or by percentage.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)

## Prerequisites

Before running the project, ensure you have the following installed:

- Python 3.7 or higher
- pip (Python package installer)

## Installation

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/yourusername/expense-splitting-api.git
   cd expense-splitting-api

## Usage

uvicorn app.main:app --reload

## API Endpoints

User Endpoints
1. Create User
Endpoint: POST /users
Description: Creates a new user.
Request Body:
{
  "email": "user@example.com",
  "name": "John Doe",
  "mobile": "1234567890"
}

Response:
Status Code: 201 Created
Response Body:
{
  "id": 1,
  "email": "user@example.com",
  "name": "John Doe",
  "mobile": "1234567890"
}


2. Get User by ID
Endpoint: GET /users/{user_id}
Description: Retrieves the user information by user ID.
Path Parameters:
user_id (integer): The ID of the user to retrieve.
Response:
Status Code: 200 OK
Response Body:
{
  "id": 1,
  "email": "user@example.com",
  "name": "John Doe",
  "mobile": "1234567890"
}
Status Code: 404 Not Found (if user not found)

Response Body:
{
  "detail": "User not found"
}
Expense Endpoints


3. Create Expense
Endpoint: POST /expenses
Description: New expense.
Request Body:
{
  "description": "Lunch",
  "amount": 100.0,
  "split_method": "Equal",
  "created_by": 1,
  "participants": [
    {"user_id": 1},
    {"user_id": 2},
    {"user_id": 3}
  ]
}
Response:
Status Code: 201 Created
Response Body:
{
  "id": 1,
  "description": "Lunch",
  "amount": 100.0,
  "split_method": "Equal",
  "created_by": 1,
  "participants": [
    {"id": 1, "user_id": 1, "amount_owed": 33.33},
    {"id": 2, "user_id": 2, "amount_owed": 33.33},
    {"id": 3, "user_id": 3, "amount_owed": 33.33}
  ]
}

4. Get Expenses by User ID
Endpoint: GET /expenses/{user_id}
Description: Get all expense by user id
Path Parameters:
user_id (integer): The ID of the user whose expenses are to be retrieved.
Response:
Status Code: 200 OK

Response Body:
[
  {
    "id": 1,
    "description": "Lunch",
    "amount": 100.0,
    "split_method": "Equal",
    "created_by": 1,
    "participants": [
      {"id": 1, "user_id": 1, "amount_owed": 33.33},
      {"id": 2, "user_id": 2, "amount_owed": 33.33},
      {"id": 3, "user_id": 3, "amount_owed": 33.33}
    ]
  }
]
