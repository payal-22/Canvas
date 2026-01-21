🎨 Real-Time Collaborative Drawing Canvas
A multi-user drawing application where multiple people can draw simultaneously on the same canvas with real-time synchronization.
✨ Features

✅ Real-time collaboration with WebSocket
🎨 Drawing tools: Brush, Eraser, Rectangle, Circle, Line
🌈 Color picker with preset colors
📏 Adjustable brush size (1-20px)
🏠 Room system - multiple isolated canvases
📱 Mobile touch support
💾 Save/Load/Download canvas
👥 See other users online
👆 Real-time cursor tracking
📊 FPS and latency monitoring
↩️ Undo/Redo functionality

🚀 Quick Start
Prerequisites

Node.js 18+
npm

Installation

Clone the repository

bashgit clone <your-repo-url>
cd collaborative-canvas

Install dependencies

bash# Install server dependencies
cd server
npm install

# Install client dependencies
cd ../client
npm install

Run the application

Terminal 1 - Server:
bashcd server
npm run dev
Terminal 2 - Client:
bashcd client
npm start

Open http://localhost:3000 in your browser

🧪 Testing Multi-User

Open http://localhost:3000
Enter a room ID (e.g., "test-room")
Open a new incognito window at http://localhost:3000
Enter the same room ID
Draw in one window - see it appear in the other!

📱 Mobile Testing
On your phone/tablet:
http://YOUR_COMPUTER_IP:3000
(Replace YOUR_COMPUTER_IP with your local IP address)
🎮 How to Use

Join a Room - Enter any room ID to create/join
Select Tool - Choose Brush, Eraser, or Shapes
Pick Color - Use presets or custom color picker
Draw - Click/touch and drag on canvas
Save - Use toolbar buttons to save/load/download

📁 Project Structure
collaborative-canvas/
├── client/              # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Canvas.jsx
│   │   ├── hooks/
│   │   │   └── useWebSocket.js
│   │   ├── App.js
│   │   └── App.css
│   └── package.json
│
├── server/              # Node.js backend
│   ├── src/
│   │   └── server.js
│   └── package.json
│
├── README.md
└── ARCHITECTURE.md
🛠️ Tech Stack
Frontend:

React 18
HTML5 Canvas API
Socket.IO Client
Lucide React (icons)

Backend:

Node.js
Express
Socket.IO
In-memory storage

📊 API Endpoints
HTTP

GET /health - Server health check
GET /rooms - List active rooms

WebSocket Events

join-room - Join a canvas room
draw - Send drawing data
cursor-move - Update cursor position
clear - Clear canvas
save-canvas - Save canvas state

⚙️ Configuration
Server port: Edit server/src/server.js
javascriptconst PORT = process.env.PORT || 5000;
WebSocket URL: Edit client/src/hooks/useWebSocket.js
javascriptconst SERVER_URL = 'http://localhost:5000';
