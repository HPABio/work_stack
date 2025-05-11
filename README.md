# work_stack
Integrated Software Tools for workflow automation and optimisation using n8n, twenty, huly/plane, Cal.Com, and supabse.
# ─────────────────────────────────────────────
# 📦 PURPOSE / STRATEGY
# ─────────────────────────────────────────────
# User is setting up a unified Docker Compose-based SaaS/automation stack on a VPS.
# Apps include: n8n (automation), TwentyCRM, Cal.com (calendar booking), Supabase (auth/db), and PostgreSQL (shared).
# Reverse proxy is Traefik v3.1, managed via Coolify.
# The stack must support integration with RAG (Retrieval-Augmented Generation) and vector DBs later.

# ─────────────────────────────────────────────
# 🧠 APPLICATIONS
# ─────────────────────────────────────────────
# - n8n           → Workflow automation
# - TwentyCRM     → CRM system
# - Cal.com       → Booking/calendar app
# - Supabase      → Auth, Postgres, and potential RAG backend
# - PostgreSQL    → One central instance with multiple DBs/users

# ─────────────────────────────────────────────
# 📂 REPO & FILE STRUCTURE
# ─────────────────────────────────────────────
# Single Git repo containing:
# /docker-compose/
#   - postgres.yml
#   - n8n.yml
#   - twenty.yml
#   - calcom.yml
#   - supabase.yml (optional or future)
# .env → root-level global environment variables
# init/ (optional)
#   - init.sql → User-defined init script for Postgres

# ─────────────────────────────────────────────
# 📄 COMPOSE FILE SCHEME (ALL SERVICES)
# ─────────────────────────────────────────────
# - All services use internal port 3000
# - All services on external network: coolify-net
# - All services must expose healthchecks if possible
# - All services must have Traefik labels:
#     traefik.enable=true
#     traefik.http.routers.<name>.rule=Host(`<subdomain>`)
#     traefik.http.routers.<name>.entrypoints=https
#     traefik.http.routers.<name>.tls.certresolver=letsencrypt
#     traefik.http.services.<name>.loadbalancer.server.port=3000
# - Supabase, if used, will be split into its own folder or compose file

# ─────────────────────────────────────────────
# 🌍 ENVIRONMENT (.env)
# ─────────────────────────────────────────────
# Global:
#   NODE_ENV=production
#   TZ=Europe/Berlin
#   GENERIC_TIMEZONE=Europe/Berlin

# Postgres (shared):
#   POSTGRES_SUPERUSER=admin
#   POSTGRES_SUPERPASS=supersecurepassword
#   POSTGRES_PORT=5432

# App-specific DB users:
#   N8N_DB=n8n
#   N8N_DB_USER=n8n_user
#   N8N_DB_PASS=n8n_password
#   TWENTY_DB=twenty
#   TWENTY_DB_USER=twenty_user
#   TWENTY_DB_PASS=twenty_password
#   CALCOM_DB=calcom
#   CALCOM_DB_USER=calcom_user
#   CALCOM_DB_PASS=calcom_password

# Domains:
#   N8N_HOST=n8n.biocentra.eu
#   TWENTY_HOST=twenty.biocentra.eu
#   CALCOM_HOST=calendar.biocentra.eu

# Cal.com secrets:
#   NEXTAUTH_SECRET=...
#   CALENDSO_ENCRYPTION_KEY=...

# Supabase env (optional, not yet defined)

# ─────────────────────────────────────────────
# 🧩 HOSTING & TOOLS
# ─────────────────────────────────────────────
# Hosting: VPS (Hostinger)
# Orchestration: Coolify (used for app deployment + env mgmt)
# Reverse proxy: Traefik v3.1 (inside container: coolify-proxy)
# Docker network: all services must use external network: coolify-net
# Data: Docker volumes for persistent storage
# DNS: Domains like `*.biocentra.eu` are pointed to VPS and used in `Host()` rules

# ─────────────────────────────────────────────
# 🛠️ FUTURE ADDITIONS
# ─────────────────────────────────────────────
# - Vector DB integration for RAG (likely via Supabase / pgvector)
# - Optional embedding workers
# - Enhanced auth (possibly via Supabase)
# - Git-based CI/CD
