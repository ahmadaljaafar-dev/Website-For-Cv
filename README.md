# Ahmad Sami Aljaafar — Full-Stack Portfolio & Interactive CV

A cinematic, full-stack portfolio and interactive CV for **Ahmad Sami Aljaafar** (Full-Stack Developer & Automation Engineer).

Built with **Next.js 14 (App Router)**, **TypeScript**, **Tailwind CSS**, **React Three Fiber (Three.js)**, **PostgreSQL** (with zero-config fallback), and **NextAuth**.

---

## Key Features

1. **Cinematic 3D Stack Visual**
   - Signature 3D visualization representing a 3-tier architecture: **User Interface**, **API & Automation**, and **Database**.
   - An emissive electric-blue pulse travels between layers illustrating request/response cycles.
   - Interactive pointer tilt response and scroll separation effect.
   - High-performance SVG fallback for mobile devices and users who prefer reduced motion.

2. **Interactive n8n Automation Demo**
   - Simulated lead capture and ticket provisioning pipeline.
   - Visitors can customize sample inquiry inputs and click **"Run Demo"**.
   - 4-stage pipeline animation: `Form Submission` &rarr; `Validate Details` &rarr; `Create Task` &rarr; `Notify Team`.
   - Real-time payload inspector showing formatted JSON input and output at each node.
   - Labeled clearly as a client-side simulation.

3. **Filterable Portfolio Showcase**
   - Filter projects dynamically by technical competencies (Next.js, TypeScript, n8n, etc.).
   - Cards display problem statement, personal contribution, tech badges, and GitHub/Live Demo links.
   - Unpublished projects remain hidden from public view.

4. **Working Contact Form & Rate Limiting**
   - Fully validated contact form with real-time feedback (success, error, and loading states).
   - Server-side Zod validation and IP-based in-memory rate limiting to prevent spam.
   - Clickable links for phone (`tel:+96171085511`), email (`ahmato-123@hotmail.com`), and WhatsApp.

5. **Printable CV View (PDF)**
   - Text-based, clean, high-contrast print layout designed for recruiters and ATS.
   - Triggered via the **"Print / Save CV"** button in navigation/footer or standard `Ctrl + P` / `Cmd + P`.

6. **Protected Admin Management Panel (`/admin`)**
   - Authenticated via NextAuth JWT session and bcrypt password verification.
   - **Dashboard**: Live counts for total projects, unread inquiries, and published work.
   - **Projects**: Create, edit, delete, and instantly toggle publish/draft status.
   - **Inquiries**: Review incoming client messages, read timestamps, and mark as read.
   - **Profile Editor**: Edit bio, headline, email, and phone dynamically.

---

## Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript (strict mode)
- **Styling**: Tailwind CSS (dark graphite `#1a1a1a`, warm white `#f5f5f0`, electric blue `#2563eb` & `#00d2ff`)
- **3D Graphics**: Three.js, `@react-three/fiber`, `@react-three/drei`
- **Database**: PostgreSQL (via `pg` pool) + resilient local file store fallback (`data/db.json`)
- **Authentication**: NextAuth.js (Credentials provider with bcryptjs)
- **Validation**: Zod

---

## Quick Start & Setup

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure Environment
Copy the example environment file:
```bash
cp .env.example .env
```
Default `.env` settings:
```env
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/portfolio
NEXTAUTH_SECRET=ahmad-portfolio-secure-jwt-secret-key-32chars-min
NEXTAUTH_URL=http://localhost:3000

ADMIN_EMAIL=ahmato-123@hotmail.com
ADMIN_PASSWORD_HASH=$2a$10$LXymTXJ07A9YlQrAhBFdf.NDwmnfyvAd/1ISPYsfSqVEODTOHcWj.
RATE_LIMIT_MAX=10
```
> **Default Admin Credentials**:
> - Email: `ahmato-123@hotmail.com`
> - Password: `admin123`

### 3. Database Migrations (Optional)
If running a local PostgreSQL instance:
```bash
npm run migrate
```
*Note: If PostgreSQL is not active, the application automatically and seamlessly initializes using `data/db.json` so you can test all features immediately without configuring a database server.*

### 4. Run the Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) to view the public portfolio.  
Access [http://localhost:3000/admin](http://localhost:3000/admin) to log into the admin dashboard.

---

## Verification Checklist

1. **Hero & 3D Layering**: Check desktop 3D stack tilt and scroll separation. Verify static illustration appears on mobile screens (< 768px).
2. **Interactive Automation**: On the home page, scroll to `#demo`, enter custom values, and click **"Run Automation Demo"**. Watch each stage turn green and inspect node inputs and outputs.
3. **Contact Submission**: Scroll to `#contact`, enter a test message, and submit. You will receive an instant success confirmation.
4. **Admin Dashboard**:
   - Go to `/admin` and log in with `ahmato-123@hotmail.com` / `admin123`.
   - Go to **Inquiries** &rarr; see the test submission you just sent &rarr; click **"Mark as Read"**.
   - Go to **Projects** &rarr; click **"+ New Project"** &rarr; enter details & toggle **"Published"** &rarr; verify it appears immediately on the public homepage.
5. **Printable CV**: Click **"Print / Save CV"** in the footer &rarr; verify the clean black-and-white print layout opens ready to save as PDF.
