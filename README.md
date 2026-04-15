# DBs — POS System (Frontend + Backend + Electron)

[![React](https://img.shields.io/badge/React-19.1-61DAFB.svg?logo=react)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.1-06B6D4.svg?logo=tailwind-css)](https://tailwindcss.com/)
[![daisyUI](https://img.shields.io/badge/daisyUI-5.0-FF7B00)](https://daisyui.com/)

Point of Sale (POS) system with a React (Vite) frontend and a Node.js (Express) backend.  
The frontend also includes Electron integration for desktop usage.

![POS Dashboard Preview](https://raw.githubusercontent.com/Ahmadkhan12345566/posb/main/frontend/public/screenshot.png)

## Features

- **POS & Checkout**
  - Product selection, cart management, and invoice/receipt flow.
- **Inventory**
  - Products, categories, brands, units, and stock management.
- **Sales & Purchases**
  - Sales, purchases, suppliers, and invoices.
- **Reports**
  - Sales report, purchase report, customer report, customer due report.
- **Multi-page App**
  - Frontend routes for dashboard, POS, products, categories, brands, units, customers, suppliers, etc.

## Repository

Clone this repository:

```bash
git clone https://github.com/abdulbasit56/DBs.git
cd DBs
```

## Installation & Running

> This repo contains two apps: `backend/` and `frontend/`.

### 1) Backend (Express)

```bash
cd backend
npm install
npm run dev
```

### 2) Frontend (Vite + React)

In another terminal:

```bash
cd frontend
npm install
npm run dev -- --host
```

## Technology Stack

### Frontend
- **React** (Vite)
- **react-router-dom**
- **Tailwind CSS** (+ `@tailwindcss/vite`)
- **daisyUI**
- **MUI (Material UI)** (`@mui/material`, `@mui/icons-material`, `@mui/x-data-grid`)
- **@tanstack/react-table**
- **jsPDF** + **xlsx** (exports)
- **Electron integration** (`electron.js`, `preload.js`)

### Backend
- **Node.js** + **Express**
- **Sequelize** (ORM)
- **MongoDB**
- **jsonwebtoken**, **bcrypt**
- **multer** (uploads)
- **express-session**
- **dotenv**, **cors**

## Project Structure

```text
DBs/
├── backend/
│   ├── .env
│   ├── package.json
│   └── src/
│       ├── config/
│       ├── middleware/
│       ├── models/
│       ├── routes/
│       ├── services/
│       ├── utils/
│       ├── index.js
│       ├── initialData.js
│       └── seed.js
├── frontend/
│   ├── build/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── context/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── electron.js
│   ├── preload.js
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
└── README.md
```

## Key Frontend Routes / Pages (from `frontend/src/App.jsx`)

- Dashboard: `/`
- POS: `/pos`
- Products: `/products`, add product: `/add-product`
- Categories: `/categories`, add: `/add-category`
- Brands: `/brands`, add: `/add-brand`
- Units: `/units`, add: `/add-unit`
- Customers: `/customers`, add: `/add-customer`
- Suppliers: `/suppliers`, add: `/add-supplier`
- Invoices: `/invoices`
- Sales: `/sales`, add: `/add-sale`, return: `/sales-return`
- Purchases: `/purchases`, add: `/add-purchase`
- Reports: `/sales-report`, `/purchase-report`, `/customer-report`, `/customer-due-report`
- Auth: `/signin`, `/signup`

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

## License

MIT License - see [LICENSE](LICENSE) for details.