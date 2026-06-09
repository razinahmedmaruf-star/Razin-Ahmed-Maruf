# Razin IPTV - Streaming Platform

A Netflix-style IPTV streaming platform built with React, Node.js, and MongoDB.

## Features

- 🎬 Live TV Channels & Video Streaming
- 👤 User Authentication & Profiles
- ❤️ Favorites & Watchlist
- 🔍 Advanced Search & Filter
- 📱 Responsive Design
- 🎥 HLS Video Player
- 📊 Channel Management
- 🌙 Dark Mode Support

## Tech Stack

**Frontend:**
- React 18+
- TailwindCSS
- Axios
- React Router

**Backend:**
- Node.js & Express
- MongoDB
- JWT Authentication
- bcryptjs

## Project Structure

```
raziniptv/
├── frontend/              # React application
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
├── backend/              # Express API server
│   ├── models/
│   ├── routes/
│   ├── controllers/
│   ├── middleware/
│   ├── server.js
│   └── package.json
├── public/               # Static HTML/CSS files
└── README.md
```

## Installation & Setup

### Prerequisites
- Node.js (v14+)
- MongoDB
- npm or yarn

### Backend Setup

```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret
npm start
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

The application will be available at `http://localhost:3000`

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/profile` - Get user profile

### Channels
- `GET /api/channels` - Get all channels
- `GET /api/channels/:id` - Get channel details
- `POST /api/channels` - Create channel (Admin)
- `PUT /api/channels/:id` - Update channel (Admin)
- `DELETE /api/channels/:id` - Delete channel (Admin)

### Favorites
- `GET /api/favorites` - Get user favorites
- `POST /api/favorites/:channelId` - Add to favorites
- `DELETE /api/favorites/:channelId` - Remove from favorites

## Environment Variables

### Backend (.env)
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/raziniptv
JWT_SECRET=your_jwt_secret_key
NODE_ENV=development
```

### Frontend (.env)
```
REACT_APP_API_URL=http://localhost:5000/api
```

## License

MIT License - Feel free to use this project

## Support

For issues and questions, please create a GitHub issue.
