
# 🧠 Learnato Discussion Forum — Microservice

> **Empower learning through conversation.**  
> A real-time, browser-based **discussion forum** for learners and instructors — enabling questions, answers, and collaborative knowledge-sharing in the **Learnato ecosystem**.  
> Built as a **modular microservice** that integrates seamlessly with e-learning or community platforms.

---

## 🚀 Tech Stack

| Layer | Technology |
|--------|-------------|
| **Frontend** | ⚛️ React (Vite) + 🎨 Tailwind CSS |
| **Backend** | 🟢 Node.js + Express.js |
| **Database** | 🍃 MongoDB (Dockerized) |
| **Realtime Engine** | 🔌 Socket.io |
| **Containerization & Deployment** | 🐳 Docker + Docker Compose |
| **Hosting (optional)** | ☁️ Render (Backend) + ▲ Vercel (Frontend) |

---

## ✨ Key Features (MVP + Stretch Goals)

### ✅ Core Features
- 📝 Create and publish posts *(title, content, optional author)*
- 🔍 Search posts dynamically (title/content)
- 📋 Sort posts by *Newest* or *Top Votes*
- 💬 Reply to posts in real-time
- 🔼 Upvote posts for visibility
- 📱 Responsive, mobile-friendly UI

### 🚀 Stretch Goals (Included)
- 🧑‍🏫 Mark posts as **Answered** (Instructor/Admin action)
- ⚡ Live synchronization via **WebSockets**
- 💬 Real-time replies powered by **Socket.io**

### 🔒 Future Enhancements
- 🔐 Authentication (OAuth / JWT)
- 🧠 AI Assistant (suggest similar questions / summarize threads)
- 📊 Analytics dashboard for educators
- 🧩 LMS (Learning Management System) plug-in microservice

---

## 🧩 Architecture Overview

**Frontend → Backend → Database Flow**

⚛️ **Frontend (React + Vite + TailwindCSS)**  
- Renders UI: post lists, search, live updates  
- Connects to backend via REST APIs & Socket.io  
- Handles user input and upvotes dynamically  

⬇️  

🟢 **Backend (Node.js + Express + Socket.io)**  
- RESTful API endpoints for CRUD operations  
- Socket.io events: `post:created`, `reply:created`, `post:upvoted`, `post:answered`  
- Real-time sync between all connected clients  

⬇️  

🍃 **Database (MongoDB)**  
- Stores posts, replies, and user info  
- Schema: `{ title, content, author, votes, answered, replies[] }`  
- Indexed for fast search and sorting  

---

## 🧪 Quickstart (Docker)

Run the entire stack (frontend + backend + MongoDB) with one command:

```bash
docker compose up --build
````

**Access:**

* 🌐 Frontend → [http://localhost:5173](http://localhost:5173)
* ⚙️ Backend API → [http://localhost:4000/api](http://localhost:4000/api)

---

## 💻 Local Development (Manual Mode)

### Start MongoDB (using Docker)

```bash
docker run -p 27017:27017 -d mongo:7
```

### Backend Setup

```bash
cd backend
cp .env.example .env
npm install
npm run dev
# API runs at http://localhost:4000
```

### Frontend Setup

```bash
cd ../frontend
npm install
npm run dev
# App available at http://localhost:5173
```

---

## 🧠 API Reference

| Method | Endpoint                | Description           |                      |
| ------ | ----------------------- | --------------------- | -------------------- |
| `POST` | `/api/posts`            | Create new post       |                      |
| `GET`  | `/api/posts?sort=votes  | date&q=term`          | List or search posts |
| `GET`  | `/api/posts/:id`        | Fetch single post     |                      |
| `POST` | `/api/posts/:id/reply`  | Add a reply           |                      |
| `POST` | `/api/posts/:id/upvote` | Upvote a post         |                      |
| `POST` | `/api/posts/:id/answer` | Mark post as answered |                      |
| `GET`  | `/api/health`           | Health check endpoint |                      |

### Example Request:

```json
POST /api/posts
{
  "title": "How does Socket.io enable real-time updates?",
  "content": "I'm trying to understand the WebSocket lifecycle...",
  "author": "John Doe"
}
```

---

## ⚙️ Environment Configuration

### Backend (`.env`)

```bash
MONGO_URL=mongodb://mongo:27017/learnato_forum
PORT=4000
CORS_ORIGIN=http://localhost:5173
```

### Frontend (`.env`)

```bash
VITE_API_URL=http://localhost:4000
```

---

## 🧱 Project Structure

```
learnato-forum/
├── backend/
│   ├── src/
│   │   ├── models/
│   │   │   └── Post.js
│   │   ├── routes/
│   │   │   └── posts.js
│   │   └── index.js
│   ├── Dockerfile
│   └── package.json
│
├── frontend/
│   ├── src/components/App.jsx
│   ├── index.html
│   ├── Dockerfile
│   └── vite.config.js
│
├── docker-compose.yml
└── README.md
```

---

## 🌍 Deployment Options

### 🐳 Docker Compose (Recommended)

Run all services (frontend, backend, database) in isolated containers.

```bash
docker compose up --build
```

### ☁️ Render (Backend)

1. Set environment variables:

   ```
   MONGO_URL=<your MongoDB URI>
   PORT=4000
   CORS_ORIGIN=*
   ```
2. Deploy directly from GitHub (auto-build supported).

### ▲ Vercel (Frontend)

* Framework: **Vite**
* Root Directory: `frontend`
* Environment Variable:

  ```
  VITE_API_URL=https://learnato-forum.onrender.com
  ```

---

## 🔮 Future Scope (Hackathon Extensions)

💡 **AI Assistant**

* Suggest similar questions or summarize discussion threads using NLP.
* Recommend relevant resources based on topic keywords.

🔗 **Blockchain Proof-of-Learning**

* Immutable log for verified student contributions.

📊 **Analytics Dashboard**

* Insights into trending questions, engagement rate, and topic heatmaps.

☁️ **Cloud Scalability**

* Kubernetes orchestration for multi-instance scaling.

---

## 🏁 Summary

**Learnato Discussion Forum** is a modular, real-time discussion platform that fosters collaborative learning.
It’s lightweight, containerized, and ready to plug into any educational or community-based ecosystem.

> 💬 *“Knowledge grows by sharing, not saving.” — Let’s empower learning together.*

