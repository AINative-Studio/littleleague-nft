# 🏃‍♂️ One-Day Agile Sprint Plan — NFT Trading App (MVP Build)

---

## 🎯 **Sprint Goal**

Deliver a functional MVP that allows:

* User registration (parent/player)
* Player profile creation
* NFT minting from uploaded player photos
* Simple marketplace listing and buying
* Parent approval flow
* Basic admin mint approval

---

## 🧩 High-Level Architecture Scope

| Layer       | Stack                                   |
| ----------- | --------------------------------------- |
| Frontend    | React Native (Expo)                     |
| Backend API | FastAPI (Python)                        |
| Database    | Supabase (Postgres)                     |
| Blockchain  | Stubbed mock NFT mint (no live minting) |
| Storage     | AWS S3 (or Supabase Storage)            |
| Payments    | Skipped for MVP                         |
| Auth        | Supabase Auth (email/password)          |

---

## 🚩 **Key Constraints**

* All features fully local or testnet (no live blockchain or payment rails).
* Parental approval simplified: toggle switch controlled by parent user.
* Custodial wallet is mocked — simply tracked as `owner_user_id` in database.
* Admin mint approval is hard-coded for demo.

---

## 🔨 **Sprint Timeline (8-10 Hours)**

| Time Block   | Activity                  | Deliverables                                                    |
| ------------ | ------------------------- | --------------------------------------------------------------- |
| 0:00 – 0:30  | Kickoff & Setup           | Repo initialized, Supabase DB live, basic frontend scaffold     |
| 0:30 – 1:30  | User Auth & Roles         | Register/Login, Parent/Player roles enforced                    |
| 1:30 – 2:30  | Player Profiles           | Player creation, photo upload, parent link                      |
| 2:30 – 3:30  | Minting Flow              | Mint request form, Admin approval dashboard, NFT record created |
| 3:30 – 4:30  | Marketplace Listings      | List NFT for sale, view marketplace, simple purchase            |
| 4:30 – 5:30  | Parental Approval Flow    | Parent sees requests, toggles approvals                         |
| 5:30 – 6:00  | Trade Flow                | Buyer flow: select listing → purchase → transfer ownership      |
| 6:00 – 7:00  | Admin Panel               | Approve/reject mint requests, basic moderation log              |
| 7:00 – 8:00  | Frontend Polishing        | Styling, minor bug fixes, UX cleanup                            |
| 8:00 – 9:00  | Final Testing & Demo Prep | Smoke test all core flows                                       |
| 9:00 – 10:00 | Optional Buffer           | Contingency or feature enhancement                              |

---

## 📌 **Sprint Epics & Stories**

### EPIC 1 — User Accounts

* [ ] As a parent, I can register/login via email/password.
* [ ] As a parent, I can register my child as a player.
* [ ] As a parent, I can see all players linked to my account.

### EPIC 2 — Player Profiles

* [ ] As a parent, I can create player profiles with name, team, photo, and position.
* [ ] As a player, I can view my own profile.

### EPIC 3 — NFT Minting Flow

* [ ] As a parent, I can request minting for my player.
* [ ] As an admin, I can approve/reject mint requests.
* [ ] As a system, mint request approval triggers NFT creation (mocked).

### EPIC 4 — Marketplace

* [ ] As a parent/player, I can list my NFT for sale.
* [ ] As a buyer, I can browse available NFTs.
* [ ] As a buyer, I can purchase listed NFTs (ownership transfers inside DB).

### EPIC 5 — Parental Approvals

* [ ] As a parent, I can approve or deny actions for my child (e.g. minting, trading).
* [ ] As a system, disallow child actions without parent approval.

### EPIC 6 — Admin Panel

* [ ] As an admin, I can see pending mint requests.
* [ ] As an admin, I can approve or reject requests.
* [ ] As an admin, I can view moderation logs.

### EPIC 7 — Testing & Demo Prep

* [ ] Smoke test core flows.
* [ ] Prepare demo data.
* [ ] Build simple demo script.

---

## 🧮 Story Sizing (SSCS Fibanocci)

| Story               | Points |
| ------------------- | ------ |
| User Auth           | 3      |
| Player Profiles     | 3      |
| Mint Request        | 3      |
| Admin Approval      | 2      |
| Marketplace Listing | 3      |
| Trade Flow          | 3      |
| Parental Approval   | 2      |
| Admin Panel         | 2      |
| Testing & Demo Prep | 2      |

**Total: \~23 Points — achievable for 1-day sprint with AI-powered agents + LLM copilots.**

---

## 🛠️ **Pre-Hackathon Prep**

| Task                                | Owner |
| ----------------------------------- | ----- |
| Supabase DB provisioned             | ✅     |
| Repo scaffolding (monorepo)         | ✅     |
| Mock blockchain service             | ✅     |
| Admin test accounts                 | ✅     |
| Brand assets (logos, icons)         | ✅     |
| Minimal UI Kit (Tailwind/Vercel UI) | ✅     |

---

✅ **This plan allows you to deliver:**

* End-to-end functional MVP
* Fully demoable core NFT mint/trade flow
* Build foundation for full production build

---


