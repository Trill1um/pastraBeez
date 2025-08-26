# PastraBeez Deployment Guide

## Switching Between Development and Deployment

1. Edit the `.env` files in the root, `frontend`, and `backend` folders.
2. Set `VITE_API_URL` to your backend address (local or deployed).
3. For backend, set `PORT` as needed.

## Development
- Run backend: `npm start` or `node server.js` in `/backend`
- Run frontend: `npm run dev` in `/frontend`

## Deployment
- Set `VITE_API_URL` in `.env` files to your deployed backend URL.
- Build frontend: `npm run build` in `/frontend`
- Serve frontend build with a static server or your backend.
- Ensure backend is running and accessible from the deployed frontend.

## .env Example
```
VITE_API_URL=https://your-deployment-url.com
```

## Notes
- Change `.env` values to switch between environments easily.
- For prototyping, you can deploy to services like Vercel, Netlify, or Heroku.
- Make sure CORS is configured on your backend for your deployed frontend URL.
