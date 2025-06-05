# 📄 Product Requirements Document (PRD): NFT Trading App for Little Leagues of America

---

## 1️⃣ Executive Summary

The NFT Trading App for Little Leagues of America is a mobile-first platform that allows youth baseball and softball players to mint, trade, and collect digital trading cards as NFTs. The platform combines the excitement of youth sports, collectibles, and modern digital ownership while staying fully COPPA-compliant (for child safety), accessible to parents, and aligned with Little League branding and sponsorship opportunities.

---

## 2️⃣ Objectives

* Create digital player cards (NFTs) for youth athletes.
* Enable safe, family-friendly trading and collecting.
* Provide fundraising mechanisms for teams, leagues, and sponsors.
* Encourage engagement and recognition for players.
* Build an early experience with digital assets for youth and parents.

---

## 3️⃣ Target Users

| Persona        | Description                                         |
| -------------- | --------------------------------------------------- |
| Parents        | Manage accounts, approve actions, purchase NFTs     |
| Players (Kids) | View, collect, and trade approved NFTs              |
| Coaches        | Submit photos, stats, milestones for minting cards  |
| Sponsors       | Purchase special edition NFTs, ad spots, team packs |
| League Admins  | Approve mints, moderate content, revenue sharing    |
| Collectors     | Trade and build digital card collections            |

---

## 4️⃣ Key Features

### 4.1 Account Management

* Parent-controlled accounts for players under 13
* KYC verification for parents
* OAuth sign-up via Google, Apple, Facebook

### 4.2 NFT Minting

* Automated minting from uploaded photos, stats, and milestones
* Limited edition cards: season highlights, MVPs, tournaments
* Blockchain selection (Polygon, Flow, or other eco-friendly chain)

### 4.3 Marketplace

* In-app trading platform
* Fixed price sales and auction options
* League-moderated secondary market
* Revenue split between league and creators

### 4.4 Sponsorships & Fundraising

* Sponsored team card packs
* Local business sponsorship slots on cards
* Fundraising packs with limited runs

### 4.5 Social & Community Features

* Showcase collections publicly or privately
* Team leaderboards for collectors
* Achievement badges for players

### 4.6 Compliance & Safety

* COPPA, GDPR, CCPA compliance
* Parent approval required for trades/purchases
* In-app moderation and reporting system

---

## 5️⃣ Technology Stack

| Layer        | Choice                                 |
| ------------ | -------------------------------------- |
| Frontend     | React Native (iOS/Android)             |
| Backend      | FastAPI (Python)                       |
| Database     | Supabase (Postgres)                    |
| Blockchain   | Flow / Polygon / Avalanche             |
| Payments     | Stripe + Apple Pay / Google Pay        |
| Storage      | AWS S3 (image uploads, metadata)       |
| Wallet       | Custodial Wallet (Fireblocks / Venly)  |
| NFT Standard | ERC-721 / Flow NFTs                    |
| Identity     | OAuth + Parental KYC (Persona / Alloy) |
| Hosting      | Vercel + AWS Lambda                    |

---

## 6️⃣ Data Model (High Level)

### Tables

#### Users

| Field       | Type      | Notes                 |
| ----------- | --------- | --------------------- |
| user\_id    | UUID      | Primary Key           |
| email       | String    | Unique                |
| role        | Enum      | Parent, Player, Coach |
| parent\_id  | UUID      | FK to parent user     |
| created\_at | Timestamp |                       |

#### Players

| Field      | Type   | Notes                |
| ---------- | ------ | -------------------- |
| player\_id | UUID   | Primary Key          |
| name       | String | Player Name          |
| team\_id   | UUID   | FK to Team           |
| stats      | JSONB  | Batting avg, HR, etc |
| image\_url | String | Player photo         |
| nft\_id    | UUID   | FK to NFT            |

#### NFTs

| Field       | Type      | Notes               |
| ----------- | --------- | ------------------- |
| nft\_id     | UUID      | Primary Key         |
| player\_id  | UUID      | FK to Player        |
| token\_uri  | String    | Metadata URL        |
| blockchain  | String    | Flow, Polygon, etc. |
| owner\_id   | UUID      | FK to User          |
| price       | Float     | For sale price      |
| created\_at | Timestamp |                     |

#### Transactions

| Field      | Type      | Notes            |
| ---------- | --------- | ---------------- |
| tx\_id     | UUID      | Primary Key      |
| nft\_id    | UUID      | NFT involved     |
| buyer\_id  | UUID      | Buyer            |
| seller\_id | UUID      | Seller           |
| price      | Float     | Sale price       |
| timestamp  | Timestamp | Transaction date |

#### Sponsorships

| Field         | Type    | Notes         |
| ------------- | ------- | ------------- |
| sponsor\_id   | UUID    | Primary Key   |
| sponsor\_name | String  | Business name |
| logo\_url     | String  | Uploaded logo |
| package\_type | Enum    | Package level |
| active        | Boolean | Active status |

---

## 7️⃣ Revenue Model

* **Primary NFT sales:** League takes % of mint sales.
* **Secondary trading fees:** Platform fee on every trade.
* **Sponsorship packages:** Local businesses buy placements.
* **Fundraising packs:** Seasonal limited edition packs.

---

## 8️⃣ Compliance & Legal

* COPPA-compliant child account structure
* Parental controls for trading and purchasing
* Moderation layer for content approval
* NFT custody managed via custodial wallet to simplify UX
* Smart contract audits prior to launch

---

## 9️⃣ Future Roadmap

| Phase | Feature Set                                             |
| ----- | ------------------------------------------------------- |
| V1    | Minting, Marketplace, Sponsorships, Parental Controls   |
| V2    | Live Game Highlights NFTs, Dynamic Stats Updates        |
| V3    | AR View for Cards, Team Trophy NFTs, Tournament Badges  |
| V4    | National League Interoperability, NFT-to-Physical Merch |

---

## 🔟 Sample User Flow: Mint & Trade

1. Coach uploads player's season stats + photo.
2. Parent reviews + approves mint request.
3. NFT minted via smart contract + stored.
4. Parent/player lists NFT on marketplace.
5. Buyer makes purchase (Stripe/Wallet).
6. Smart contract executes transfer.
7. Transaction recorded for compliance.

---

## 1️⃣1️⃣ Wireframe Sketches (for designer handoff)

> If you'd like, I can also generate a set of UI wireframe outlines for:

* Home Screen
* Player Profile
* Minting Screen
* Marketplace
* Parental Controls
* Trading Flow
* Admin Dashboard

---

## 1️⃣2️⃣ Notes on Blockchain Selection

* **Flow**: Proven in sports (NBA TopShot), youth-friendly.
* **Polygon**: Large ecosystem, low fees, EVM compatible.
* **Avalanche Subnets**: Full control + compliance possible.

---
