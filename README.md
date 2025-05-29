🚕 Scalable Ride-Sharing Backend with Microservices

This project is a scalable and modular backend system for a **ride-sharing service**. It’s designed with **microservices architecture**, real-time communication, and robust load balancing to ensure high availability and flexibility.

---

🌟 Objective  
To build a reliable and scalable backend for ride-sharing that can handle growing user demand, efficiently manage rides, and support real-time interactions.

---

🌟 Key Features  
✅ **Microservices Architecture** – The backend is divided into separate services for:
- **User Management** – Handles user registration, authentication, and profiles.  
- **Ride Management** – Manages ride creation, updates, and tracking.  
- **Notifications** – Sends real-time updates to users and drivers.

✅ **Asynchronous Communication** – Utilizes **RabbitMQ** for efficient message queuing and inter-service communication, improving scalability and reducing bottlenecks.

✅ **Load Balancing** – Dynamic load balancing ensures consistent performance and availability, even during high-traffic periods.

---

⚙️ Tech Stack  
- **Express.js** – Fast and flexible web server framework.  
- **Node.js** – JavaScript runtime environment powering the backend logic.  
- **MongoDB** – NoSQL database for storing user and ride data.  
- **RabbitMQ** – Message broker for handling asynchronous tasks and communication.  
- **JWT (JSON Web Tokens)** – Secure authentication and authorization for users and drivers.

---

💻 How to Run Locally  

➡️ **Step 1:**  
Open multiple terminal windows and navigate to each service’s folder:  
```bash
cd user
npx nodemon index.js
cd ../captain
npx nodemon index.js
cd ../ride
npx nodemon index.js
cd ../notifications
npx nodemon index.js
➡️ Step 2:
Connect to MongoDB on port 27017 using MongoDB Compass.

➡️ Step 3:
Connect to RabbitMQ using CloudAMQP (or any RabbitMQ host).

🔧 Usage API Steps

✅ User Flow:
1️⃣ Register User

bash
Copy
Edit
POST http://localhost:3000/user/register  
BODY:  
{
  "name": "aditya-user",
  "email": "aditya-email",
  "password": "aditya-password"
}
2️⃣ Login User

bash
Copy
Edit
POST http://localhost:3000/user/login  
BODY:  
{
  "email": "aditya-email",
  "password": "aditya-password"
}
💡 Copy the returned token.

3️⃣ Get User Profile

sql
Copy
Edit
GET http://localhost:3000/user/profle  
HEADERS:  
Authorization: Bearer <token>
4️⃣ Logout User

sql
Copy
Edit
GET http://localhost:3000/user/logout  
HEADERS:  
Authorization: Bearer <token>
✅ Captain Flow:
5️⃣ Register Captain

bash
Copy
Edit
POST http://localhost:3000/captain/register  
BODY:  
{
  "name": "aditya-captain",
  "email": "aditya-email-captain",
  "password": "aditya-password-captain"
}
6️⃣ Login Captain

bash
Copy
Edit
POST http://localhost:3000/captain/login  
BODY:  
{
  "email": "aditya-email-captain",
  "password": "aditya-password-captain"
}
💡 Copy the returned token.

7️⃣ Get Captain Profile

bash
Copy
Edit
GET http://localhost:3000/captain/profle  
HEADERS:  
Authorization: Bearer <token>
8️⃣ Toggle Captain Availability

bash
Copy
Edit
PATCH http://localhost:3000/captain/toggle-availability  
HEADERS:  
Authorization: Bearer <token>
✅ Ride Flow:
9️⃣ Create Ride

makefile
Copy
Edit
POST http://localhost:3000/ride/create-ride  
BODY:  
{
  "pickup": "jss",
  "destination": "airport"
}
HEADERS:  
Authorization: Bearer <user_token>
🔄 Get New Rides (Captain)

sql
Copy
Edit
GET http://localhost:3000/captain/new-ride  
HEADERS:  
Authorization: Bearer <captain_token>
💡 Repeat Step 9 to create more rides.

🔄 Accept Ride (Captain)

bash
Copy
Edit
PUT http://localhost:3000/ride/accept-ride?rideid=<id>  
HEADERS:  
Authorization: Bearer <captain_token>
🔄 Get Accepted Ride (User)

sql
Copy
Edit
GET http://localhost:3000/user/accepted-ride  
HEADERS:  
Authorization: Bearer <user_token>
🎯 Overall Flow Summary:

Login as user

Login as captain

Create new rides

Captain sees new rides and accepts

User can see the accepted ride status

🚨 Security & Deployment Notes
✅ Use environment variables for sensitive data (MongoDB URI, JWT secrets, RabbitMQ URI).
✅ Add authentication and rate limiting for production environments.
✅ Consider Docker and Docker Compose for consistent deployments across all services.

✨ Scalable, real-time ride-sharing backend ready to grow!
Built with ❤️ by [yourusername].

sql
Copy
Edit

✅ Save as `README.md`, commit and push:  
```bash
git add README.md
git commit -m "Add final README with detailed explanation and API usage steps"
git push
