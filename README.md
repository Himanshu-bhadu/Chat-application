# 💬 ChatApp — Real-Time Chat & Video Calling

<div align="center">

![ChatApp Banner](https://img.shields.io/badge/ChatApp-Real--Time%20Communication-blue?style=for-the-badge&logo=socket.io)

[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?style=flat-square&logo=node.js)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb)](https://mongodb.com/)
[![Socket.io](https://img.shields.io/badge/Socket.io-Real--Time-010101?style=flat-square&logo=socket.io)](https://socket.io/)
[![WebRTC](https://img.shields.io/badge/WebRTC-Video%20Calls-333333?style=flat-square&logo=webrtc)](https://webrtc.org/)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-Styling-06B6D4?style=flat-square&logo=tailwindcss)](https://tailwindcss.com/)

**A full-stack real-time chat application with peer-to-peer video calling, connection management, and privacy controls.**

[Live Demo](#) · [Report Bug](#) · [Request Feature](#)

</div>

---

## 📸 Screenshots

<div align="center">

| Chat Interface | Video Call | Mobile View |
|:-:|:-:|:-:|
<img src="https://github.com/user-attachments/assets/6b5f8f88-388c-4896-80cb-d9afb8f160fa" style="max-width:100%; height:auto; border-radius:8px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);" alt="Chat View Alpha" /><br/><br/>
<img src="https://github.com/user-attachments/assets/48b17161-de4c-4896-98ba-2143dab08912" style="max-width:100%; height:auto; border-radius:8px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);" alt="Chat View Beta" /> | 
<img src="https://github.com/user-attachments/assets/aa4733c6-298b-422a-8403-b437ccd9054f" style="max-width:100%; height:auto; border-radius:8px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);" alt="Video Session" /> |
<img src="https://github.com/user-attachments/assets/8195368a-ef21-451f-a15e-7891cfcb3714" style="max-width:260px; width:100%; height:auto; border-radius:8px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1);" alt="Mobile Shell View" /> |
 |

</div>

> 💡 Replace the placeholder images above with actual screenshots of your app.

---

## ✨ Features

### 💬 Real-Time Messaging
- Instant message delivery using **Socket.io** WebSockets
- Messages sync across devices in real time
- Per-connection **chat history toggle** — each user independently controls whether their chat history is saved

### 📹 Peer-to-Peer Video Calling
- **WebRTC**-powered video calls — video streams directly between browsers, zero server load
- STUN/TURN relay servers for reliable connectivity across different networks
- Picture-in-picture local video preview
- Mute audio / toggle camera on the fly
- Incoming call notifications with accept/reject

### 🔐 Authentication & Security
- JWT-based authentication stored in **httpOnly cookies**
- Secure password hashing with **bcrypt**
- Change password from within the app
- Full account deletion with confirmation flow

### 👥 Connection System
- Send connection requests by username
- Accept or decline incoming requests
- Remove connections (wipes chat history)
- Real-time notifications for new requests and accepted connections

### 🌐 Online Presence
- Live **online/offline** status indicators
- **Last seen** timestamps with human-readable format (e.g. "2m ago", "3h ago")

### 🎨 UI/UX
- **Dark/Light mode** toggle with smooth transitions
- Fully **responsive** — works on mobile, tablet, and desktop
- Clean minimal design with Tailwind CSS
- Smooth animations and micro-interactions

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| **React 18** | UI framework |
| **Vite** | Build tool & dev server |
| **Tailwind CSS** | Styling |
| **Socket.io Client** | Real-time communication |
| **WebRTC** | Peer-to-peer video calls |
| **Axios** | HTTP requests |
| **React Hot Toast** | Notifications |
| **React Icons** | Icon library |

### Backend
| Technology | Purpose |
|---|---|
| **Node.js + Express** | REST API server |
| **Socket.io** | WebSocket signaling server |
| **MongoDB + Mongoose** | Database |
| **JWT** | Authentication tokens |
| **bcryptjs** | Password hashing |
| **cookie-parser** | Cookie management |

### Infrastructure
| Service | Purpose |
|---|---|
| **Metered TURN** | WebRTC relay for cross-network video calls |
| **MongoDB Atlas** | Cloud database |
| **Render** | Backend hosting |
| **Vercel** | Frontend hosting |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                    CLIENT (React)                    │
│                                                      │
│   ┌──────────┐   ┌──────────┐   ┌───────────────┐  │
│   │ Chat UI  │   │ Video UI │   │ Auth / Sidebar │  │
│   └────┬─────┘   └────┬─────┘   └───────┬───────┘  │
│        │              │                  │           │
│   Socket.io      WebRTC P2P          REST API       │
└───────┬──────────────────────────────────┬──────────┘
        │                                  │
        ▼                                  ▼
┌───────────────┐                 ┌────────────────┐
│  Socket.io    │                 │  Express REST  │
│  Server       │                 │  API Server    │
│               │                 │                │
│ • Signaling   │                 │ • Auth routes  │
│ • Messaging   │                 │ • Chat routes  │
│ • Presence    │                 │ • Request      │
│ • Relay ICE   │                 │   routes       │
└───────┬───────┘                 └───────┬────────┘
        │                                 │
        └──────────────┬──────────────────┘
                       ▼
              ┌────────────────┐
              │  MongoDB Atlas │
              │                │
              │ • Users        │
              │ • Messages     │
              │ • Connections  │
              └────────────────┘

        WebRTC P2P Stream (after signaling):
        Browser A ←————————————————→ Browser B
                  (via TURN if needed)
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js v18+
- MongoDB Atlas account (or local MongoDB)
- Metered.ca account (for TURN servers — free tier works)

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/chat-application.git
cd chat-application
```

### 2. Setup the Backend

```bash
cd Backend
npm install
```

Create a `.env` file in the `Backend` folder:

```env
PORT=5000
MONGO_URI=your_mongodb_atlas_connection_string
JWT_SECRET=your_jwt_secret_key
CLIENT_URL=http://localhost:5173
```

Start the backend:

```bash
node server.js
```

### 3. Setup the Frontend

```bash
cd frontend
npm install
```

Create a `.env` file in the `frontend` folder:

```env
VITE_BACKEND_URL=http://localhost:5000
VITE_TURN_USERNAME=your_metered_username
VITE_TURN_CREDENTIAL=your_metered_password
```

Start the frontend:

```bash
npm run dev
```

### 4. Open the app

Visit `http://localhost:5173` in your browser. Open a second tab or incognito window to test real-time features between two users.

---

## 📁 Project Structure

```
chat-application/
│
├── Backend/
│   ├── config/
│   │   └── db.js                  # MongoDB connection
│   ├── controllers/
│   │   ├── authController.js      # Login, register, logout
│   │   ├── chatController.js      # Messages, history toggle
│   │   └── reqController.js       # Connection requests
│   ├── middleware/
│   │   └── authMiddleware.js      # JWT verification
│   ├── models/
│   │   ├── User.js                # User schema
│   │   ├── Message.js             # Message schema
│   │   └── Connection.js          # Connection schema
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── chatRoutes.js
│   │   └── reqRoutes.js
│   └── server.js                  # Express + Socket.io server
│
└── frontend/
    └── src/
        ├── components/
        │   ├── auth/
        │   │   ├── LoginForm.jsx
        │   │   └── RegisterForm.jsx
        │   ├── common/
        │   │   └── Input.jsx
        │   └── dashboard/
        │       ├── Sidebar.jsx
        │       ├── ChatView.jsx
        │       ├── VideoCallModal.jsx
        │       ├── SendRequestView.jsx
        │       ├── AcceptRequestsView.jsx
        │       ├── ChangePasswordView.jsx
        │       └── DefaultView.jsx
        ├── context/
        │   ├── AuthContext.jsx
        │   └── ThemeContext.jsx
        ├── pages/
        │   ├── DashboardPage.jsx
        │   └── WelcomePage.jsx
        ├── services/
        │   └── api.js
        └── main.jsx
```

---

## 🔌 WebRTC Video Call Flow

```
Caller                    Server (Socket.io)              Receiver
  │                              │                            │
  │──── call-user (offer) ──────►│                            │
  │                              │──── incoming-call ────────►│
  │                              │                            │
  │                              │◄─── answer-call ───────────│
  │◄─── call-accepted ───────────│                            │
  │                              │                            │
  │◄════ ICE candidates ════════►│◄════ ICE candidates ══════►│
  │                              │                            │
  │◄══════════════ Direct P2P Video Stream ══════════════════►│
                        (via TURN relay if needed)
```

---

## 🌐 Deployment

### Backend (Render)
1. Push your code to GitHub
2. Create a new **Web Service** on Render
3. Set environment variables in Render dashboard
4. Deploy

### Frontend (Vercel)
1. Import your GitHub repo on Vercel
2. Set the `VITE_BACKEND_URL` environment variable to your Render backend URL
3. Deploy

> ⚠️ **Important:** For cross-domain cookies to work (Vercel → Render), ensure your login cookie is set with `sameSite: 'None'` and `secure: true` in your backend.

---

## 🤝 Contributing

This is a personal project built for learning and portfolio purposes. Feel free to fork it and build on top of it!

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 👨‍💻 Authors

Built with ❤️ by **[Himanshu Bhadu]** and **[Bhawanjeet]**

- GitHub: [@himanshubhadu](https://github.com/Himanshu-bhadu)
- GitHub: [@bhawanjeet04](https://github.com/Bhawanjeet04)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<div align="center">

**If you found this project helpful, please give it a ⭐ on GitHub!**

</div>
