# Career Co-Pilot 🚀

## AI-Powered Career Guidance & Resume Analysis Platform

An intelligent, full-stack career development platform that uses multiple specialized AI agents to help students and early professionals navigate their career journey. Career Co-Pilot democratizes access to professional career counseling through intelligent automation.

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![PHP](https://img.shields.io/badge/PHP-8.0+-purple.svg)
![Python](https://img.shields.io/badge/Python-3.9+-yellow.svg)
![React](https://img.shields.io/badge/React-18.2-blue.svg)

---

## 📋 Table of Contents

- [Problem Statement](#-problem-statement)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Documentation](#-api-documentation)
- [AI Agent System](#-ai-agent-system)
- [Database Design](#-database-design)
- [Security](#-security)
- [Pages & UI Components](#-pages--ui-components)
- [Deployment](#-deployment)
- [Future Roadmap](#-future-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Problem Statement

Job seekers, especially fresh graduates and career switchers, often struggle with:
- Crafting effective resumes that pass ATS systems
- Preparing for interviews without professional coaching
- Making informed career decisions without guidance
- Identifying skill gaps for their target roles

Traditional career counseling is **expensive and not scalable**, leaving millions without proper career support.

### Target Users

| User Type | Description |
|-----------|-------------|
| **Fresh Graduates** | Students entering the job market for the first time |
| **Career Switchers** | Professionals transitioning to new industries |
| **Job Seekers** | Anyone actively searching for employment |
| **Professionals** | Individuals seeking career advancement guidance |

---

## 🌟 Features

### Core Features

| Feature | Description |
|---------|-------------|
| 🤖 **AI Resume Analyzer** | Analyzes resumes against job descriptions with ATS scoring and improvement suggestions |
| 📊 **Skill Gap Analysis** | Compares current skills to target role requirements with prioritized learning areas |
| 🗺️ **Personalized Learning Roadmap** | Creates customized learning plans with curated resources and milestones |
| 💬 **AI Career Chat** | 24/7 personalized career guidance based on user profile |
| 🎤 **Interview Preparation** | Generates role-specific questions with model answers and feedback |
| 📁 **Project Portfolio Management** | Track projects, get suggestions, and showcase skills |
| 📈 **Job Application Tracker** | Track applications, view statistics, and get insights |
| 📄 **PDF Resume Generation** | Generate professional PDF resumes from your profile |

### Additional Features

- **Career Readiness Score**: Dynamic scoring based on skills, goals, and market requirements
- **Smart Opportunity Matching**: Job recommendations with match percentages
- **Feedback Processing**: Turn rejections into actionable insights for improvement
- **Dark Mode**: Full theme support with CSS variables

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Frontend** | React 18 + TypeScript | User interface & interactions |
| **Frontend** | Tailwind CSS | Modern, responsive styling |
| **Frontend** | Vite | Fast frontend bundling |
| **Backend** | PHP 8.0+ | API Gateway, authentication, CRUD |
| **Backend** | Python 3.9+ + Flask | AI Agent orchestration & processing |
| **AI Integration** | Google Gemini API | NLP & AI responses |
| **AI Integration** | OpenRouter API | Multi-model AI access |
| **Database** | MySQL 8.0 | Data persistence |
| **Server** | Apache (XAMPP) | Local development server |

### Frontend Dependencies

```json
{
  "react": "^18.2.0",
  "react-router-dom": "^6.21.0",
  "axios": "^1.6.2",
  "lucide-react": "^0.294.0",
  "recharts": "^2.10.3",
  "tailwind-merge": "^2.2.0"
}
```

### Python Dependencies

```
flask==3.0.0
flask-cors==4.0.0
python-dotenv==1.0.0
mysql-connector-python==8.2.0
openai>=1.6.0
numpy>=2.0.0
sentence-transformers>=2.2.2
gunicorn==21.2.0
pydantic>=2.5.2
requests>=2.31.0
reportlab>=4.0.0
```

---

## 🏗️ Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                         CLIENT LAYER                                 │
│   Landing │ Resume Analyzer │ Interview Prep │ Career Advice        │
└─────────────────────────────┬───────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                   PHP API LAYER (Router)                             │
│   • Request routing        • JWT Authentication                      │
│   • Input validation       • Response formatting                     │
└─────────────────────────────┬───────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    CONTROLLER LAYER (PHP)                            │
│  AuthCtrl │ ResumeCtrl │ SkillsCtrl │ AgentCtrl │ ProfileCtrl       │
└─────────────────────────────┬───────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                   PYTHON AI AGENTS LAYER                             │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │
│  │Resume Agent │ │ Skill Agent │ │Planner Agent│ │Feedback Agent│   │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘   │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │
│  │Projects Agent│ │Reasoning    │ │      Orchestrator          │   │
│  └─────────────┘ │Agent        │ └─────────────────────────────┘   │
│                  └─────────────┘                                    │
└─────────────────────────────┬───────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    EXTERNAL AI SERVICES                              │
│        Google Gemini API │ OpenRouter API │ Embedding Models         │
└─────────────────────────────┬───────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                       DATABASE LAYER                                 │
│   Users │ Profiles │ Resumes │ Skills │ Projects │ Feedback         │
└─────────────────────────────────────────────────────────────────────┘
```

### API Request/Response Lifecycle

```
1. User Action (e.g., uploads resume)
           │
           ▼
2. React Frontend captures input
           │
           ▼
3. Axios sends request to PHP API
           │
           ▼
4. PHP Router matches endpoint
           │
           ▼
5. Controller validates & processes
           │
           ▼
6. Python Agent called via HTTP (if AI needed)
           │
           ▼
7. AI model generates response
           │
           ▼
8. Response flows back through layers
           │
           ▼
9. React renders results in UI
```

---

## 📁 Project Structure

```
carrer-co-pilot/
├── 📂 frontend/                      # React + TypeScript Frontend
│   ├── src/
│   │   ├── App.tsx                   # Main React app
│   │   ├── main.tsx                  # Entry point
│   │   ├── index.css                 # Global styles
│   │   ├── 📂 components/            # Reusable UI components
│   │   │   ├── ui/
│   │   │   │   ├── Avatar.tsx        # User profile pictures
│   │   │   │   ├── Badge.tsx         # Status indicators
│   │   │   │   ├── Button.tsx        # Buttons
│   │   │   │   ├── Card.tsx          # Content containers
│   │   │   │   ├── Input.tsx         # Form inputs
│   │   │   │   ├── Loading.tsx       # Loading states
│   │   │   │   ├── Modal.tsx         # Dialog overlays
│   │   │   │   ├── Progress.tsx      # Progress bars
│   │   │   │   ├── Skeleton.tsx      # Loading placeholders
│   │   │   │   ├── Tabs.tsx          # Tab navigation
│   │   │   │   ├── Textarea.tsx      # Multi-line input
│   │   │   │   └── Tooltip.tsx       # Hover information
│   │   │   └── index.ts
│   │   ├── 📂 context/               # React contexts
│   │   │   ├── AuthContext.tsx       # Authentication state
│   │   │   └── ThemeContext.tsx      # Theme management
│   │   ├── 📂 layouts/               # Page layouts
│   │   │   └── DashboardLayout.tsx
│   │   ├── 📂 lib/                   # Utility functions
│   │   │   └── utils.ts
│   │   ├── 📂 pages/                 # Page components
│   │   │   ├── LandingPage.tsx
│   │   │   ├── LoginPage.tsx
│   │   │   ├── SignupPage.tsx
│   │   │   ├── OnboardingPage.tsx
│   │   │   ├── DashboardPage.tsx
│   │   │   ├── ProfilePage.tsx
│   │   │   ├── ResumePage.tsx
│   │   │   ├── SkillGapPage.tsx
│   │   │   ├── RoadmapPage.tsx
│   │   │   ├── ProjectsPage.tsx
│   │   │   ├── ApplicationsPage.tsx
│   │   │   ├── ChatPage.tsx
│   │   │   └── FeedbackPage.tsx
│   │   ├── 📂 services/              # API service layer
│   │   │   └── api.ts
│   │   └── 📂 types/                 # TypeScript types
│   │       └── index.ts
│   ├── package.json
│   ├── tailwind.config.js
│   ├── tsconfig.json
│   └── vite.config.ts
│
├── 📂 php-backend/                   # PHP API Gateway
│   ├── index.php                     # Main entry point & router
│   ├── 📂 config/
│   │   └── database.php              # Database configuration
│   ├── 📂 controllers/
│   │   ├── AgentController.php       # AI agent communication
│   │   ├── ApplicationsController.php
│   │   ├── AuthController.php        # Authentication
│   │   ├── FeedbackController.php
│   │   ├── GoalsController.php
│   │   ├── PlansController.php
│   │   ├── ProfileController.php
│   │   ├── ProjectsController.php
│   │   ├── ResumeController.php
│   │   └── SkillsController.php
│   ├── 📂 core/
│   │   ├── Database.php              # PDO wrapper
│   │   ├── JWT.php                   # JWT authentication
│   │   ├── Request.php               # Request handling
│   │   ├── Response.php              # Response formatting
│   │   └── Router.php                # URL routing
│   └── 📂 services/
│       └── AgentService.php          # Python agent integration
│
├── 📂 python-agents/                 # Python Agent Service
│   ├── app.py                        # Flask API entry point
│   ├── config.py                     # Configuration settings
│   ├── database.py                   # Database connection
│   ├── llm_client.py                 # LLM API client
│   ├── orchestrator.py               # Agent orchestration
│   ├── requirements.txt
│   ├── 📂 agents/
│   │   ├── __init__.py
│   │   ├── embedding_agent.py        # Text embeddings
│   │   ├── feedback_agent.py         # Interview feedback
│   │   ├── planner_agent.py          # Career planning
│   │   ├── projects_agent.py         # Project suggestions
│   │   ├── reasoning_agent.py        # Complex reasoning
│   │   ├── resume_agent.py           # Resume analysis
│   │   └── skill_gap_agent.py        # Skill gap analysis
│   ├── 📂 services/
│   │   ├── html_pdf_generator.py     # HTML to PDF
│   │   └── pdf_generator.py          # PDF generation
│   └── 📂 templates/
│       └── resume_template.html      # Resume HTML template
│
├── 📂 database/                      # Database schemas
│   ├── schema.sql                    # Main schema
│   ├── migration_v2.sql              # Skills migration
│   ├── migration_v3.sql              # Goals migration
│   ├── migration_v4_resume.sql       # Resume tables
│   ├── migration_v5_learning_resources.sql
│   ├── migration_v6_projects.sql
│   └── migration_v7_feedback_analysis.sql
│
├── 📂 resumes/                       # Generated resume PDFs
├── PROJECT_ANALYSIS.txt
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **XAMPP** (Apache + MySQL + PHP 8.0+)
- **Python 3.9+**
- **Node.js 18+**
- **Git**

### Step-by-Step Setup

#### 1. Clone the Repository

```bash
cd C:\xampp\htdocs
git clone <repository-url> carrer-co-pilot
cd carrer-co-pilot
```

#### 2. Database Setup

```bash
# Start MySQL in XAMPP Control Panel
# Then import the schema

mysql -u root -p < database/schema.sql
mysql -u root -p career_copilot < database/migration_v2.sql
mysql -u root -p career_copilot < database/migration_v3.sql
mysql -u root -p career_copilot < database/migration_v4_resume.sql
mysql -u root -p career_copilot < database/migration_v5_learning_resources.sql
mysql -u root -p career_copilot < database/migration_v6_projects.sql
mysql -u root -p career_copilot < database/migration_v7_feedback_analysis.sql
```

#### 3. Python Agent Service Setup

```bash
cd python-agents

# Create virtual environment
python -m venv .venv

# Activate virtual environment
# Windows PowerShell:
.venv\Scripts\Activate.ps1
# Windows CMD:
.venv\Scripts\activate.bat
# Linux/Mac:
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Create .env file
cp .env.example .env
# Edit .env with your API keys:
# OPENROUTER_API_KEY=your_api_key
# GEMINI_API_KEY=your_api_key
# DB_HOST=localhost
# DB_NAME=career_copilot
# DB_USER=root
# DB_PASS=

# Start the Python agent server
python app.py
```

#### 4. PHP Backend Setup

```bash
cd php-backend

# Create .env file
cp .env.example .env
# Edit .env with:
# DB_HOST=localhost
# DB_PORT=3306
# DB_NAME=career_copilot
# DB_USER=root
# DB_PASS=
# JWT_SECRET=your-secret-key
# PYTHON_AGENT_URL=http://localhost:8000

# Start Apache in XAMPP Control Panel
# The API will be available at:
# http://localhost/carrer-co-pilot/php-backend/api
```

#### 5. Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env
# Edit .env with:
# VITE_API_URL=http://localhost/carrer-co-pilot/php-backend/api

# Start development server
npm run dev
```

### Access the Application

| Service | URL |
|---------|-----|
| **Frontend** | http://localhost:5173 |
| **PHP API** | http://localhost/carrer-co-pilot/php-backend/api |
| **Python Agents** | http://localhost:8000 |

---

## 📡 API Documentation

### Authentication Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/auth/register` | POST | email, password, name | JWT token |
| `/api/auth/login` | POST | email, password | JWT token |
| `/api/auth/me` | GET | JWT header | User data |

### Profile Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/profile` | GET | JWT header | Profile data |
| `/api/profile` | PUT | Profile JSON | Updated profile |
| `/api/profile/onboarding` | POST | Onboarding data | Profile created |

### Resume Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/resume` | GET | JWT header | Resume data |
| `/api/resume` | POST | Resume JSON | Created resume |
| `/api/resume/analyze` | POST | Resume + job title | AI analysis |
| `/api/resume/generate-pdf` | POST | Resume data | PDF file |

### Skills Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/skills` | GET | JWT header | Skills list |
| `/api/skills/gap-analysis` | POST | Target role | Skill gaps |
| `/api/skills/recommendations` | GET | JWT header | Skill suggestions |

### AI Agent Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/agent/chat` | POST | Message, context | AI response |
| `/api/agent/career-advice` | POST | Profile data | Career guidance |
| `/api/agent/interview-prep` | POST | Job role, level | Interview Q&A |
| `/api/agent/feedback` | POST | Interview response | Feedback |

### Projects Endpoints

| Endpoint | Method | Input | Output |
|----------|--------|-------|--------|
| `/api/projects` | GET | JWT header | Projects list |
| `/api/projects` | POST | Project data | Created project |
| `/api/projects/suggestions` | GET | JWT header | AI suggestions |

---

## 🤖 AI Agent System

The orchestrator coordinates specialized agents, each with domain-specific prompt templates and response parsers.

### Agent Overview

| Agent | Purpose | Key Functions |
|-------|---------|---------------|
| **Reasoning Agent** | Complex reasoning and career analysis | Profile analysis, career path optimization |
| **Resume Agent** | Resume analysis and optimization | ATS scoring, keyword extraction, improvement suggestions |
| **Skill Gap Agent** | Skills assessment | Compare skills, prioritize learning areas |
| **Planner Agent** | Learning roadmap generation | Milestone-based plans, resource curation |
| **Feedback Agent** | Interview feedback processing | Question generation, response evaluation |
| **Projects Agent** | Portfolio management | Project suggestions, skill demonstration |
| **Embedding Agent** | Semantic search | Text embeddings, similarity matching |

### How Resume Analysis Works

```
1. User uploads resume (PDF/DOCX) with target job title
           │
           ▼
2. Python resume_agent extracts text using pdf/docx parsers
           │
           ▼
3. Sends structured prompt to Gemini/OpenRouter API
           │
           ▼
4. AI analyzes content, format, keywords, achievements
           │
           ▼
5. Returns scored breakdown:
   • Overall Score (0-100)
   • Strengths (list)
   • Improvements (list)
   • ATS Compatibility Score
   • Keyword Suggestions
   • Section-by-section feedback
           │
           ▼
6. Response stored in database
           │
           ▼
7. JSON returned to frontend for display
```

---

## 🗄️ Database Design

### Tables Overview

| Table | Purpose |
|-------|---------|
| `users` | User accounts and authentication |
| `user_profiles` | Extended profile information |
| `resumes` | User resume data |
| `resume_sections` | Individual resume sections |
| `skills` | User skills inventory |
| `skill_assessments` | Skill level assessments |
| `career_goals` | User career objectives |
| `learning_plans` | Personalized learning roadmaps |
| `learning_resources` | Educational resources |
| `projects` | Portfolio projects |
| `job_applications` | Job application tracking |
| `feedback_sessions` | Interview feedback data |
| `chat_history` | AI conversation logs |

### Entity Relationships

```
                    ┌─────────────┐
                    │    users    │
                    └──────┬──────┘
                           │
           ┌───────────────┼───────────────┐
           │               │               │
           ▼               ▼               ▼
    ┌──────────────┐ ┌──────────┐ ┌──────────────┐
    │user_profiles │ │  skills  │ │   resumes    │
    └──────────────┘ └──────────┘ └──────┬───────┘
                                         │
                                         ▼
                                  ┌──────────────┐
                                  │resume_sections│
                                  └──────────────┘
           │               │               │
           ▼               ▼               ▼
    ┌──────────────┐ ┌──────────┐ ┌──────────────┐
    │ career_goals │ │ projects │ │applications  │
    └──────┬───────┘ └──────────┘ └──────────────┘
           │
           ▼
    ┌──────────────┐
    │learning_plans│
    └──────┬───────┘
           │
           ▼
    ┌──────────────────┐
    │learning_resources│
    └──────────────────┘
```

---

## 🔒 Security

| Measure | Implementation |
|---------|----------------|
| **Authentication** | JWT tokens with expiration |
| **Password Hashing** | `password_hash()` with BCRYPT |
| **Input Validation** | Type checking, required fields |
| **SQL Injection** | PDO prepared statements |
| **XSS Prevention** | `htmlspecialchars()` on output |
| **CORS** | Configured allowed origins |
| **API Key Protection** | Server-side only, environment variables |

---

## 📱 Pages & UI Components

### Pages

| Page | File | Purpose |
|------|------|---------|
| Landing Page | `LandingPage.tsx` | Hero, features, CTA |
| Login | `LoginPage.tsx` | User authentication |
| Signup | `SignupPage.tsx` | User registration |
| Onboarding | `OnboardingPage.tsx` | 4-step profile setup wizard |
| Dashboard | `DashboardPage.tsx` | Career readiness score, stats |
| Profile | `ProfilePage.tsx` | User profile management |
| Resume | `ResumePage.tsx` | Resume builder & analysis |
| Skill Gap | `SkillGapPage.tsx` | Skills assessment |
| Roadmap | `RoadmapPage.tsx` | Career learning path |
| Projects | `ProjectsPage.tsx` | Portfolio projects |
| Applications | `ApplicationsPage.tsx` | Job application tracker |
| Chat | `ChatPage.tsx` | AI career chat |
| Feedback | `FeedbackPage.tsx` | Interview feedback |

### User Flow

```
┌────────────────┐
│  Landing Page  │
└───────┬────────┘
        │
        ▼
┌───────┴────────┐     ┌────────────────┐
│     Login      │◄───►│     Signup     │
└───────┬────────┘     └────────────────┘
        │
        ▼
┌───────┴────────┐
│   Onboarding   │  (First-time users)
└───────┬────────┘
        │
        ▼
┌────────────────┐
│    Dashboard   │
└───────┬────────┘
        │
        ├──────────┬──────────┬──────────┬──────────┐
        ▼          ▼          ▼          ▼          ▼
   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐
   │ Resume  │ │ Skills  │ │ Roadmap │ │Projects │ │  Chat   │
   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘
```

### Design System

| Element | Value |
|---------|-------|
| **Primary Color** | Indigo (#6366f1) |
| **Accent Color** | Violet (#8b5cf6) |
| **Typography** | Inter font family |
| **Style** | Glassmorphism with subtle gradients |
| **Dark Mode** | Full support with CSS variables |

---

## 🚢 Deployment

### Local Development (XAMPP)

```bash
# 1. Start Apache & MySQL in XAMPP Control Panel

# 2. Start Python agents
cd python-agents
.venv\Scripts\Activate.ps1
python app.py

# 3. Start frontend
cd frontend
npm run dev

# Access:
# - Frontend: http://localhost:5173
# - PHP API: http://localhost/carrer-co-pilot/php-backend/api
# - Python API: http://localhost:8000
```

### Production Deployment

**Option 1: VPS (DigitalOcean/AWS/Linode)**
- Ubuntu 22.04 LTS
- Nginx + PHP-FPM
- MySQL 8.0
- Python with Gunicorn
- Let's Encrypt SSL

**Option 2: Platform as a Service**
- Frontend: Vercel/Netlify
- PHP Backend: Heroku/Railway
- Python Agents: Railway/Render
- Database: PlanetScale/AWS RDS

### Production Checklist

- [ ] Environment variables configured
- [ ] API keys secured (not in code)
- [ ] HTTPS/SSL enabled
- [ ] Database credentials secured
- [ ] Error logging configured
- [ ] Rate limiting enabled
- [ ] CORS properly configured
- [ ] Input validation on all endpoints
- [ ] Backup strategy implemented
- [ ] Monitoring & alerting set up

---

## 🔮 Future Roadmap

### Phase 1: Performance Optimization
- Add Redis for caching AI responses
- Implement response caching headers
- Optimize database queries with indexes
- Add database connection pooling

### Phase 2: Infrastructure Scaling
- Containerize with Docker
- Set up load balancer
- Implement job queues (Redis Queue / RabbitMQ)

### Phase 3: Advanced Features
- Real-time notifications (WebSockets)
- Resume templates marketplace
- Mock interview with voice (WebRTC)
- Mobile application (React Native)
- LinkedIn profile import
- AI-powered cover letter generator

---

## 📊 Project Metrics

| Metric | Value |
|--------|-------|
| Total Files | ~80+ |
| Lines of Code | ~15,000+ |
| PHP Files | ~15 |
| Python Files | ~15 |
| React Components | ~25 |
| API Endpoints | ~30+ |
| Database Tables | ~12 |
| External APIs | 2 (Gemini, OpenRouter) |

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Built with React, TypeScript, Tailwind CSS
- AI powered by Google Gemini & OpenRouter APIs
- Inspired by Linear, Notion, and Vercel design systems
- Icons by Lucide React
- Charts by Recharts

---

## 📝 Resume-Ready Description

### Short Summary
> Career Co-Pilot is a full-stack AI-powered career guidance platform that helps job seekers optimize resumes, identify skill gaps, prepare for interviews, and plan career paths. Built with PHP, Python/Flask, React/TypeScript, and Google Gemini AI, it democratizes access to professional career counseling through intelligent automation.

### ATS Keywords
```
PHP, Python, Flask, React, TypeScript, Tailwind CSS, MySQL, REST API, JWT Authentication,
Google Gemini API, OpenRouter, AI/ML Integration, Full-Stack Development, Multi-Agent Systems,
PDF Generation, Prompt Engineering, Natural Language Processing, Vite, Axios, PDO, CORS,
Career Tech, HR Tech, Resume Parser, API Development, Frontend Development, Backend Development
```

---

<p align="center">
  Made with ❤️ for career seekers everywhere
</p>
