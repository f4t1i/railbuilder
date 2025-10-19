# 🚂 RAILBUILDER - Railway Workflow Canvas

**Version:** 1.0.0  
**Status:** Database Setup Complete ✅  
**Next Milestone:** M1 - Parser & Canvas MVP (Week 1-3)

---

## 📖 Overview

RAILBUILDER is a **WebGL-based canvas application** for visual railway workflow planning. It enables railway operators and logistics planners to configure trains (locomotives, wagons, containers) through an interactive canvas interface while ensuring **TSI compliance** (Technical Specification for Interoperability) and **deterministic safety validation**.

### Key Features

- 🎨 **Interactive Canvas** - PixiJS-powered WebGL rendering for smooth 60 FPS performance
- 🚂 **Single-Track Workflow** - One canvas = one workflow = one track (Schiene)
- ✅ **Real-time Validation** - Deterministic safety checks (stowage, bogie loads, CG offset)
- 📥 **Multi-format Import** - CSV, XLSX, XML, PDF → normalized JSON
- 📤 **Compliant Export** - JSON, PDF, Excel with digital signatures
- 🤖 **AI-Assisted** - GPT-4 powered optimization suggestions
- 📝 **Complete Audit Trail** - Every mutation logged for compliance

---

## 🚀 Quick Start

### Prerequisites

- PostgreSQL 14+ (or Supabase account)
- Node.js 18+
- psql command-line tool

### 1. Set Up Database

```bash
# Option A: Use Supabase (recommended)
# Create project at https://supabase.com
# Get connection string from Project Settings → Database

# Option B: Use local PostgreSQL
createdb railbuilder_dev

# Set DATABASE_URL
export DATABASE_URL="postgresql://user:pass@host:5432/db"
```

### 2. Run Bootstrap

```bash
# Automated setup (recommended)
bash QUICKSTART.sh

# Manual setup (step-by-step)
# See SETUP_GUIDE.md for detailed instructions
```

### 3. Verify Setup

```bash
# Run tests
psql "$DATABASE_URL" -f tests/sql/test_core.sql
cd tests/js && npm install && npm run test:schema
```

**Expected Result:** All tests pass ✅

---

## 📁 Project Structure

```
RAILBUILDER_Top3_Essentials_v1/
├── 📄 START_HERE_COMPLETE.md          # ← Start here!
├── 📄 SETUP_GUIDE.md                  # Detailed setup instructions
├── 📄 QUICKSTART.sh                   # Automated setup script
├── 📄 SETUP_CHECKLIST.md              # Verification checklist
├── 📄 ARCHITECTURE_IMPLEMENTATION_GUIDE.md  # Implementation guide
│
├── 🗄️ db_core/                        # Database core
│   ├── 01_schema.sql                  # Core schema
│   ├── 02_seed.sql                    # Seed data
│   ├── sql_extras/                    # Hardening, audit, functions
│   └── import_templates/              # Staging & transform
│
├── 🚂 loading_patterns/               # Wagon loading patterns
│   ├── schemas/                       # JSON schemas
│   ├── patterns/                      # Sgns, Sggmrss patterns
│   ├── sql/                           # Pattern SQL (03, 04, 05)
│   └── agent_contracts/               # AI agent contracts
│
├── 🧪 tests/                          # Test suites
│   ├── sql/test_core.sql              # SQL validation tests
│   └── js/                            # JavaScript schema tests
│
├── 📚 docs/                           # Complete documentation
│   ├── arc42/                         # Architecture (12 chapters)
│   ├── PRD.md                         # Product requirements
│   ├── PROJECT_PLAN.md                # Milestones & timeline
│   ├── backend/                       # Backend docs
│   ├── frontend/                      # Frontend docs
│   └── agent/                         # AI agent docs
│
├── 🔧 bootstrap/                      # Setup automation
│   ├── bootstrap_local_psql.sh        # Bootstrap script
│   └── supabase_config.env.example    # Config template
│
└── 📦 Supabase_DB_SingleTrack_Patch_v1.sql  # Single-track patch
```

---

## 🏗️ Architecture

### System Overview

```
User (Browser)
    ↓
Frontend (React 18 + PixiJS)
    ↓
Backend API (Node.js + Express)
    ↓
Database (PostgreSQL + Supabase)
    ↓
AI Agent (GPT-4 + TSI Rules)
```

### Technology Stack

**Frontend:**
- React 18 (component architecture)
- PixiJS 7 (WebGL canvas)
- TypeScript (type safety)
- React Query (state management)

**Backend:**
- Node.js + Express (API)
- TypeScript (type safety)
- Supabase (BaaS)
- WebSocket (real-time)

**Database:**
- PostgreSQL 14+ (main DB)
- Supabase (hosting + RLS)
- Row Level Security (RLS)
- Audit trail (all mutations)

**AI:**
- OpenAI GPT-4 (TSI interpretation)
- Custom training data (railway domain)

---

## 📊 Single-Track Workflow Model

**Core Concept:** One Canvas = One Workflow = One Track

```
Workflow (Canvas)
    │
    └─► Track (Schiene)
            │
            ├─► Wagon 1 (order_index: 0)
            │       ├─► Container A (at locking point)
            │       └─► Container B (at locking point)
            │
            ├─► Wagon 2 (order_index: 1)
            │       └─► Container C
            │
            └─► Wagon 3 (order_index: 2)
```

**Database Tables:**
- `train_workflows` - Workflow metadata
- `train_wagons_map` - Wagon sequence on track
- `train_placements` - Container placements on wagons

