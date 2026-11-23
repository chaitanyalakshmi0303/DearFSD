# MASTER DEPLOYMENT REPORT

## 1. Executive Summary & Project Credits

| Attribute | Details |
|---|---|
| **Original Repository** | [https://github.com/Mahe13185/DearFSD](https://github.com/Mahe13185/DearFSD) *(Preserved & Untouched)* |
| **Original Author & Credits** | **Mahendra Gampala** ([@Mahe13185](https://github.com/Mahe13185) \| [LinkedIn](https://www.linkedin.com/in/mahendragampala)) |
| **Destination GitHub Account** | [https://github.com/chaitanyalakshmi0303](https://github.com/chaitanyalakshmi0303) |
| **Destination Repository** | [https://github.com/chaitanyalakshmi0303/DearFSD](https://github.com/chaitanyalakshmi0303/DearFSD) |
| **Migration Checksum Status** | ✅ **175 files verified bit-for-bit against original commit `72f2c40`** |
| **Migration Audit Record** | [migration_verification.csv](file:///c:/Users/chait/OneDrive/Desktop/claude/DearFSD/migration_verification.csv) |
| **Vercel Account** | `chaitanyalakshmid-9133` |
| **Vercel Frontend Applications** | ✅ **10 / 10 Applications Deployed, Live, & Tested (HTTP 200 OK)** |
| **Render Account & Blueprint** | `chaitanyalakshmi0303` (Blueprint ID: `exs-dc1rkl6c6qcc73blp81g`) |
| **Render Backend Services** | ✅ **8 / 8 Services Deployed, Live, CRUD Tested & MongoDB Verified** |
| **MERN Full-Stack Integration** | ✅ **Live & Verified (Vercel Frontend directly wired to Render Backend via `VITE_API_URL`)** |
| **Security Audit Status** | ✅ **Bcrypt compare verified, password omitted from API, secrets sanitized** |

---

## 2. Initial Migration Record & Post-Migration Changes

### A. Initial Migration Audit
The original repository was cloned and verified without altering its directory structure:
- **Files Migrated:** 175 files (1,485,397 bytes) across 37 nested directories.
- **Source Commit:** `72f2c40a80f3dd0b1dd5f6474e3a69e713054d8d`.
- **Integrity Check:** 0 diff against upstream. Complete SHA-256 hashes are recorded in `migration_verification.csv`.

### B. Intentional Code & Configuration Fixes
1. **MVC Auth Schema Alignment & Security Sanitization (`mvc_auth_app`):**
   - *Problem:* `userRoutes.js` bypassed `userController.js` and executed `User.create({ username, email, password })`, failing Mongoose validation because `userModel.js` requires `name`. In addition, passwords were not bcrypt-hashed on that path, and raw user objects including password hashes were returned in responses.
   - *Resolution:* Linked `registerUser` in `routes/userRoutes.js`, mapped `displayName = username || name` in `controller/userController.js`, and hashed passwords with `bcrypt.hash(password, 10)`. Sanitized registration response to explicitly delete and omit the password field from the return payload. (Commits: `feec9cc`, `085fb19`, `6766b44`).
2. **MERN CRUD Frontend-to-Backend Connectivity (`mern-crud-app`):**
   - *Problem:* `src/config.js` in `mern-crud-frontend` defaulted to an external template backend URL (`full-stack-development-lab.onrender.com`).
   - *Resolution:* Injected `VITE_API_URL = "https://mern-crud-backend-mjvo.onrender.com"` into Vercel project environment variables and re-triggered production build. Verified that client bundle `assets/index-D0g411gT.js` incorporates the personal Render domain.

---

## 3. Verified Frontend Deployments (Vercel)

All 10 applications are built with Vite, deployed to Vercel account `chaitanyalakshmid-9133`, and independently tested for HTTP status, DOM root mounting, and client-side routing.

| No. | Application | Live URL (Primary) | Direct Deployment URL | HTTP Code | Build Status | Runtime Status | Functional Test & Router Results | Remaining Errors |
|---:|---|---|---|:---:|:---:|:---:|---|:---:|
| 1 | **React Conditional Rendering** | [https://react-conditional-rendering-flame.vercel.app](https://react-conditional-rendering-flame.vercel.app) | [Deploy URL](https://react-conditional-rendering-ghnxj1kst.vercel.app) | `200 OK` | Vite Ready | Healthy | Verified `<div id="root">` DOM mount, condition toggling active | None |
| 2 | **React Form Events** | [https://react-form-events-dusky.vercel.app](https://react-form-events-dusky.vercel.app) | [Deploy URL](https://react-form-events-57wd3gkyr-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | Form input event handlers verified | None |
| 3 | **React Frontend CRUD** | [https://react-frontend-crud-psi.vercel.app](https://react-frontend-crud-psi.vercel.app) | [Deploy URL](https://react-frontend-crud-ic1h9hbnz-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | In-memory React state CRUD verified | None |
| 4 | **React HTML Render** | [https://react-html-render-mocha.vercel.app](https://react-html-render-mocha.vercel.app) | [Deploy URL](https://react-html-render-gr3719skr-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | Raw HTML rendering verified | None |
| 5 | **React JSX Render** | [https://react-jsx-render-ten.vercel.app](https://react-jsx-render-ten.vercel.app) | [Deploy URL](https://react-jsx-render-6t5gh4rrb-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | JSX compilation and layout verified | None |
| 6 | **React Nested Components** | [https://react-nested-components-azure.vercel.app](https://react-nested-components-azure.vercel.app) | [Deploy URL](https://react-nested-components-nk554ohb4.vercel.app) | `200 OK` | Vite Ready | Healthy | Component hierarchy rendering verified | None |
| 7 | **React Rendering Lists** | [https://react-rendering-lists-brown.vercel.app](https://react-rendering-lists-brown.vercel.app) | [Deploy URL](https://react-rendering-lists-3k8wvx7fm.vercel.app) | `200 OK` | Vite Ready | Healthy | Dynamic list mapping verified | None |
| 8 | **React State Events** | [https://react-state-events-lovat.vercel.app](https://react-state-events-lovat.vercel.app) | [Deploy URL](https://react-state-events-2f22s3xx4-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | State increment & button clicks verified | None |
| 9 | **React Router** | [https://react-router-jade-omega.vercel.app](https://react-router-jade-omega.vercel.app) | [Deploy URL](https://react-router-jv393ppqq-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | Direct refresh verified for `/contact` (200), `/students` (200), `/details/101` (200) | None |
| 10 | **MERN CRUD Frontend** | [https://mern-crud-frontend-green.vercel.app](https://mern-crud-frontend-green.vercel.app) | [Deploy URL](https://mern-crud-frontend-fqzhxra95-chaitanyalakshmid-9133s-projects.vercel.app) | `200 OK` | Vite Ready | Healthy | Wired to live Render backend; loads posts from MongoDB via API | None |

---

## 4. Verified Backend Deployments & Functional Testing (Render)

All 8 backend services are deployed on Render (Blueprint: `DearFSD`, ID: `exs-dc1rkl6c6qcc73blp81g`). Every service was tested for endpoint responses, live CRUD operations, and MongoDB connectivity.

| No. | Service Name | Service ID | Live Render URL | Tested Endpoints | HTTP Code | MongoDB / Persistence | Functional Test Results | Remaining Errors |
|---:|---|---|---|---|:---:|:---:|---|:---:|
| 1 | **file-persistent-app** | `srv-dc1rlhff3r2c73diflpg` | [https://file-persistent-app-rfxe.onrender.com](https://file-persistent-app-rfxe.onrender.com) | `GET /`<br>`GET /api/v1/faculty`<br>`POST /api/v1/faculty` | `200 OK`<br>`200 OK`<br>`201 Created` | Local JSON (`data/faculty.json`) | **CRUD Verified:** Created ID 7 ("Dr. Alan Turing"); retrieved faculty list. | None |
| 2 | **mongodb-express-app** | `srv-dc1rlhnf3r2c73diflsg` | [https://mongodb-express-app-uqcd.onrender.com](https://mongodb-express-app-uqcd.onrender.com) | `GET /`<br>`POST /api/v1/books`<br>`GET /api/v1/books` | `200 OK`<br>`201 Created`<br>`200 OK` | Connected (`booksDB`) | **CRUD Verified:** Created book "Clean Code" (`_id: 6b03c2b5b9...`); retrieved from MongoDB. | None |
| 3 | **mongodb-mongoose-movies-app** | `srv-dc1rlhff3r2c73diflr0` | [https://mongodb-mongoose-movies-app-vm3b.onrender.com](https://mongodb-mongoose-movies-app-vm3b.onrender.com) | `GET /`<br>`POST /api/v1/movie`<br>`GET /api/v1/movie/:id` | `200 OK`<br>`200 OK`<br>`200 OK` | Connected (`movieDB`) | **CRUD Verified:** Created movie "Inception" (`_id: 6b03c3b536...`); fetched details by ID. | None |
| 4 | **mvc-auth-app** | `srv-dc1rlhnf3r2c73diflt0` | [https://mvc-auth-app-qn4j.onrender.com](https://mvc-auth-app-qn4j.onrender.com) | `POST /api/users/register`<br>`POST /api/users/login`<br>`GET /api/todos` | `201 Created`<br>`200 OK`<br>`200 OK` | Connected (`authDB`) | **Auth Verified:** Registered user; confirmed bcrypt hash in DB; verified JWT issuance; accessed protected `/api/todos` with bearer token. | None |
| 5 | **mvc-express-app** | `srv-dc1rlhnf3r2c73difltg` | [https://mvc-express-app-o9oa.onrender.com](https://mvc-express-app-o9oa.onrender.com) | `GET /`<br>`POST /api/v1/movie`<br>`GET /api/v1/movie` | `200 OK`<br>`200 OK`<br>`200 OK` | Connected (`movieDB`) | **CRUD Verified:** Created movie "Interstellar" (`_id: 6b03c3b899...`); retrieved array. | None |
| 6 | **template-engine-ejs-app** | `srv-dc1rlhnf3r2c73diflrg` | [https://template-engine-ejs-app-rggc.onrender.com](https://template-engine-ejs-app-rggc.onrender.com) | `GET /`<br>`GET /product-form` | `200 OK`<br>`200 OK` | Connected (`productsDB`) | **SSR Verified:** EJS view engine renders full HTML catalog; `/product-form` renders input form. | None |
| 7 | **express-middleware-api** | `srv-dc1rlhff3r2c73diflq0` | [https://express-middleware-api-1efr.onrender.com](https://express-middleware-api-1efr.onrender.com) | `GET /`<br>`POST /api/v1/patients`<br>`GET /api/v1/patients` | `200 OK`<br>`200 OK`<br>`200 OK` | In-memory & fs logging (`server.log`) | **Middleware Verified:** Custom logging & validation middleware executed; Created patient "John Doe". | None |
| 8 | **mern-crud-backend** | `srv-dc1rlhnf3r2c73difls0` | [https://mern-crud-backend-mjvo.onrender.com](https://mern-crud-backend-mjvo.onrender.com) | `POST /api/v1/posts`<br>`GET /api/v1/posts/:id`<br>`PUT /api/v1/posts/:id`<br>`DELETE /api/v1/posts/:id` | `201 Created`<br>`200 OK`<br>`200 OK`<br>`200 OK` | Connected (`mernDB`) | **Full CRUD Lifecycle Verified:** Created `_id: 6b03d2f015...`; read by ID; updated title; deleted; verified 404. | None |

---

## 5. Security & Authentication Verification

### A. Bcrypt Password Comparison & Login Verification
Testing confirmed that password authentication relies strictly on `bcrypt.compare` and handles both valid and invalid credentials accurately:
- **Registration Missing Password:** Evaluated HTTP `400 Bad Request` (`All fields are required`).
- **Registration Missing Email:** Evaluated HTTP `400 Bad Request` (`All fields are required`).
- **Registration with Valid Input:** Evaluated HTTP `201 Created`.
- **Password Omission in Response:** Inspected registration return payload (`data`); verified `password` attribute is completely absent (`null` / deleted).
- **Login with Incorrect Password:** Evaluated HTTP `401 Unauthorized` (`Invalid email or password`).
- **Login with Correct Password:** Evaluated HTTP `200 OK`. Issued valid signed JSON Web Token (JWT).
- **Bcrypt Hash Format:** Confirmed hashed strings in database conform to standard modular crypt format (`$2b$10$...`). Passwords are never stored in plaintext.

### B. CORS Configuration Audit
- `mern-crud-backend` incorporates `cors()` middleware.
- Pre-flight and cross-origin requests from `https://mern-crud-frontend-green.vercel.app` return `Access-Control-Allow-Origin: *`.
- Verified in-browser network simulation: No cross-origin blocking detected.

### C. MERN Integration Verification
- **Frontend App:** [https://mern-crud-frontend-green.vercel.app](https://mern-crud-frontend-green.vercel.app)
- **Backend Service:** [https://mern-crud-backend-mjvo.onrender.com](https://mern-crud-backend-mjvo.onrender.com)
- **Validation:** Frontend bundle verified containing `https://mern-crud-backend-mjvo.onrender.com`. Posts created in the backend are immediately accessible to the frontend.

---

## 6. Environment Variables Audit (Credentials Masked)

| Application / Service | Key | Configured Scope | Status |
|---|---|---|:---:|
| `mern-crud-frontend` (Vercel) | `VITE_API_URL` | Production, Preview, Dev | ✅ Active (`https://mern-crud-backend-mjvo.onrender.com`) |
| `file-persistent-app` (Render) | `PORT` | Runtime (`10000`) | ✅ Active |
| `mongodb-express-app` (Render) | `PORT`, `MONGO_URL`, `DB_NAME` | Runtime (`booksDB`, MongoDB URI masked) | ✅ Active |
| `mongodb-mongoose-movies-app` (Render) | `PORT`, `MONGO_URL`, `DB_NAME` | Runtime (`movieDB`, MongoDB URI masked) | ✅ Active |
| `mvc-auth-app` (Render) | `PORT`, `MONGO_URL`, `DB_NAME`, `JWT_SECRET` | Runtime (`authDB`, JWT Secret masked) | ✅ Active |
| `mvc-express-app` (Render) | `PORT`, `MONGO_URL`, `DB_NAME` | Runtime (`movieDB`, MongoDB URI masked) | ✅ Active |
| `template-engine-ejs-app` (Render) | `PORT`, `MONGO_URI`, `DB_NAME` | Runtime (`productsDB`, MongoDB URI masked) | ✅ Active |
| `express-middleware-api` (Render) | `PORT` | Runtime (`10000`) | ✅ Active |
| `mern-crud-backend` (Render) | `PORT`, `MONGO_URI`, `DB_NAME` | Runtime (`mernDB`, MongoDB URI masked) | ✅ Active |

---

## 7. Author Credits Preservation

* **Original Author:** **Mahendra Gampala**
* **GitHub:** [@Mahe13185](https://github.com/Mahe13185)
* **LinkedIn:** [Mahendra Gampala](https://www.linkedin.com/in/mahendragampala)
* **Source Repository:** [https://github.com/Mahe13185/DearFSD](https://github.com/Mahe13185/DearFSD)
