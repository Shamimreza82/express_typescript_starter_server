🚀 Express + TypeScript Boilerplate (Production Ready)

A clean, scalable, production-ready Express + TypeScript boilerplate with:

⚡ Root-level dist/ compiled folder

🧱 Folder-structured architecture

🛡 Global error handling

🔄 Async handler (no try/catch in controllers)

🌍 CORS, dotenv, morgan logging

📦 Ready for AWS, Vercel, Render, Docker

🚀 Perfect for starting any backend server instantly

📁 Project Structure
project-root/
│
├─ src/
│   ├─ controllers/
│   ├─ routes/
│   ├─ middlewares/
│   ├─ config/
│   ├─ utils/
│   └─ server.ts
│
├─ dist/          <-- Compiled JS files (after build)
├─ .env
├─ tsconfig.json
├─ package.json
└─ README.md

🔧 Installation
1️⃣ Clone the project
git clone https://github.com/YOUR-REPO.git
cd your-project

2️⃣ Install dependencies
npm install

⚙️ Environment Setup

Create a .env file in the project root:

PORT=3000
NODE_ENV=development

🛠 Scripts
Start development server (auto reload)
npm run dev

Build TypeScript → JavaScript (output in /dist)
npm run build

Start production server
npm start

🧩 Included Features
✔ TypeScript support

Strict mode enabled, full Node + Express typings.

✔ Global error handler

Every thrown error is handled cleanly.

✔ Global 404 handler

Undefined routes automatically return a proper JSON 404.

✔ Async route wrapper

No try/catch needed in controllers.

✔ Morgan logging

Request logging enabled in development.

✔ CORS enabled
✔ Clean scalable structure

Controllers, routes, middlewares, config, utils.

✔ Deployment-ready

Build once → deploy anywhere.

🚀 Deployment Guide
📌 Render

Connect GitHub repo

Set Build Command:

npm install && npm run build


Set Start Command:

npm start


Add environment variables in the Render dashboard.

📌 Vercel (Node Server Mode)

Create a vercel.json:

{
  "version": 2,
  "builds": [{ "src": "dist/server.js", "use": "@vercel/node" }],
  "routes": [{ "src": "/(.*)", "dest": "/dist/server.js" }]
}


Run:

npm run build
vercel deploy

📌 AWS EC2
npm install
npm run build
pm2 start dist/server.js

📌 Docker

Use this simple Dockerfile:

FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

EXPOSE 3000
CMD ["npm", "start"]


Build:

docker build -t my-app .


Run:

docker run -p 3000:3000 my-app

📚 API Example
GET /api/hello

Response:

{
  "message": "Hello from universal Express + TypeScript server!"
}

🏗 How to Add New Routes
1️⃣ Create controller

src/controllers/userController.ts

export const getUser = async (req, res) => {
  res.json({ user: "Shamim" });
};

2️⃣ Add route

src/routes/userRoutes.ts

import { Router } from "express";
import { asyncHandler } from "../middlewares/asyncHandler";
import { getUser } from "../controllers/userController";

const router = Router();

router.get("/", asyncHandler(getUser));

export default router;

3️⃣ Register route in server.ts
app.use("/api/users", userRoutes);

🧨 Troubleshooting
❗ “Cannot find module dist/server.js”

Run:

npm run build

❗ Environment variables not loading

Check .env location (must be root).
Ensure dotenv.config() is called in config file.

❤️ Contribute

This boilerplate is made to help developers avoid repeating setup work.
Feel free to improve + submit PRs!

If you want, I can also generate:

✅ A full GitHub repo
✅ .env.example file
✅ Docker Compose support
✅ PM2 ecosystem config

Just tell me!   

Reza 
+8801531297879 (What's app)