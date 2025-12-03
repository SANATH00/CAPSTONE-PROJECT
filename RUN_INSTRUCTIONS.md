# How to Run Ask Your Vet Site

This guide will help you run both the **React Frontend** and **Django Backend**.

## Prerequisites

1. **Node.js** installed (for frontend)
2. **Python 3.8+** installed (for backend)
3. **Supabase account** with your project set up (for database)
4. **OpenAI API Key** (for chatbot)

---

## Step 1: Setup Backend (Django)

### 1.1 Install Python Dependencies

Open **PowerShell** or **Command Prompt** and run:

```powershell
cd backend
pip install -r requirements.txt
```

### 1.2 Get Supabase Database Credentials

1. Go to your **Supabase Dashboard**: https://supabase.com/dashboard
2. Select your project
3. Go to **Settings** > **Database**
4. Scroll to **Connection string** section
5. Copy these details:
   - **Host** (e.g., `db.xxxxx.supabase.co`)
   - **Database name** (usually `postgres`)
   - **Port** (usually `5432`)
   - **Password** (click "Reveal" to see it)

### 1.3 Create `.env` File

Create a file named `.env` in the `backend` folder with:

```env
SECRET_KEY=your-secret-key-change-this-in-production
DEBUG=True

# Supabase Database Connection
SUPABASE_DB_HOST=db.your-project-ref.supabase.co
SUPABASE_DB_NAME=postgres
SUPABASE_DB_USER=postgres
SUPABASE_DB_PASSWORD=your-supabase-db-password-from-step-1.2
SUPABASE_DB_PORT=5432

# OpenAI API Key
OPENAI_API_KEY=sk-your-openai-api-key-here
```

### 1.4 Setup Database

Since you're using Supabase, the database already exists! Just run migrations:

```powershell
cd backend
python manage.py makemigrations
python manage.py migrate
```

### 1.5 Start Django Server

```powershell
cd backend
python manage.py runserver
```

**✅ Backend will run at:** `http://localhost:8000`
**✅ API endpoint:** `http://localhost:8000/api/chat/ai/`

**Keep this terminal window open!**

---

## Step 2: Setup Frontend (React)

### 2.1 Install Node Dependencies

Open a **NEW** PowerShell/Command Prompt window and run:

```powershell
npm install
```

### 2.2 Start Frontend Dev Server

```powershell
npm run dev
```

**✅ Frontend will run at:** `http://localhost:5173` (or the port shown in terminal)

**Keep this terminal window open!**

---

## Step 3: Open in Browser

Open Chrome and go to: **`http://localhost:5173`**

You should see your Ask Your Vet website!

---

## Quick Start Commands Summary

### Terminal 1 (Backend):
```powershell
cd backend
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

### Terminal 2 (Frontend):
```powershell
npm install
npm run dev
```

---

## Troubleshooting

### "npm is not recognized"
- Install Node.js from https://nodejs.org (LTS version)

### "pip is not recognized"
- Install Python from https://www.python.org
- Make sure to check "Add Python to PATH" during installation

### "Database connection error"
- Check your Supabase database credentials in `backend/.env`
- Make sure you're using the correct host (from Supabase Dashboard)
- Verify the password is correct (it's different from your Supabase account password)
- Ensure your IP is allowed in Supabase (Settings > Database > Connection pooling)

### "OPENAI_API_KEY not set"
- Add your OpenAI API key to `backend/.env` file
- Get your key from: https://platform.openai.com/api-keys

### "Port already in use"
- Django: Change port with `python manage.py runserver 8001`
- Vite: It will automatically use the next available port

---

## What's Running?

- **Frontend (React)**: `http://localhost:5173` - Your main website
- **Backend (Django API)**: `http://localhost:8000` - API endpoints
- **Chatbot API**: `http://localhost:8000/api/chat/ai/` - AI chatbot endpoint

---

## Next Steps

1. Test the chatbot by sending a POST request to `/api/chat/ai/`
2. Connect your React frontend to the Django backend API
3. Update CORS settings in `backend/askyourvet/settings.py` if needed

