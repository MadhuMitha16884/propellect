
# 🏠 Propellect — Real Estate AI CRM Backend

A production-ready FastAPI backend for a Real Estate AI CRM platform, built during internship at **Purview India Consulting and Services LLP**.

Live API: [https://realestate-backend-qh6p.onrender.com](https://realestate-backend-qh6p.onrender.com)  
API Docs: [https://realestate-backend-qh6p.onrender.com/docs](https://realestate-backend-qh6p.onrender.com/docs)

---

## 🚀 Features

- **Lead Management** — Create, fetch, update and delete real estate leads
- **AI Lead Scoring** — Groq LLaMA 3 scores each lead 0–100 based on budget and intent
- **AI Property Matching** — Automatically matches leads to best available properties using AI
- **AI Chat Assistant** — Conversational AI with session memory for property suggestions
- **JWT Authentication** — Register, login, profile management with bcrypt password hashing
- **Twilio Integration** — Trigger real phone calls to leads directly from the API
- **Campaign Management** — Create and manage outreach campaigns
- **Property Listings** — Add and fetch property data
- **Analytics APIs** — Leads by day, conversion funnel, budget distribution
- **CSV Import** — Bulk import leads via CSV file upload
- **Dashboard Stats** — Real-time stats for the frontend dashboard

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| Python + FastAPI | Backend framework |
| PostgreSQL (Supabase) | Cloud database |
| SQLAlchemy | ORM |
| Pydantic v2 | Data validation |
| Groq (LLaMA 3.3-70b) | AI — chat, scoring, matching |
| JWT (python-jose) | Authentication tokens |
| bcrypt (passlib) | Password hashing |
| Twilio | Voice calls and SMS |
| Render | Cloud deployment |
| GitHub | Version control |

---

## 📁 Project Structure

```
realestate-backend/
├── main.py              # App entry point, CORS, routes
├── requirements.txt     # All dependencies
├── .env                 # Secret keys (never committed)
├── .gitignore           # Protects .env from GitHub
└── app/
    ├── __init__.py
    ├── database.py      # Supabase PostgreSQL connection
    ├── models.py        # Database table definitions
    ├── schemas.py       # Pydantic validation schemas
    └── routes.py        # All 22+ API endpoints
```

---

## 🔌 API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/register` | Register new user |
| POST | `/auth/login` | Login → returns JWT token |
| GET | `/auth/me` | Get logged-in user profile |
| PUT | `/auth/profile` | Update name, phone, company |
| PUT | `/auth/change-password` | Change password |

### Leads
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/lead` | Add a new lead |
| GET | `/leads` | Get all leads |
| GET | `/leads/{id}` | Get single lead |
| DELETE | `/leads/{id}` | Delete a lead |
| POST | `/lead/{id}/call` | Trigger Twilio call to lead |
| POST | `/leads/import` | Bulk import leads via CSV |

### AI Features
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/chat` | AI chat with session memory |
| POST | `/ai/score-lead` | Score a lead 0–100 using AI |
| POST | `/ai/match-property` | Match lead to best property using AI |

### Dashboard & Analytics
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/dashboard/stats` | Total leads, hot leads, campaigns |
| GET | `/analytics/leads-by-day` | Leads grouped by date |
| GET | `/analytics/funnel` | Conversion funnel stats |
| GET | `/analytics/budget-distribution` | Budget range breakdown |

### Campaigns & Properties
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET/POST | `/campaigns` | Fetch / create campaigns |
| DELETE | `/campaigns/{id}` | Delete campaign |
| GET/POST | `/properties` | Fetch / create properties |

### Utility
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/health` | Health check |
| GET | `/test-twilio` | Test Twilio config |
| GET | `/` | Root endpoint |

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/MadhuMitha16884/realestate-backend.git
cd realestate-backend
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Create `.env` file
```env
DATABASE_URL=postgresql://postgres.YOUR_PROJECT:PASSWORD@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres
GROQ_API_KEY=your_groq_api_key
SECRET_KEY=your_jwt_secret_key
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_PHONE_NUMBER=your_twilio_number
AGENT_PHONE_NUMBER=your_phone_number
```

### 4. Run the server
```bash
uvicorn main:app --reload
```

### 5. Open API docs
```
http://127.0.0.1:8000/docs
```

---

## 🗄️ Database Tables

| Table | Description |
|-------|-------------|
| `leads` | All real estate leads |
| `users` | Registered users |
| `campaigns` | Outreach campaigns |
| `properties` | Property listings |
| `chat_sessions` | AI chat history for memory |
| `lead_property_matches` | AI matched lead-property pairs |

---

## 🚀 Deployment

Backend is deployed on **Render** with auto-deploy from GitHub.

Every `git push origin main` triggers an automatic redeployment.

Environment variables are stored securely in Render's dashboard — never in code.

---

## 👥 Team

| Name | Role |
|------|------|
| **Madhu Mitha** | Backend Developer — FastAPI, AI, Deployment |
| **Nitya** | Frontend Developer — React, TypeScript |
| **Archana** | Frontend Developer — React, TypeScript |
| **Fatimah Zahraa** | Database — Supabase PostgreSQL setup |

---

## 🏢 Built During

**Purview India Consulting and Services LLP**  
Internship: 27 April 2026 – 11 June 2026  
Role: Software Development Intern  
Project: Real Estate GenAgent Development (Propellect / CallAIhm)

---

## 📄 License

This project was built as part of an internship and is for educational/demonstration purposes.
