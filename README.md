# PlayerLog.ai

> AI gaming coach that remembers every session, every build, every clutch moment.

## What Is This

PlayerLog.ai is a gaming-focused themed vessel of [log-origin](https://github.com/CedarBeach2019/log-origin) — a privacy-first, self-improving AI gateway. It's a competitive gaming companion that tracks your sessions, optimizes your builds, analyzes the meta, and coaches you to rank up.

**The core idea:** Every game builds a log. The log reveals your patterns. Your coach gets smarter. You rank up.

## Features

- **Game Session Logger** — Log games with character, build, KDA, rank, and notes
- **Build Optimizer** — Track build performance, discover top-performing loadouts
- **Meta Tracker** — Stay on top of character pick rates, win rates, and meta shifts
- **Rank Progression** — Visualize your climb (or decline) over time
- **AI Coach Chat** — Chat with an AI coach that knows your session history
- **Weakness Report** — Automated analysis of recurring gameplay weaknesses
- **Mental Game Tips** — Curated tips for tilt control, focus, and improvement

## Gaming Modules

| Module | File | Purpose |
|--------|------|---------|
| Tracker | `src/gaming/tracker.ts` | GameSession, BuildOptimizer, MetaAnalyzer, StatTracker |
| Coach | `src/gaming/coach.ts` | VODReviewPrompts, WeaknessFinder, DecisionCoach, MentalGameTips |

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/v1/app/gaming/sessions` | GET | List recent game sessions |
| `/v1/app/gaming/sessions` | POST | Log a new game session |
| `/v1/app/gaming/stats` | GET | Aggregated stats (win rate, KDA, trends) |
| `/v1/app/gaming/builds` | GET | Top builds + personal build performance |
| `/v1/app/gaming/meta` | GET | Current meta snapshot |
| `/v1/app/gaming/rank` | GET | Rank progression history |
| `/v1/app/gaming/weaknesses` | GET | Automated weakness analysis |
| `/v1/app/gaming/coaching` | POST | AI-powered coaching responses |

## UI Theme

Dark gaming aesthetic: `#0F0F0F` background, neon purple `#A855F7` accents, cyan `#06B6D4` highlights. Sidebar navigation with sections for Dashboard, Analysis, and Coaching.

## Design Documents

| Document | What It Covers |
|----------|---------------|
| [Platform Vision](docs/PLATFORM-VISION.md) | The big picture: LOG.ai concept, domains as hubs, omni-bot, flywheel |
| [Master Plan](docs/MASTER-PLAN.md) | 7-phase roadmap, architecture overview, privacy model |
| [Database Schema](docs/database/SCHEMA-DESIGN.md) | Every table, column, index, migration strategy, D1 constraints |
| [Intelligence Design](docs/routing/INTELLIGENCE-DESIGN.md) | Routing, classification, adaptive learning, draft rounds, agent routing |
| [Security Model](docs/security/SECURITY-MODEL.md) | 17-threat matrix, auth, authorization, API security, Worker security |
| [Privacy Architecture](docs/privacy/PRIVACY-ARCHITECTURE.md) | Encryption flows, PII detection, zero-knowledge analysis, compliance |
| [API Design](docs/api/API-DESIGN.md) | Every endpoint, request/response schemas, streaming, error handling |
| [Protocol Spec](docs/api/PROTOCOL-SPEC.md) | MCP integration, agent communication, local tunnels, federation |
| [UX Design](docs/ux/UX-DESIGN.md) | Personas, wireframes, theming, accessibility, information architecture |
| [Component Spec](docs/ux/COMPONENT-SPEC.md) | Preact components, state management, streaming, performance |
| [Initial Design](docs/architecture/initial-design.md) | Original design from the research phase |

## Key Design Decisions

- **Cloudflare Workers** — edge deployment, $0 on free tier, scale to zero
- **D1 (SQLite)** — our current Python prototype uses SQLite, D1 ports directly
- **Preact** — 4KB, no build step, ships as static Worker assets
- **Hono** — typed HTTP framework for Workers
- **Client-side encryption** — AES-256-GCM, PBKDF2 key derivation, zero-knowledge at rest
- **Regex-first routing** — 5ms classification on Workers, ML optimizes rules over time
- **OpenAI-compatible API** — drop-in replacement for existing SDKs

## Themed Forks

log-origin is the engine. Themed forks add personality:

- **PlayerLog.ai** — Competitive gaming coach with session tracking and build optimization (this fork)
- **DMlog.ai** — TTRPG world-builder's AI
- **studylog.ai** — AI tutor that remembers what you've learned
- **makerlog.ai** — AI pair programmer that learns your style
- **businesslog.ai** — AI assistant for operations and analytics

Each fork customizes: system prompts, UI theme, routing rules, and feature set.

## Research

See `.research/` for the raw research that informed the design:

- `cloudflare-arch.md` — Cloudflare services, limits, pricing
- `privacy-vault.md` — Encryption research, threat model
- `agent-tunnels.md` — Cloudflare Tunnel, MCP, A2A protocols
- `forkable-repo.md` — Fork patterns, update mechanism, personality packs
- `log-platform.md` — LOG.ai brand concept, omni-bot design
- `multi-tenant.md` — Workers for Platforms, scaling tiers
- `agent-network.md` — Agent identity, discovery, communication

## License

MIT
