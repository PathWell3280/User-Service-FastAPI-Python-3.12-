# Profile Service (FastAPI + Python 3.12)

## Overview
This microservice manages user profiles with PHI tokenization and AES-256 encryption, enforcing:

- **5 000 RPM** rate limit
- **Row-Level Security** (RLS) on `profiles` table
- **AES-256-encrypted tablespace** (configure in PostgreSQL)
- **PIPEDA Schedule 1** compliance (data residency, minimal collection, encryption)

## Prerequisites

- Python 3.12
- PostgreSQL 16 with encrypted tablespace
- Redis (for rate‐limiting internal storage)

## Setup

1. Clone this repo
2. Create a PostgreSQL database with an **AES-256** tablespace:
   ```sql
   CREATE TABLESPACE phi_encrypted OWNER pathwell LOCATION '/var/lib/postgresql/data_phi'
   -- ensure OS/disk-level encryption (LUKS/AES-256-GCM)
