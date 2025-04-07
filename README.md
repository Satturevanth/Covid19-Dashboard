📊 COVID-19 India Portal

This is a backend application built using Node.js, Express, and SQLite that manages COVID-19 data across various states and districts in India. The portal supports user authentication using JWT tokens and provides secure APIs for managing states and districts' COVID-19 statistics.

💠 Technologies Used

Node.js

Express.js

SQLite

JWT (JSON Web Token)

bcrypt (for password hashing)

📁 Database Schema

🗂️ state Table

Column Name

Type

state_id

INTEGER

state_name

TEXT

population

INTEGER

🗂️ district Table

Column Name

Type

district_id

INTEGER

district_name

TEXT

state_id

INTEGER

cases

INTEGER

cured

INTEGER

active

INTEGER

deaths

INTEGER

🧑‍💻 user Table (for login authentication)

Sample credentials for testing:

{
  "username": "christopher_phillips",
  "password": "christy@123"
}

🔐 Authentication Flow

All APIs (except login) require a valid JWT token for access.

🔑 Login API

Endpoint: /login/Method: POST

✅ Request Body

{
  "username": "christopher_phillips",
  "password": "christy@123"
}

♻️ Scenarios:

Unregistered user: Returns status 400 with message Invalid user

Wrong password: Returns status 400 with message Invalid password

Success: Returns status 200 with a JWT token

✅ Response (Success)

{
  "jwtToken": "ak2284ns8Di32......"
}

🔐 JWT Authentication

All routes except /login/ must include a valid JWT token in the header:

Authorization: Bearer <jwt_token>

❌ If token is missing or invalid:

Status code: 401

Body: Invalid JWT Token

📡 API Endpoints

✅ API 1: Get All States

Path: /states/

Method: GET

Description: Returns all states

Response:

[
  {
    "stateId": 1,
    "stateName": "Andaman and Nicobar Islands",
    "population": 380581
  },
  ...
]

✅ API 2: Get State by ID

Path: /states/:stateId/

Method: GET

Response:

{
  "stateId": 8,
  "stateName": "Delhi",
  "population": 16787941
}

✅ API 3: Add a New District

Path: /districts/

Method: POST

Request:

{
  "districtName": "Bagalkot",
  "stateId": 3,
  "cases": 2323,
  "cured": 2000,
  "active": 315,
  "deaths": 8
}

Response:

District Successfully Added

✅ API 4: Get District by ID

Path: /districts/:districtId/

Method: GET

Response:

{
  "districtId": 322,
  "districtName": "Palakkad",
  "stateId": 17,
  "cases": 61558,
  "cured": 59276,
  "active": 2095,
  "deaths": 177
}

✅ API 5: Delete District by ID

Path: /districts/:districtId/

Method: DELETE

Response:

District Removed

✅ API 6: Update District by ID

Path: /districts/:districtId/

Method: PUT

Request:

{
  "districtName": "Nadia",
  "stateId": 3,
  "cases": 9628,
  "cured": 6524,
  "active": 3000,
  "deaths": 104
}

Response:

District Details Updated

✅ API 7: Get State-Wise Stats

Path: /states/:stateId/stats/

Method: GET

Response:

{
  "totalCases": 724355,
  "totalCured": 615324,
  "totalActive": 99254,
  "totalDeaths": 9777
}

⚙️ Setup Instructions

Clone the repository

git clone <your-repo-url>
cd covid19-india-portal

Install dependencies

npm install

Run the server

node app.js

Use tools like Postman or Thunder Client to test the APIs.

✅ Project Features

JWT-based Authentication

Login API with proper error handling

Full CRUD operations on States & Districts

Middleware for token validation

Clean API responses

Easy to extend and maintain

📂 Folder Structure (Suggested)

.
├── app.js
├── covid19IndiaPortal.db
├── package.json
├── node_modules/
├── utils/
│   └── authentication.js
├── routes/
│   ├── stateRoutes.js
│   └── districtRoutes.js
└── controllers/
    ├── stateController.js
    └── districtController.js

👨‍💼 Author

Revanth SattuBuilt as part of NxtWave’s Full Stack Development Course.

