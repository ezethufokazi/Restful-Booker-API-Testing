# Restful Booker API Testing Project

**Author:** Ezethu Fokazi  
**Tool:** Postman  
**Project Type:** API Testing Portfolio Project
## Documentation
View the full API documentation here: [Restful Booker API Documentation](https://documenter.getpostman.com/view/52307578/2sBXcKBHyz)
## Test Report
View the Newman HTML test report: [Test Report](https://github.com/ezethufokazi/Restful-Booker-API-Testing/blob/main/Restful-Booker/Restful-Booker-Newman-Test-Report.html)

---

## Project Overview

This project is an API testing portfolio piece built by an aspiring QA Engineer. It covers the full Restful Booker API — a practice API built specifically for testers — using Postman. The project includes positive and negative test cases, environment variables, dynamic data, and a documented bug report.

The Restful Booker API simulates a hotel booking system with endpoints for creating, retrieving, updating, and deleting bookings. All test scripts were written in JavaScript using Postman's built-in test framework.

---

## Tools Used

- **Postman** — API testing and test script execution
- **JavaScript** — Test assertions and pre/post request scripts
- **GitHub** — Version control and portfolio hosting

---

## Project Structure

```
Restful-Booker Collection
├── Auth
│   └── Create Token
├── Bookings
│   ├── Create Booking
│   ├── Get All Bookings
│   ├── Get Booking by name
│   ├── Get Booking by check in/check out date
│   ├── Get Booking by ID
│   ├── Update Booking
│   ├── Partial Update Booking
│   └── Delete Booking
├── Ping
│   └── Health Check
└── Negative Tests
    ├── Create Booking - Missing Required Field
    ├── Create Booking - Invalid Data Type
    ├── Get Booking - Invalid ID
    ├── Update Booking - Invalid Token
    ├── Update Booking - Missing Auth
    └── Delete Booking - Non Existent ID
```

---

## Endpoints Covered

| Method | Endpoint | Description |
|---|---|---|
| POST | /auth | Generate auth token |
| POST | /booking | Create a new booking |
| GET | /booking | Get all bookings |
| GET | /booking?firstname=&lastname= | Filter bookings by first and last name |
| GET | /booking?checkin=&checkout= | Filter bookings by check in and check out date |
| GET | /booking/:id | Get booking by ID |
| PUT | /booking/:id | Full update of a booking |
| PATCH | /booking/:id | Partial update of a booking |
| DELETE | /booking/:id | Delete a booking |
| GET | /ping | Health check |

---

## Test Approach

**Positive Testing**
- Happy path scenarios for all endpoints
- Status code validation
- Response body assertions using dynamic environment variables
- Response time checks

**Negative Testing**
- Missing required fields
- Invalid data types
- Invalid auth token
- Missing auth
- Non existent booking IDs

**Environment Variables**
All test data is stored dynamically in environment variables. The Create Booking request saves all booking details automatically which are then reused across GET, PUT, PATCH and DELETE requests. This means no hardcoded values anywhere in the collection.

---

## Bug Report

Six bugs were identified and documented during testing:

| # | Bug | Endpoint | Expected | Actual |
|---|---|---|---|---|
| 1 | No input validation on required fields | POST /booking | 400 Bad Request | 500 Internal Server Error |
| 2 | No data type validation on totalprice | POST /booking | 400 Bad Request | 200 OK with totalprice saved as null |
| 3 | Date filter returns inconsistent results | GET /booking | Array with matching results | Empty array returned inconsistently |
| 4 | Wrong status code for non existent booking deletion | DELETE /booking/:id | 404 Not Found | 403 Forbidden |
| 5 | Wrong status code for successful deletion | DELETE /booking/:id | 200 OK or 204 No Content | 201 Created |
| 6 | Wrong status code for health check | GET /ping | 200 OK | 201 Created |

---

## How to Run the Collection

**Prerequisites**
- Postman installed on your machine
- Download the collection and environment files from this repository

**Steps**
1. Open Postman
2. Click **Import** and import both the collection and environment files
3. Select the **RestfulBooker** environment from the top right dropdown
4. Click the **Runner** button
5. Select the **Restful-Booker** collection
6. Make sure the request order is correct (Auth and Create Booking must run first)
7. Click **Run Restful-Booker**

**Important Note**  
Restful Booker runs on a shared public server that resets periodically. Always run Auth and Create Booking first to ensure fresh test data exists before running the rest of the collection.

---

## Key Learnings

- API testing fundamentals using Postman
- Writing JavaScript test assertions for status codes, response bodies and response times
- Using environment variables for dynamic and reusable test data
- Difference between positive and negative testing
- Bug identification and documentation
- Understanding of HTTP methods, status codes, headers and authentication
- Difference between token based auth (Cookie) and Basic Auth
- Importance of test execution order in API testing
