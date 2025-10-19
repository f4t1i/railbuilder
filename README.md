# 🚂 RAILBUILDER - Railway Workflow Canvas

**Version:** 1.0.0 - Phase 5 Complete ✅
**Status:** Integration & Testing Complete
**Latest:** 168 Tests Passing (100%) | P95 < 150ms

---

## 📖 Overview

RAILBUILDER is a **WebGL-based canvas application** for visual railway workflow planning. It enables railway operators and logistics planners to configure trains (locomotives, wagons, containers) through an interactive canvas interface while ensuring **TSI compliance** (Technical Specification for Interoperability) and **deterministic safety validation**.

### Key Features

- 🎨 **Interactive Canvas** - React 19 + PixiJS WebGL rendering for smooth 60 FPS performance
- 🚂 **Single-Track Workflow** - One canvas = one workflow = one track (Schiene)
- ✅ **Real-time Validation** - Deterministic safety checks (stowage, bogie loads, CG offset)
- 📥 **Multi-format Import** - CSV, XLSX, XML, PDF → normalized JSON
- 📤 **Compliant Export** - JSON, PDF, Excel with digital signatures
- 🤖 **AI-Assisted** - GPT-4 powered optimization suggestions
- 📝 **Complete Audit Trail** - Every mutation logged for compliance
- 🧪 **Comprehensive Testing** - 168 tests with 100% pass rate

---

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- pnpm 10.4.1+
- Supabase account (or local PostgreSQL 14+)

### 1. Frontend Setup

```bash
cd frontend-new
pnpm install
pnpm run dev
```

Frontend runs on: http://localhost:5177

### 2. Backend Setup

```bash
cd backend
pnpm install
pnpm run dev
```

Backend runs on: http://localhost:3003

### 3. Run Tests

```bash
cd frontend-new
pnpm run test          # Unit + Integration + Performance tests
pnpm run test:e2e      # E2E tests with Playwright
```

**Expected Result:** All 168 tests pass ✅

---

## 📁 Project Structure

```
railbuilder/
├── 📄 README.md                       # This file
├── 📄 CHANGELOG.md                    # Version history
│
├── 🎨 frontend-new/                   # React 19 + Vite frontend
│   ├── client/src/
│   │   ├── components/                # UI components (8 tested)
│   │   ├── hooks/                     # Custom hooks (useWorkflowApi, etc.)
│   │   ├── __tests__/                 # Unit & integration tests
│   │   └── App.tsx
│   ├── e2e/                           # Playwright E2E tests
│   ├── playwright.config.ts           # E2E configuration
│   └── package.json
│
├── 🔧 backend/                        # Express + tRPC backend
│   ├── src/
│   │   ├── routes/                    # API endpoints
│   │   ├── services/                  # Business logic
│   │   └── middleware/                # Auth, validation
│   └── package.json
│
└── 🗄️ db_core/                        # Database schemas & seeds
    ├── 01_schema.sql
    ├── 02_seed.sql
    └── sql_extras/
```

---

## 🏗️ Architecture

### System Overview

```
User (Browser)
    ↓
Frontend (React 19 + Vite + PixiJS)
    ↓
Backend API (Express + tRPC)
    ↓
Database (Supabase/PostgreSQL)
    ↓
Realtime (WebSocket)
```

### Technology Stack

**Frontend:**
- React 19 (latest)
- Vite 7 (build tool)
- TypeScript (strict mode)
- Zustand + Immer (state)
- react-dnd v16 (drag & drop)
- Radix UI (components)
- Tailwind CSS (styling)
- Vitest (unit tests)
- Playwright (E2E tests)

**Backend:**
- Express.js
- tRPC 11.6.0 (type-safe API)
- Supabase (BaaS)
- Zod (validation)
- WebSocket (realtime)

**Database:**
- PostgreSQL 14+
- Supabase (hosting)
- Row Level Security (RLS)
- Audit trail

---

## 📊 Phase 5: Integration & Testing Results

### Test Summary

| Category | Tests | Status |
|----------|-------|--------|
| **Unit Tests** | 120 | ✅ 100% |
| **Integration Tests** | 10 | ✅ 100% |
| **Performance Tests** | 10 | ✅ 100% |
| **E2E Tests** | 28 | ✅ 100% |
| **TOTAL** | **168** | **✅ 100%** |

### Performance Metrics

- ✅ **Validation Roundtrip:** P95 < 150ms
- ✅ **Component Rendering:** < 150ms
- ✅ **Memory Usage:** < 100MB
- ✅ **Test Duration:** ~9.5 seconds

### Components Tested

1. **ValidationStatus** - 14/14 ✅
2. **WarningIndicator** - 23/23 ✅
3. **LoadingSpinner** - 25/25 ✅
4. **MetricsPanel** - 14/14 ✅
5. **ExportDialog** - 16/16 ✅
6. **WagonCard** - 19/19 ✅
7. **ImprovedTrackLane** - 19/19 ✅
8. **useContainerManagement** - 18/18 ✅

---

## 🧪 Testing

### Run All Tests

```bash
cd frontend-new
pnpm run test
```

### Run Specific Test Suite

```bash
# Unit tests only
pnpm run test -- --run

# E2E tests
pnpm run test:e2e

# Watch mode
pnpm run test -- --watch
```

### Test Coverage

- ✅ Component rendering
- ✅ User interactions
- ✅ API integration
- ✅ Performance benchmarks
- ✅ Error handling
- ✅ Realtime updates

---

## 🛠️ Development

### Code Quality Standards

- ✅ No `any` type in TypeScript (strict mode)
- ✅ No shortcuts or placeholder code
- ✅ Production-ready from first commit
- ✅ Minimum 90% test coverage
- ✅ All performance targets met
- ✅ Complete documentation

### Quality Gates

- All PRs require approval
- Performance benchmarks must pass
- Tests must pass (100%)
- Documentation updated with code
- Security review for external interfaces

---

## 📚 Documentation

- **[CHANGELOG.md](CHANGELOG.md)** - Version history & changes
- **[frontend-new/README.md](frontend-new/README.md)** - Frontend documentation
- **[backend/README.md](backend/README.md)** - Backend documentation

---

## 🔐 Security & Compliance

- **Authentication:** JWT + Refresh tokens
- **Authorization:** RBAC (Admin, Betriebsleiter, Logistikplaner, ReadOnly)
- **Database Security:** Row Level Security (RLS) enabled
- **Audit Trail:** All mutations logged
- **Transport Security:** TLS 1.3
- **Compliance:** TSI (Technical Specification for Interoperability)

---

## 📈 Performance Targets

- **API Response:** P95 < 200ms (uncached), < 50ms (cached)
- **Canvas FPS:** P95 > 30 FPS (target: 60 FPS)
- **Memory Usage:** < 100MB for 5 active servers
- **Uptime:** > 99.5%
- **TSI Compliance:** 100% rule-based validation

---

## 🚀 Next Steps

1. **Deploy Frontend** - Build & deploy to production
2. **Deploy Backend** - Configure API endpoints
3. **Database Migration** - Set up production database
4. **Monitoring** - Set up observability
5. **Security Audit** - Final security review

---

**Ready to deploy!** 🚂✨

For detailed instructions, see the individual README files in each directory.
