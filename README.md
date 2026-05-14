# MedAgent AI — AI-Powered Medical Assistant

> **Revolutionize healthcare with AI-powered medical solutions.**

MedAgent AI is a full-stack web application that connects users with specialized AI doctor agents via real-time voice conversations. Powered by **Vapi AI** for voice interactions, **OpenAI** for intelligent responses, and **Clerk** for authentication, it provides an accessible and privacy-respecting way to get medical guidance across 10 specializations — anytime, anywhere.

---

## Features

- Voice-Based AI Consultations — Speak directly with AI doctor agents using real-time voice (powered by Vapi AI)
- 10 Medical Specializations — General Physician, Pediatrician, Dermatologist, Psychologist, Nutritionist, Cardiologist, ENT Specialist, Orthopedic, Gynecologist, and Dentist
- Secure Authentication — Sign up / sign in powered by Clerk
- User Dashboard — Track and review past medical sessions
- Session Chat History — AI-generated summaries and transcripts of consultations stored in Neon (PostgreSQL)
- Doctor Suggestion Engine — Smart API that recommends the right specialist based on user symptoms
- Subscription Model — Free access to General Physician; premium plan unlocks all specialists
- Modern Stack — Built with Next.js 15 App Router, TypeScript, Tailwind CSS v4, Drizzle ORM, and Framer Motion

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Framework** | Next.js 15 (App Router) |
| **Language** | TypeScript |
| **Styling** | Tailwind CSS v4 + Framer Motion |
| **Auth** | Clerk |
| **Voice AI** | Vapi AI |
| **AI/LLM** | OpenAI API |
| **Database** | Neon (Serverless PostgreSQL) |
| **ORM** | Drizzle ORM |
| **UI Components** | Radix UI + shadcn/ui |

---

## Getting Started

### Prerequisites

- Node.js 18+
- A Clerk account
- A Vapi AI account
- An OpenAI API key
- A Neon PostgreSQL database

### 1. Clone the Repository

```bash
git clone https://github.com/priyanshyou/AI-Medical-Assistant.git
cd AI-Medical-Assistant
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a .env.local file in the root of the project and add the following:

```env
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/dashboard
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/dashboard

# Neon Database
DATABASE_URL=your_neon_postgres_connection_string

# OpenAI
OPENAI_API_KEY=your_openai_api_key

# Vapi AI
NEXT_PUBLIC_VAPI_API_KEY=your_vapi_web_api_key
```

### 4. Push the Database Schema

```bash
npx drizzle-kit push
```

### 5. Run the Development Server

```bash
npm run dev
```

Open http://localhost:3000 in your browser.

---

## Project Structure

```
AI-Medical-Assistant/
├── app/
│   ├── (auth)/              # Clerk sign-in / sign-up pages
│   ├── (routes)/
│   │   └── dashboard/
│   │       ├── _components/ # Dashboard UI components
│   │       ├── medical-agent/
│   │       │   └── [sessionID]/ # Dynamic voice session page
│   │       ├── layout.tsx
│   │       └── page.tsx     # Doctor agent listing
│   ├── _components/         # Shared app-level components
│   ├── api/
│   │   ├── session-chat/    # Save & fetch session transcripts
│   │   ├── suggest-doctor/  # Symptom-to-specialist suggestion
│   │   └── users/           # User management endpoints
│   ├── layout.tsx
│   ├── page.tsx             # Landing / hero page
│   └── provider.tsx         # Global providers (Clerk, etc.)
├── components/
│   ├── hero-section-demo-1.tsx
│   └── ui/                  # shadcn/ui components
├── config/                  # App-level configuration
├── context/                 # React context providers
├── lib/                     # Utility functions & DB client
├── shared/
│   └── list.tsx             # AI doctor agents configuration
├── drizzle.config.ts
├── middleware.ts            # Clerk auth middleware
└── next.config.ts
```

---

## AI Doctor Agents

The app includes 10 specialized AI doctor agents, each configured with a unique voice and clinical focus:

| # | Specialist | Voice | Plan |
|---|---|---|---|
| 1 | General Physician | Will | Free |
| 2 | Pediatrician | Chris | Premium |
| 3 | Dermatologist | Sarge | Premium |
| 4 | Psychologist | Susan | Premium |
| 5 | Nutritionist | Eileen | Premium |
| 6 | Cardiologist | Charlotte | Premium |
| 7 | ENT Specialist | Ayla | Premium |
| 8 | Orthopedic | Aaliyah | Premium |
| 9 | Gynecologist | Hudson | Premium |
| 10 | Dentist | Atlas | Premium |

---

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | /api/users | Create or fetch a user record |
| GET/POST | /api/session-chat | Manage voice session transcripts |
| POST | /api/suggest-doctor | Get AI-based specialist recommendation |

---

## Deployment

The easiest way to deploy this app is with Vercel:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/priyanshyou/AI-Medical-Assistant)

Make sure to add all the environment variables listed above in your Vercel project settings before deploying.

---

## Disclaimer

MedAgent AI is built for informational and educational purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment. Always consult a qualified healthcare provider for medical concerns.

---

## Author

Priyansh — @priyanshyou

---

## License

This project is open-source and available under the MIT License (LICENSE).
