# Quick Start Guide - Run Your Site

## ⚠️ Important: Database Setup Required

Your Django backend needs Supabase database credentials to run. Follow these steps:

### Step 1: Create `.env` File in `backend/` folder

Create a file named `.env` in the `backend` directory with your Supabase credentials:

```env
SECRET_KEY=django-insecure-change-this-in-production-12345
DEBUG=True

# Supabase Database Connection
# Get these from: https://supabase.com/dashboard → Your Project → Settings → Database
SUPABASE_DB_HOST=db.xxxxx.supabase.co
SUPABASE_DB_NAME=postgres
SUPABASE_DB_USER=postgres
SUPABASE_DB_PASSWORD=your-supabase-password-here
SUPABASE_DB_PORT=5432

# Optional: OpenAI API Key (for AI chatbot)
OPENAI_API_KEY=sk-your-key-here

# Optional: Razorpay Keys (for payments)
RAZORPAY_KEY_ID=rzp_test_xxxxx
RAZORPAY_KEY_SECRET=your-secret-here
```

### Step 2: Get Your Supabase Credentials

1. Go to: https://supabase.com/dashboard
2. Select your project
3. Go to **Settings** → **Database**
4. Find **Connection string** section
5. Copy:
   - **Host** (e.g., `db.xxxxx.supabase.co`)
   - **Password** (click "Reveal")
   - Port is usually `5432`

### Step 3: Run Backend Setup

After creating `.env` file, run:

```powershell
cd backend
python manage.py migrate
python manage.py load_sample_faqs
python manage.py runserver
```

### Step 4: Run Frontend

In a **NEW** terminal:

```powershell
npm run dev
```

### Step 5: Open in Browser

Go to: **http://localhost:5173**

---

## Current Status

✅ **Migrations Created** - Database migrations are ready  
✅ **Frontend Starting** - React app should be running  
❌ **Backend Needs Database** - Add Supabase credentials to `.env`  

---

## What's Working Without Database?

- ✅ Frontend UI (React)
- ✅ Static pages
- ❌ FAQ Chatbot (needs database)
- ❌ AI Chatbot (needs database + OpenAI key)
- ❌ Payment features (needs database + Razorpay keys)

---

## Quick Test (After Database Setup)

Once you've added Supabase credentials and run migrations:

1. **Test FAQ Chatbot:**
   - Open chatbot in browser
   - Ask: "How do I book an appointment?"

2. **Test API:**
   ```bash
   curl -X POST http://localhost:8000/api/chat/faq/ -H "Content-Type: application/json" -d "{\"message\": \"how do I book an appointment?\"}"
   ```

---

## Need Help?

- **Database connection error?** → Check Supabase credentials in `.env`
- **Frontend not loading?** → Make sure `npm install` ran successfully
- **Backend not starting?** → Check if port 8000 is already in use

