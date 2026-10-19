# CareLink live deployment

This repository is configured for Render with MongoDB Atlas.

## 1. Create MongoDB Atlas

Create a database named `carelink`, create a database user, and allow the Render outbound IP range. For a quick initial deployment, Atlas Network Access can use `0.0.0.0/0`; restrict it after confirming the service works.

Copy the Atlas connection string. Do not commit it.

## 2. Deploy on Render

1. Push this repository to GitHub.
2. In Render, choose **New > Blueprint** and select the repository.
3. Render detects `render.yaml` and creates `carelink-api` and `carelink-web`.
4. Set the `MONGO_URI` secret on `carelink-api` to the Atlas connection string.
5. Keep the generated `JWT_SECRET` private.
6. Deploy the blueprint.

The expected URLs are:

- Frontend: `https://carelink-web.onrender.com`
- API: `https://carelink-api.onrender.com`
- Health check: `https://carelink-api.onrender.com/`

If Render assigns different names or URLs, update these values in the Render dashboard and redeploy:

- Backend `FRONTEND_URL`: the exact frontend URL
- Frontend `REACT_APP_API_URL`: the backend URL followed by `/api/v1`

## 3. Verify

Open the API health URL first. It should return JSON containing `CareLink Backend API is running`. Then open the frontend and test registration, login, doctor search, and booking.

The backend must have a reachable MongoDB Atlas database. Local MongoDB and the development memory fallback are not used in production.
