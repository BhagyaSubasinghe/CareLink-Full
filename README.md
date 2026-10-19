# CareLink

CareLink is a healthcare appointment platform with a React frontend and an
Express/MongoDB backend.

## Project structure

- `CareLink-frontend/` - React web application
- `CareLink-backend/` - Express API
- `render.yaml` - Render Blueprint for deploying both services
- `DEPLOYMENT.md` - MongoDB Atlas and Render deployment instructions

## Local development

Install dependencies in each application:

```bash
cd CareLink-backend
npm install

cd ../CareLink-frontend
npm install
```

Copy each `.env.example` to `.env` and provide local values before starting
the applications. Never commit `.env` files or production credentials.

Start the backend and frontend in separate terminals:

```bash
cd CareLink-backend
npm run dev
```

```bash
cd CareLink-frontend
npm start
```

For production deployment, follow [DEPLOYMENT.md](./DEPLOYMENT.md).
