# Medisynn Backend

The API server for **Medisynn**, a healthcare platform with an **AI-powered health assessment**. It handles authentication, email OTP verification, media uploads, and the Gemini-powered health assessment.

The web app lives in a separate repository: **Medisynn-Frontend**.

## Features

- **Authentication** with JWT stored in httpOnly cookies.
- **Email OTP verification**, sent through the Brevo HTTP API.
- **AI health assessment** powered by Google Gemini 2.5 Flash.
- **Media uploads** stored on Cloudinary.
- **MongoDB** (Atlas) for users and health data, with Mongoose.
- **CORS and cookie setup** for the Netlify frontend.

## Tech stack

| Area | Tools |
| --- | --- |
| Runtime and framework | Node.js, Express |
| Database | MongoDB Atlas, Mongoose |
| Auth | JWT, httpOnly cookies |
| AI | Google Gemini 2.5 Flash |
| Email | Brevo HTTP API |
| Media storage | Cloudinary |
| Hosting | Render |

## Getting started

### Prerequisites

- Node.js (LTS)
- npm (comes with Node.js)
- A MongoDB Atlas connection string
- A Google Gemini API key
- A Brevo account (API key and sender)
- A Cloudinary account (cloud name, API key and API secret)

### Clone

```bash
git clone https://github.com/aditya79373/Medisynn-Backend.git
cd Medisynn-Backend
```

### Install and run

```bash
npm install
npm run dev
```

The server starts on the port set in `.env` (default `5000`).

### Environment variables

Create a `.env` file in the project root:

```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
GEMINI_API_KEY=your_gemini_api_key
BREVO_API_KEY=your_brevo_api_key
BREVO_SMTP_USER=your_brevo_sender_login
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
CLIENT_URL=http://localhost:5173
```

| Variable | Purpose |
| --- | --- |
| `PORT` | Port the server runs on |
| `MONGODB_URI` | MongoDB Atlas connection string |
| `JWT_SECRET` | Secret used to sign JWT tokens |
| `GEMINI_API_KEY` | Google Gemini API key for the health assessment |
| `BREVO_API_KEY` | Brevo API key for sending OTP emails |
| `BREVO_SMTP_USER` | Brevo account login used as the email sender |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name |
| `CLOUDINARY_API_KEY` | Cloudinary API key |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret |
| `CLIENT_URL` | Frontend URL (used for CORS and cookies) |

Never commit `.env` files. For production, set `CLIENT_URL` to `https://medisynncare24.netlify.app`.



## Scripts

| Script | What it does |
| --- | --- |
| `npm run dev` | Start the server in development |
| `npm start` | Start the server in production |

## Troubleshooting

- **MongoDB `querySrv` / DNS errors:** some networks (college or hostel Wi-Fi) block DNS SRV lookups used by `mongodb+srv://` URIs. Setting custom DNS servers in Node.js (`dns.setServers([...])`) before connecting fixes this.
- **Cookies or CORS not working:** make sure `CLIENT_URL` exactly matches your frontend URL, with no trailing slash.

## Notes

- Do not commit `.env` files.
- The health assessment gives AI-generated suggestions only. It is **not a substitute for professional medical advice**.
