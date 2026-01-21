# Real-Time Collaborative Drawing Canvas

A real-time multi-user drawing application where multiple users can draw simultaneously on a shared canvas using WebSockets.

---

## 📋 What This Does

- Multiple people can draw on the same canvas at the same time
- See other users' cursors and drawings in real-time
- Works on desktop and mobile (touch support)
- Different rooms for different groups
- Save, load, and download your drawings

---

## 🚀 Setup Instructions

### Prerequisites
- Node.js (v16 or higher)
- npm (comes with Node.js)

### Step 1: Install and Run Backend

```bash
cd server
npm install
npm start
```

The server will start at `http://localhost:5000`

### Step 2: Install and Run Frontend

Open a **new terminal window** and run:

```bash
cd client
npm install
npm start
```

The app will open at `http://localhost:3000`

---

## 🧪 How to Test with Multiple Users

### Option 1: Same Computer
1. Open `http://localhost:3000` in Chrome
2. Enter your name: **Alice**
3. Enter room ID: **test-room**
4. Click "Join Room"
5. Open `http://localhost:3000` in **Firefox** (or incognito Chrome)
6. Enter your name: **Bob**
7. Enter room ID: **test-room** (same as Alice)
8. Click "Join Room"
9. Draw in one window → it appears in the other instantly!

### Option 2: Different Computers (Same WiFi)
1. Find your computer's IP address:
   - Windows: Run `ipconfig` in CMD, look for IPv4 Address
   - Mac/Linux: Run `ifconfig` or `ip addr`, look for inet address
2. On Computer 1: Open `http://YOUR-IP:3000`
3. On Computer 2: Open `http://YOUR-IP:3000`
4. Both join the same room ID

---

## 🎨 Features

### Drawing Tools
- **Brush** - Freehand drawing
- **Eraser** - Remove parts of drawing
- **Line** - Draw straight lines
- **Rectangle** - Draw rectangles
- **Circle** - Draw circles
- **Triangle** - Draw triangles
- **Arrow** - Draw arrows
- **Star** - Draw stars

### Other Features
- **Text Tool** - Add text anywhere
- **Image Upload** - Upload and place images (max 2MB)
- **Colors** - 10 preset colors + custom color picker
- **Undo/Redo** - Fix mistakes (keeps last 50 actions)
- **Save/Load** - Save to browser storage
- **Download** - Export as PNG image
- **User Cursors** - See where others are drawing

---

## 🐛 Known Limitations & Bugs

### Performance Issues
1. **Slow with 10+ users** - Too many drawing events at once
2. **Large images lag** - Keep images under 1MB for best performance
3. **Undo/redo only works locally** - Doesn't sync to other users

### Missing Features
1. **No authentication** - Anyone can join any room
2. **Drawings don't persist** - Refresh = lose everything (except saved to localStorage)
3. **Can't edit shapes** - Once drawn, can't move or resize
4. **No layers** - Everything on one layer

### Known Bugs
1. **Mobile eraser** - Sometimes doesn't work on first touch (touch again)
2. **Very long text** - Might go off-canvas
3. **Slow internet** - Drawings might appear delayed
4. **Room cleanup** - Empty rooms stay in server memory until restart

### What Would Break It
- Uploading 10MB images
- 50+ users in one room
- Drawing while disconnected (lost forever)
- Special characters in room names might cause issues

---

## ⏱️ Time Spent on Project

**Total Time: ~12-15 hours**

Breakdown:
- **Basic canvas setup** - 2 hours
- **WebSocket integration** - 3 hours
- **Drawing tools (shapes, text, images)** - 4 hours
- **Bug fixes and testing** - 2 hours
- **UI/UX improvements** - 2 hours
- **Documentation** - 1 hour

---

## 🏗️ Project Structure

```
collaborative-canvas/
├── client/                  # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   └── Canvas.jsx   # Main drawing component
│   │   ├── hooks/
│   │   │   └── useWebSocket.js  # WebSocket logic
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
│
└── server/                  # Node.js backend
    ├── src/
    │   └── server.js        # Express + Socket.IO server
    └── package.json
```

---

## 🔧 How It Works (Simple Explanation)

### 1. WebSocket Connection
- When you join a room, your browser connects to the server via WebSocket
- WebSocket = like a phone call (stays connected, instant messages both ways)
- Regular HTTP = like sending letters (request → response → close)

### 2. Drawing Process
```
You draw a line:
  ↓
Browser draws it on your canvas (instant!)
  ↓
Browser sends coordinates to server
  ↓
Server broadcasts to all other users in room
  ↓
Their browsers draw the same line
```

### 3. Room System
- Server keeps a list of rooms (like chat rooms)
- Each room has its own users and drawing history
- Room "abc123" can't see room "xyz789"

---

## 📱 Browser Support

✅ **Works on:**
- Chrome (Desktop & Mobile)
- Firefox (Desktop & Mobile)
- Safari (Desktop & Mobile)
- Edge

❌ **Might not work:**
- Internet Explorer (too old)
- Very old Android browsers

---

## 🆘 Troubleshooting

### "Cannot find module" error
```bash
# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### Server won't start
- Check if port 5000 is already in use
- Change port in `server/src/server.js`: `const PORT = 5001;`

### Client won't connect to server
- Make sure server is running first
- Check browser console for errors (F12)
- Verify `SERVER_URL` in client code matches server address

### Drawing doesn't sync
- Check both users are in the **same room ID**
- Look at connection status (green = connected, red = disconnected)
- Try refreshing both browsers

### Images won't upload
- Check file size (must be under 2MB)
- Make sure it's an image file (jpg, png, gif)

---

## 🎯 What I Learned

1. **WebSockets are powerful** - Real-time features need persistent connections
2. **Canvas API is tricky** - Coordinate systems, scaling, touch events
3. **Performance matters** - Sending 100 events/second crashes things
4. **Error handling is crucial** - Users do unexpected things!
5. **Testing is hard** - Need multiple browsers/devices to test properly

---

## 🚀 Future Improvements (If I Had More Time)

1. **Database** - Save drawings permanently (MongoDB/PostgreSQL)
2. **Better undo/redo** - Sync across all users
3. **Layers** - Multiple drawing layers
4. **Shape editing** - Move, resize, delete shapes after drawing
5. **Chat** - Text chat while drawing
6. **User authentication** - Secure rooms with passwords
7. **Performance** - Handle 100+ concurrent users
8. **Mobile app** - Native iOS/Android apps
9. **AI features** - Auto-complete drawings, suggestions
10. **Export options** - SVG, PDF, different formats

---

## 📄 License

This is a student project. Free to use and modify.

---

## 👤 Contact

If something doesn't work, check:
1. Console for errors (F12 → Console tab)
2. Server terminal for error messages
3. Both server AND client are running

**Made with ❤️ as a learning project**
