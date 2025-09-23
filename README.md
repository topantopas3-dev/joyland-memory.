# Joyland Memory System (UID: 2Z427W)

A memory storage system for **Joyland.ai roleplay**, dedicated to user **UID: 2Z427W**.  
This service keeps character memory alive for **7 days** since last access, with options for persistence.

---

## ✨ Features
- Save character profiles, story progress, and roleplay notes.
- Retrieve memory data via simple API endpoints.
- Automatic **7-day TTL** (extended on access using `touch`).
- Supports permanent storage with `persistent=true`.
- Optional daily backup to JSON files.

---

## 🚀 Usage

### 1. Save Character Memory
POST /memory/user:2Z427W:char:aizen
Content-Type: application/json

{
"content": {
"bio": "Aizen Uzunami, a wandering shinobi with a terminal illness",
"status": "Alive",
"rank": "SSS"
}
}POST /memory/user:2Z427W:char:aizen
Content-Type: application/json

{
"content": {
"bio": "Aizen Uzunami, a wandering shinobi with a terminal illness",
"status": "Alive",
"rank": "SSS"
}
}
### 2. Get Character Memory
GET /memory/user:2Z427W:char:aizen
### 3. Extend TTL (reset memory to 7 days)
POST /memory/user:2Z427W:char:aizen/touch
### 4. Delete Character Memory
DELETE /memory/user:2Z427W:char:aizen
---

## ⚙️ Configuration

Create a `.env` file in the project root:

PORT=3000
MONGO_URI=your-mongodb-uri-here
REDIS_URL=your-redis-uri-here
- **PORT** → App port (default: 3000).  
- **MONGO_URI** → Free MongoDB Atlas cluster URI.  
- **REDIS_URL** → Free Redis Cloud URI.  

---

## 📦 Deployment

You can deploy for free on:
- [Railway](https://railway.app)  
- [Render](https://render.com)  
- [Heroku](https://heroku.com)  

Steps:
1. Push this repo to GitHub.  
2. Connect your repo to one of the hosting platforms above.  
3. Add the required environment variables (`MONGO_URI`, `REDIS_URL`).  
4. Start the service (`npm start`).  

After deployment, you’ll get a public API URL like:  
https://joyland-memory.up.railway.app/memory/user:2Z427W:char:aizen
---

## 📌 Notes
- Use this key format:  
user:2Z427W:char:<characterName>- Example keys for multiple characters:  
- `user:2Z427W:char:aizen`  
- `user:2Z427W:char:uzunami`  
- `user:2Z427W:char:kurokawa`  
- To keep history lightweight, store summaries in Redis and full logs in MongoDB.  
- Run `backupJob.js` to export daily memory snapshots into JSON files.

---

## 👤 Owner
- **UID:** 2Z427W  
- **Platform:** Joyland.ai  
