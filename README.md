# PHARMACY-QUEUE-MANAGEMENT
# Pharmacy Queue Management System

A full-stack web application for managing **pharmacy queues**, employee registrations, and order processing. Built with **React (frontend)** and **Node.js/Express (backend)**, using **MongoDB** for data storage and **Firebase** for authentication.

---

## Features

* **Employee Management**: Register, view, edit, and delete employees.
* **Order Management**: Create, update, and track orders with status (Pending, Completed, Cancelled).
* **Authentication**: Firebase-based login for admins and employees.
* **Queue System**: Daily order numbering with automatic reset at midnight.
* **Reports**: View order history and aggregated statistics by employee (daily, weekly, monthly).
* **Responsive UI**: Bootstrap and Tailwind CSS for mobile-friendly design.
* **Notifications**: In-app notifications for user feedback.

---

## Tech Stack

### Frontend

* **React 18** with **Vite**
* **React Router**
* **Firebase Auth**
* **Axios**
* **Bootstrap 5** and **Tailwind CSS**
* **FontAwesome** and **React Icons**
* **React Toastify**
* **jsPDF**

### Backend

* **Node.js** with Express.js
* **MongoDB** with Mongoose
* **CORS**
* **Dotenv**

### Deployment / Other

* **Firebase**
* **Vercel / Render**

---

## Installation

### Prerequisites

* Node.js (v18+)
* MongoDB (local or Atlas)
* Firebase project with Authentication enabled

### Backend Setup

```bash
cd backend
npm install
```

* Create `.env` in backend:

```
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
```

* Start backend server:

```bash
npm run dev
```

### Frontend Setup

```bash
cd frontend
npm install
```

* Create `.env` in frontend:

```
VITE_REACT_APP_API_BASE_URL=http://localhost:5000
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_firebase_auth_domain
VITE_FIREBASE_PROJECT_ID=your_firebase_project_id
```

* Start frontend:

```bash
npm run dev
```

* Open browser → `http://localhost:5173`

---

## Usage

### User Roles

* **Admin (Ak)**: Manage employees, view all orders, access reports
* **Employee**: View assigned orders, update status

### Routes

* `/employees` → Admin only
* `/pending-order` → Admin pending orders
* `/user` → Employee interface
* `/order-history` → Reports
* `/login` → Login page
* `/register` → Admin can register users

---

## Deployment

### Backend

* Render, Railway, or Vercel
* Set `MONGODB_URI` for production
* Set environment variables

### Frontend

* Build frontend:

```bash
cd frontend
npm run build
```

* Serve `dist` folder on Vercel / Netlify or integrate with backend

### Full-Stack

* Serve frontend via backend (optional)

```js
import path from 'path';
import { fileURLToPath } from 'url';

const __filename = fileURLToPath(import.meta.url);
const __dirname = path.dirname(__filename);
const distPath = path.resolve(__dirname, '../frontend/dist');

app.use(express.static(distPath));
app.get('*', (req, res) => {
  if (req.path.startsWith('/api/')) return res.status(404).end();
  res.sendFile(path.join(distPath, 'index.html'));
});
```

---

## Database Schema

### Employee

* `empID` (String, required, unique)
* `name` (String, required)
* `email` (String, unique)

### Order

* `orderID` (String, required)
* `orderDate` (Date, required)
* `orderTime` (String, required)
* `orderStatus` (Pending / Completed / Cancelled)
* `EmpID` (String, required)

---

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push branch
5. Open a Pull Request

---

## Author

**AravindKumarGS**

---

## License

ISC License

