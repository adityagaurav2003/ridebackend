# 🚕 Scalable Ride-Sharing Backend with Microservices

A robust backend for a ride-sharing service, designed with microservices, real-time communication, and dynamic load balancing.

---

## 🌟 Objective  
Build a **scalable** and **modular** backend system to support high user demand, efficient ride management, and real-time updates.

---

## 🌟 Key Features  
✅ **Microservices Architecture** – Independent services for user, ride, and captain management.  
✅ **Asynchronous Communication** – Uses RabbitMQ for reliable, decoupled service communication.  
✅ **Load Balancing** – Ensures high performance and availability.  
✅ **Authentication** – Secured with JWT tokens.  
✅ **MongoDB** – Data storage for users, rides, and captains.

---

## ⚙️ Tech Stack  
- **Node.js** + **Express.js** – Server-side logic and APIs.  
- **MongoDB** – Database for storing and managing data.  
- **RabbitMQ** – Message broker for asynchronous communication.  
- **JWT** – Secure user and captain authentication.

---

## 🚀 How to Run Locally  

1️⃣ **Start Each Microservice**  
Open separate terminal windows for each service:  
```bash
cd user && npx nodemon index.js  
cd captain && npx nodemon index.js  
cd ride && npx nodemon index.js  
cd gateway && npx nodemon index.js  
2️⃣ Connect to MongoDB
Use MongoDB Compass or another client to connect to the default port:


mongodb://localhost:27017
3️⃣ Connect to RabbitMQ
Use CloudAMQP or a local RabbitMQ instance for messaging.

🧪 API Usage
🟡 User Flow

Register
POST /user/register
{ "name": "aditya-user", "email": "aditya-email", "password": "aditya-password" }


Login
POST /user/login
{ "email": "aditya-email", "password": "aditya-password" }
Copy the JWT token from the response.

Profile
GET /user/profle
Header: Authorization: Bearer <token>

Logout
GET /user/logout
Header: Authorization: Bearer <token>

🟠 Captain Flow
Register
POST /captain/register
{ "name": "aditya-captain", "email": "aditya-email-captain", "password": "aditya-password-captain" }

Login
POST /captain/login
{ "email": "aditya-email-captain", "password": "aditya-password-captain" }
Copy the JWT token.

Profile
GET /captain/profle
Header: Authorization: Bearer <token>

Toggle Availability
PATCH /captain/toggle-availability
Header: Authorization: Bearer <token>

🟢 Ride Flow
Create Ride (User)
POST /ride/create-ride
{ "pickup": "jss", "destination": "airport" }
Header: Authorization: Bearer <user_token>

Get New Rides (Captain)
GET /captain/new-ride
Header: Authorization: Bearer <captain_token>

Accept Ride (Captain)
PUT /ride/accept-ride?rideid=<id>
Header: Authorization: Bearer <captain_token>

Get Accepted Ride (User)
GET /user/accepted-ride
Header: Authorization: Bearer <user_token>

🔄 Overall Flow
User logs in & creates a ride.

Captain logs in & sees available rides.

Captain accepts a ride.

User sees the accepted ride status.

🚨 Security & Deployment
✅ Use environment variables for sensitive data (MongoDB URI, JWT secret, RabbitMQ URI).
✅ Add authentication & rate limiting in production.
✅ Consider Docker Compose for orchestration and deployment.

✨ Scalable, real-time backend to power modern ride-sharing applications.