**Validation Functions:**
- `fn_check_stowage` - Locking alignment, overhang
- `fn_bogie_loads` - Axle load distribution
- `fn_cg_offset` - Center of gravity offset

---

## 🎯 Project Milestones

| Milestone | Content | Timeline | Status |
|-----------|---------|----------|--------|
| **Setup** | Database bootstrap | Week 0 | ✅ Complete |
| **M1** | Parser & Canvas MVP | Week 1-3 | 🔄 Next |
| **M2** | TSI Engine + AI Agent | Week 4-6 | ⏳ Planned |
| **M3** | Export + Signatures | Week 7-8 | ⏳ Planned |
| **M4** | Observability + Security | Week 9-10 | ⏳ Planned |
| **GA** | Stabilization + Audits | Week 11-12 | ⏳ Planned |

---

## 📚 Documentation

### Getting Started
- **[START_HERE_COMPLETE.md](START_HERE_COMPLETE.md)** - Complete startup guide
- **[SETUP_GUIDE.md](SETUP_GUIDE.md)** - Detailed setup instructions
- **[SETUP_CHECKLIST.md](SETUP_CHECKLIST.md)** - Verification checklist

### Architecture & Implementation
- **[ARCHITECTURE_IMPLEMENTATION_GUIDE.md](ARCHITECTURE_IMPLEMENTATION_GUIDE.md)** - Complete implementation guide
- **[docs/arc42/](docs/arc42/)** - Arc42 architecture documentation (12 chapters)
- **[docs/PRD.md](docs/PRD.md)** - Product Requirements Document
- **[docs/PROJECT_PLAN.md](docs/PROJECT_PLAN.md)** - Project plan & milestones

### Database
- **[db_core/README_SUPABASE.md](db_core/README_SUPABASE.md)** - Database documentation
- **[README_PATCH.md](README_PATCH.md)** - Single-track patch documentation
- **[loading_patterns/README_LOADING_PATTERNS.md](loading_patterns/README_LOADING_PATTERNS.md)** - Loading patterns

### Development
- **[MASTER_PROMPT.md](MASTER_PROMPT.md)** - Development guidelines (DeepALL V2.2)
- **[docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)** - Contribution guidelines
- **[docs/TEST_STRATEGY.md](docs/TEST_STRATEGY.md)** - Testing strategy

---

## 🔐 Security & Compliance

- **Authentication:** JWT + Refresh tokens
- **Authorization:** RBAC (Admin, Betriebsleiter, Logistikplaner, ReadOnly)
- **Database Security:** Row Level Security (RLS) enabled
- **Audit Trail:** All mutations logged in `audit.change_log`
- **Transport Security:** TLS 1.3
- **Input Validation:** Sanitization, MIME checks, AV scan
- **Compliance:** TSI (Technical Specification for Interoperability)

---

## 📈 Performance Targets

- **API Response:** P95 < 200ms (uncached), < 50ms (cached)
- **Canvas FPS:** P95 > 30 FPS (target: 60 FPS)
- **File Upload:** 15MB < 5 seconds
- **Memory Usage:** < 100MB for 5 active servers
- **Uptime:** > 99.5%
- **TSI Compliance:** 100% rule-based validation

---

## 🧪 Testing

### SQL Tests
```bash
psql "$DATABASE_URL" -f tests/sql/test_core.sql
```

**Tests:**
- ✅ Stowage validation (locking, overhang)
- ✅ Bogie load calculations
- ✅ CG offset checks
- ✅ Workflow resequencing

### JavaScript Tests
```bash
cd tests/js
npm install
npm run test:schema
```

**Tests:**
- ✅ JSON schema validation
- ✅ Contract compliance
- ✅ Data integrity

---

## 🛠️ Development

### Quality Standards (DeepALL V2.2)

- ✅ No `any` type in TypeScript (except justified)
- ✅ No shortcuts or placeholders
- ✅ Production-ready code from first commit
- ✅ Minimum 90% test coverage
- ✅ All performance targets met
- ✅ Complete documentation

### Code Quality Gates

- All PRs require approval
- Performance benchmarks must pass
- Documentation updated with code
- Security review for external interfaces

---

## 🤝 Contributing

See **[docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)** for:
- Code style guidelines
- Commit message conventions
- Pull request process
- Testing requirements

---

## 📄 License

See **[docs/SBOM_AND_LICENSE_POLICY.md](docs/SBOM_AND_LICENSE_POLICY.md)**

---

## 🆘 Support

### Troubleshooting
- Check **[SETUP_GUIDE.md](SETUP_GUIDE.md)** troubleshooting section
- Review error messages in terminal
- Verify DATABASE_URL is correct
- Check PostgreSQL version (must be 14+)

### Documentation
- **Architecture:** `docs/arc42/`
- **API:** `ARCHITECTURE_IMPLEMENTATION_GUIDE.md`
- **Database:** `db_core/README_SUPABASE.md`
- **Testing:** `docs/TEST_STRATEGY.md`

---

## ✨ Next Steps

1. **Review Architecture** - Read `ARCHITECTURE_IMPLEMENTATION_GUIDE.md`
2. **Set Up Backend** - Implement API endpoints (M1)
3. **Set Up Frontend** - Build Canvas UI (M1)
4. **Integration Testing** - E2E workflows
5. **Deploy** - Production deployment (GA)

---

**Ready to build!** 🚂✨

For detailed instructions, start with **[START_HERE_COMPLETE.md](START_HERE_COMPLETE.md)**

