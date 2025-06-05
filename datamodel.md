# 📊 Detailed Data Model — NFT Trading App for Little Leagues of America

---

## 🧩 1. Users Table

```sql
CREATE TABLE users (
    user_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    role VARCHAR(50) CHECK (role IN ('parent', 'player', 'coach', 'admin')),
    full_name VARCHAR(255),
    date_of_birth DATE,
    profile_image_url TEXT,
    phone_number VARCHAR(20),
    kyc_status VARCHAR(50) CHECK (kyc_status IN ('pending', 'verified', 'rejected')) DEFAULT 'pending',
    parent_id UUID REFERENCES users(user_id),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

> ✅ *Note: Players under 13 will be linked to parent via `parent_id`*

---

## 🧩 2. Teams Table

```sql
CREATE TABLE teams (
    team_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    league_id UUID REFERENCES leagues(league_id),
    team_name VARCHAR(255) NOT NULL,
    coach_id UUID REFERENCES users(user_id),
    division VARCHAR(100),
    season_year INT,
    logo_url TEXT,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 3. Leagues Table

```sql
CREATE TABLE leagues (
    league_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    league_name VARCHAR(255) NOT NULL,
    location VARCHAR(255),
    admin_user_id UUID REFERENCES users(user_id),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 4. Players Table

```sql
CREATE TABLE players (
    player_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(user_id),
    team_id UUID REFERENCES teams(team_id),
    position VARCHAR(50),
    jersey_number INT,
    height_cm INT,
    weight_kg INT,
    bats VARCHAR(10) CHECK (bats IN ('Right', 'Left', 'Switch')),
    throws VARCHAR(10) CHECK (throws IN ('Right', 'Left')),
    bio TEXT,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 5. Player\_Stats Table

```sql
CREATE TABLE player_stats (
    stat_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    player_id UUID REFERENCES players(player_id),
    season_year INT,
    games_played INT,
    at_bats INT,
    hits INT,
    home_runs INT,
    rbi INT,
    stolen_bases INT,
    batting_average DECIMAL(5,3),
    on_base_percentage DECIMAL(5,3),
    slugging_percentage DECIMAL(5,3),
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 6. NFTs Table

```sql
CREATE TABLE nfts (
    nft_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    player_id UUID REFERENCES players(player_id),
    minting_request_id UUID REFERENCES minting_requests(request_id),
    blockchain VARCHAR(50),
    contract_address VARCHAR(255),
    token_id VARCHAR(255),
    token_uri TEXT,
    owner_user_id UUID REFERENCES users(user_id),
    status VARCHAR(50) CHECK (status IN ('minted', 'listed', 'sold', 'retired')) DEFAULT 'minted',
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 7. Minting Requests Table

```sql
CREATE TABLE minting_requests (
    request_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    requested_by_user_id UUID REFERENCES users(user_id),
    player_id UUID REFERENCES players(player_id),
    photo_url TEXT,
    stats_json JSONB,
    approved BOOLEAN DEFAULT FALSE,
    approved_by UUID REFERENCES users(user_id),
    rejected_reason TEXT,
    requested_at TIMESTAMP DEFAULT NOW(),
    approved_at TIMESTAMP
);
```

---

## 🧩 8. Marketplace Listings Table

```sql
CREATE TABLE marketplace_listings (
    listing_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    nft_id UUID REFERENCES nfts(nft_id),
    seller_user_id UUID REFERENCES users(user_id),
    price_usd DECIMAL(10,2),
    listing_type VARCHAR(50) CHECK (listing_type IN ('fixed', 'auction')) DEFAULT 'fixed',
    start_time TIMESTAMP,
    end_time TIMESTAMP,
    status VARCHAR(50) CHECK (status IN ('active', 'sold', 'cancelled')) DEFAULT 'active',
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 9. Transactions Table

```sql
CREATE TABLE transactions (
    transaction_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    listing_id UUID REFERENCES marketplace_listings(listing_id),
    nft_id UUID REFERENCES nfts(nft_id),
    buyer_user_id UUID REFERENCES users(user_id),
    seller_user_id UUID REFERENCES users(user_id),
    transaction_price DECIMAL(10,2),
    payment_method VARCHAR(50),
    blockchain_tx_hash VARCHAR(255),
    completed_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 10. Sponsorships Table

```sql
CREATE TABLE sponsorships (
    sponsorship_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sponsor_name VARCHAR(255),
    contact_email VARCHAR(255),
    phone VARCHAR(20),
    website_url TEXT,
    logo_url TEXT,
    package_tier VARCHAR(50) CHECK (package_tier IN ('local', 'regional', 'national')),
    active BOOLEAN DEFAULT TRUE,
    start_date DATE,
    end_date DATE
);
```

---

## 🧩 11. Sponsored\_Packs Table

```sql
CREATE TABLE sponsored_packs (
    pack_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sponsor_id UUID REFERENCES sponsorships(sponsorship_id),
    league_id UUID REFERENCES leagues(league_id),
    season_year INT,
    total_nfts INT,
    pack_price DECIMAL(10,2),
    active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 12. Admin Moderation Logs

```sql
CREATE TABLE moderation_logs (
    log_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    admin_user_id UUID REFERENCES users(user_id),
    action_type VARCHAR(50),
    target_entity VARCHAR(50),
    target_id UUID,
    notes TEXT,
    created_at TIMESTAMP DEFAULT NOW()
);
```

---

## 🧩 13. Parental Approvals Table

```sql
CREATE TABLE parental_approvals (
    approval_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    parent_user_id UUID REFERENCES users(user_id),
    child_user_id UUID REFERENCES users(user_id),
    action_type VARCHAR(50),
    approved BOOLEAN,
    requested_at TIMESTAMP DEFAULT NOW(),
    approved_at TIMESTAMP
);
```

---

# 🔐 Special Considerations:

* ✅ COPPA compliance: All player accounts linked to parent accounts
* ✅ KYC verification for adults through external KYC provider (Persona, Alloy, etc.)
* ✅ Custodial wallet management through 3rd party (Venly, Fireblocks)
* ✅ GDPR exportable data records (player collections, transactions)

---

# ✅ This data model is:

* **API-ready**
* **Supabase/Postgres compatible**
* **Fully extensible for future features**
* **Enterprise and compliance friendly**

---


