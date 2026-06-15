# Niramaya — Women's Hormonal Health Screening Platform

🔗 **Live Demo:** https://hackathon-topaz-gamma.vercel.app

A comprehensive hormonal health screening web app that detects conditions like Hypothyroidism, Anemia, PCOS, and 21 more through symptom-based screening and optional lab report integration.

> ⚠️ This is a screening tool, NOT a medical diagnosis. Always consult a healthcare professional for medical advice.

---

## 🚀 Features

- **Symptom-Based Screening** — 30+ symptoms across physical, emotional, and behavioral categories
- **24+ Condition Detection** — Major: Hypothyroidism, Hyperthyroidism, Iron-deficiency Anemia, PCOS, Lifestyle Fatigue. Minor: Vitamin D/B12 deficiency, PMS/PMDD, Stress, Sleep issues, and more
- **Lab Report Integration** — Upload blood test reports (CBC, TSH, Ferritin) for enhanced accuracy
- **Results Dashboard** — Visual confidence percentage rankings per condition
- **AI Health Chatbot** — Groq-powered assistant for health insights
- **PDF Reports** — Download detailed screening reports
- **Timeline Tracking** — Track health progress over time
- **Find Doctors** — Locate nearby healthcare providers

---

## 🏗️ Architecture

```
Frontend (React + Vite)          Backend (Node.js + Express)
┌──────────────────────┐         ┌──────────────────────────┐
│  Zustand store       │◄───────►│  JWT Authentication      │
│  Framer Motion UI    │         │  Screening Algorithm     │
│  6 page routes       │         │  Lab Report Parser       │
│  PDF generation      │         │  Groq AI chatbot         │
└──────────────────────┘         └──────────────────────────┘
                                           │
                                    MongoDB Atlas
```

**Frontend:** React 18 + Vite · Zustand · Framer Motion · PDFKit

**Backend:** Node.js + Express · MongoDB + Mongoose · JWT · Groq AI · PDFKit

---

## 🧠 Core Screening Algorithm

`screeningService.js` works in 5 stages:

1. **Symptom Normalization** — Parse and weight reported symptoms
2. **Condition Evaluation** — Score each of 24 conditions against symptom profile
3. **Lab Integration** — Factor in uploaded blood test values (CBC, TSH, Ferritin)
4. **Minor Tendency Detection** — Identify supporting/secondary conditions
5. **Confidence Calculation** — Produce percentage-based ranked results

### Detected Conditions

**Major (5):** Iron-deficiency Anemia · Hypothyroidism · Hyperthyroidism · PCOS/PCOD · Lifestyle Fatigue

**Minor (19):** Vitamin D deficiency · B12 deficiency · PMS/PMDD · Stress-related fatigue · Sleep disruption · Endometriosis · Menorrhagia · Amenorrhea · Uterine Fibroids · Insulin Resistance · and more

---

## 📱 User Flow

```
Sign Up → Onboarding (age/height/weight/lifestyle)
       → Symptom Check-in (30+ symptoms, 3 categories)
       → Lab Upload (optional)
       → Screening Engine
       → Results Dashboard (confidence % per condition)
       → PDF Report Download
       → Timeline (track over time)
```

---

## 🔐 API Reference

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register user |
| POST | `/api/auth/login` | Login user |
| GET | `/api/auth/profile` | Get profile |

### Screening
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/screen` | Run screening |
| GET | `/api/screen/history/:userId` | Screening history |
| GET | `/api/screen/progression/:userId` | Risk progression |
| GET | `/api/screen/report/:sessionId` | Download PDF |

### Symptoms & Profile
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/symptoms` | Save symptom log |
| GET | `/api/symptoms/:userId` | Get symptom history |
| PUT | `/api/profile` | Update profile |

---

## ⚙️ Local Setup

```bash
# Clone
git clone https://github.com/Kush-67598/Niramaya.git
cd Niramaya

# Backend
cd backend
npm install
cp .env.example .env   # fill in values below
npm run dev

# Frontend
cd ../frontend
npm install
npm run dev
# → http://localhost:5173
```

### Environment Variables

```env
# backend/.env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_secure_random_string_min_32_chars
JWT_EXPIRES_IN=7d
GROQ_API_KEY=your_groq_key

# frontend/.env
VITE_API_BASE_URL=http://localhost:5000/api
```

---

## 👤 Author

Built by [Kush Kumar Singh](https://github.com/Kush-67598)

---

## 📄 License

MIT
