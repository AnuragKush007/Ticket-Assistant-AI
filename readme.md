🤖 AI Ticket Assistant

An AI-powered ticket management system that automatically categorizes, prioritizes, and assigns support tickets to the most appropriate moderators using Google Gemini AI.

This system reduces manual effort in ticket routing and improves response efficiency through AI-driven automation and skill-based moderator assignment.

🚀 Features
🧠 AI-Powered Ticket Processing

Automatic ticket categorization

Priority detection using AI

AI-generated moderator notes

Identification of required technical skills

👨‍💻 Smart Moderator Assignment

Automatic skill-based moderator matching

Regex-based skill detection

Admin fallback assignment if no matching moderator is found

👥 User Management

Role-based access control

User

Moderator

Admin

Moderator skill management

Secure JWT authentication

⚙️ Background Processing

Event-driven architecture using Inngest

Asynchronous ticket processing

Automated email notifications

🛠️ Tech Stack
Technology	Usage
Node.js	Backend runtime
Express.js	API framework
MongoDB	Database
JWT	Authentication
Inngest	Background job processing
Google Gemini API	AI ticket analysis
Nodemailer	Email notifications
Mailtrap	Email testing
Nodemon	Development auto-reload
📋 Prerequisites

Make sure you have the following installed:

Node.js (v14+)

MongoDB

Google Gemini API Key

Mailtrap Account

⚙️ Installation
1️⃣ Clone the repository
git clone <repository-url>
cd ai-ticket-assistant
2️⃣ Install dependencies
npm install
3️⃣ Environment setup

Create a .env file in the root directory.

# MongoDB
MONGO_URI=your_mongodb_uri

# JWT
JWT_SECRET=your_jwt_secret

# Email (Mailtrap)
MAILTRAP_SMTP_HOST=your_mailtrap_host
MAILTRAP_SMTP_PORT=your_mailtrap_port
MAILTRAP_SMTP_USER=your_mailtrap_user
MAILTRAP_SMTP_PASS=your_mailtrap_password

# AI (Gemini)
GEMINI_API_KEY=your_gemini_api_key

# Application
APP_URL=http://localhost:3000
▶️ Running the Application
Start the backend server
npm run dev
Start the Inngest dev server
npm run inngest-dev

Inngest dashboard will run on:

http://localhost:8288
📝 API Endpoints
🔐 Authentication
Method	Endpoint	Description
POST	/api/auth/signup	Register new user
POST	/api/auth/login	Login and receive JWT
🎫 Tickets
Method	Endpoint	Description
POST	/api/tickets	Create new ticket
GET	/api/tickets	Get all user tickets
GET	/api/tickets/:id	Get ticket details
🛠️ Admin
Method	Endpoint	Description
GET	/api/auth/users	Get all users
POST	/api/auth/update-user	Update role & skills
🔄 Ticket Processing Flow
1️⃣ Ticket Creation

User submits a ticket with title and description.

2️⃣ AI Processing

Inngest triggers an event:

on-ticket-created

Gemini AI analyzes the ticket and generates:

Ticket category

Priority level

Required skills

Helpful moderator notes

3️⃣ Moderator Assignment

The system:

Searches moderators with matching skills

Assigns the best matching moderator

Falls back to admin assignment if none found

4️⃣ Notification

An email is sent to the assigned moderator containing:

Ticket details

AI-generated notes

Priority level

🧪 Testing Ticket Creation

Use this CURL command:

curl -X POST http://localhost:3000/api/tickets \
-H "Content-Type: application/json" \
-H "Authorization: Bearer YOUR_JWT_TOKEN" \
-d '{
"title": "Database Connection Issue",
"description": "Experiencing intermittent database connection timeouts"
}'
🔍 Troubleshooting
Port conflict
lsof -i :8288
kill -9 <PID>
AI Errors

Check:

GEMINI_API_KEY

API limits

Request format

Email Issues

Verify:

Mailtrap credentials

SMTP configuration

Email logs

📦 Dependencies
@inngest/agent-kit
bcrypt
cors
dotenv
express
inngest
jsonwebtoken
mongoose
nodemailer
🙏 Acknowledgements

Inngest — Background job processing

Google Gemini — AI-powered ticket analysis

Mailtrap — Email testing

MongoDB — Database
