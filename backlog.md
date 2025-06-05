# 📦 NFT Trading App for Little Leagues of America

**Detailed Backlog (Epics & User Stories)**

---

## **Epic 1 — User Management & Authentication**

### User Stories

* **US-1.1** As a parent, I can register for a new account using email/password.
* **US-1.2** As a parent, I can log into my account securely.
* **US-1.3** As a parent, I can register my child as a player and link them to my account.
* **US-1.4** As a player, I can view my personal profile once registered.
* **US-1.5** As a parent, I can edit my profile and update my contact information.
* **US-1.6** As a system, I enforce role-based access: parent, player, coach, admin.

**Est. Story Points (SSCS)**:
3, 2, 3, 2, 1, 1
**Epic Total**: 12 points

---

## **Epic 2 — Player Profile Management**

### User Stories

* **US-2.1** As a parent, I can create a player profile with name, photo, team, and position.
* **US-2.2** As a parent, I can update my child’s profile and re-upload new photos.
* **US-2.3** As a system, I store and validate uploaded photos securely.
* **US-2.4** As a coach, I can view the profiles of players on my team.

**Est. Story Points (SSCS)**:
3, 2, 2, 1
**Epic Total**: 8 points

---

## **Epic 3 — NFT Minting Flow**

### User Stories

* **US-3.1** As a parent, I can submit a mint request for my child’s player card.
* **US-3.2** As a system, I store mint requests in a pending state.
* **US-3.3** As an admin, I can approve or reject minting requests.
* **US-3.4** As a system, I generate an NFT record upon approval (mocked for MVP).
* **US-3.5** As a system, I notify parents when minting is approved or rejected.

**Est. Story Points (SSCS)**:
3, 2, 2, 3, 2
**Epic Total**: 12 points

---

## **Epic 4 — Marketplace Core Functionality**

### User Stories

* **US-4.1** As a parent/player, I can list my NFT for sale in the marketplace.
* **US-4.2** As a buyer, I can view all NFTs listed for sale.
* **US-4.3** As a buyer, I can purchase an NFT and transfer ownership (internal DB transfer for MVP).
* **US-4.4** As a system, I track transactions and update ownership records.
* **US-4.5** As a seller, I can cancel my listing before it sells.

**Est. Story Points (SSCS)**:
3, 3, 3, 3, 2
**Epic Total**: 14 points

---

## **Epic 5 — Parental Controls & Approvals**

### User Stories

* **US-5.1** As a parent, I can approve or deny minting requests initiated for my child.
* **US-5.2** As a parent, I can enable or disable trading permissions for my child.
* **US-5.3** As a system, I block all unapproved child transactions automatically.
* **US-5.4** As a parent, I can view pending approval requests in a dashboard.

**Est. Story Points (SSCS)**:
2, 2, 2, 2
**Epic Total**: 8 points

---

## **Epic 6 — Admin Dashboard**

### User Stories

* **US-6.1** As an admin, I can see a queue of pending mint requests.
* **US-6.2** As an admin, I can approve or reject requests.
* **US-6.3** As an admin, I can view moderation logs for all actions taken.

**Est. Story Points (SSCS)**:
2, 2, 2
**Epic Total**: 6 points

---

## **Epic 7 — Transaction History & Logs**

### User Stories

* **US-7.1** As a parent, I can see my transaction history.
* **US-7.2** As a system, I store a transaction log for compliance and reporting.

**Est. Story Points (SSCS)**:
2, 2
**Epic Total**: 4 points

---

## **Epic 8 — Testing, Demo Prep & Polishing**

### User Stories

* **US-8.1** As a developer, I can seed the database with test data for demo.
* **US-8.2** As a QA, I can run a smoke test across all core flows.
* **US-8.3** As a presenter, I can run the full demo scenario successfully.

**Est. Story Points (SSCS)**:
2, 2, 1
**Epic Total**: 5 points

---

## **📊 Backlog Summary**

| Epic                | Total Story Points |
| ------------------- | ------------------ |
| User Management     | 12                 |
| Player Profiles     | 8                  |
| NFT Minting         | 12                 |
| Marketplace         | 14                 |
| Parental Controls   | 8                  |
| Admin Dashboard     | 6                  |
| Transaction History | 4                  |
| Testing & Demo      | 5                  |

**Total: 69 Story Points**

---

👉 **NOTE:** This is fully achievable in one day **only** because:

* We’re using rapid LLM/agent builds.
* Blockchain is stubbed for MVP.
* Payments are not integrated yet.
* Custodial wallets are simulated.
* UX is minimal and functional.

---
