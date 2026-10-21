# Brian Nielsen

**Field CTO · AI Architect · Execution Systems**
Dallas–Fort Worth, TX

I design systems where AI moves from demo to production. My work sits at the intersection of agent orchestration, delivery architecture, and developer ergonomics — building the scaffolding that lets teams ship AI systems with operational discipline from the start.

Lately that means building the infrastructure *around* AI agents, not just agents themselves: systems that **generate** agent applications, **orchestrate** agent work, **govern** agent fleets, and **ship** real product on top.

---

## Projects

### Agency Pipeline — Autonomous Multi-Agent Software Factory
> *A plain-language request → a secured, production application — built, reviewed, and shipped by agents*

An end-to-end agentic pipeline that turns a plain request into a **deployed, secured application**. A **Prompt Composer** routes the request to the smallest sufficient set of registered specialist agents — parallel **builders** plus an adversarial **judge**, with a **Project Manager** agent always injected — and drives the full lifecycle:

- **Use-case synthesis** — turns the request into structured use cases / requirements the agents build against
- **Mock UI generation** — produces interactive UI mockups for review *before* any code is written
- **Multi-agent build + review** — builders write the app in parallel, the judge critiques, with **live progress streamed over WebSocket**
- **Sandboxed validation** — every build runs in an **isolated sandbox**, keeping agent-generated code out of production until it passes
- **Automated production deployment** — promotes validated apps to **production on Google Cloud**, collapsing idea-to-live from weeks to hours
- **Board tracking + resumable memory** — the Project Manager agent opens a card on a self-hosted **Planka** board, assigns a checklist task per agent, and moves it through the workflow; a per-run `STATE.md` records goal, decisions, and "where to pick up" so work survives across sessions
- **Full prompt-to-output traceability** at every stage

**Production hardening:** fronted by a **global external GCP load balancer** with managed TLS, gated behind **Clerk one-time-passcode (OTP)** authentication + SSO token hand-off; a zero-redeploy runtime module feed ships generated apps straight into the live multi-tenant platform.

**Architecture:** Piral micro-frontend shell hosting independent pilets · Fastify + SQLite orchestration service · self-hosted Planka board · Claude agents · WebSocket streaming · GCP (Cloud Run, Load Balancing) · Clerk

**Stack:** TypeScript · Piral · Fastify · SQLite · Planka · Claude · Google Cloud · Clerk

---

### AgentOS — Enterprise Control Plane for AI Agent Fleets
> *Governance + FinOps for AI labor — the operating layer around agent employees*

OpenClaw and Hermes help agents *do* work. AgentOS helps an organization **govern, provision, fund, monitor, and control** agents doing work — the HR system, finance ledger, access-control layer, and service catalog around a fleet of agent "employees."

- **Org-scoped resources** — business units, roles, ownership links, approval gates
- **Model-tier policy & access control** — what each agent can touch and which tier it runs on
- **FinOps / chargeback** — attribute agent cost to the business unit that pays for it
- **Operator console** — org tree, rollout, approval queue, failures, and cost in one place
- **Distributed runtime** — a Node control plane + operator console with a **Rust** runtime worker over Postgres/Redis, containerized with Docker

**Stack:** TypeScript · Rust · Node.js · PostgreSQL · Redis · Docker · pnpm monorepo

---

### LiquidMetal — Multi-Agent Application Generator
> *CLI-driven scaffolding for production-grade agentic systems*

Most AI agent systems fail when transitioning from demo to production — they lack structured evaluation loops, observability, safe schema evolution, and clear separation between orchestration and business logic.

LiquidMetal is an architectural experiment in solving those problems from the ground up:

- **Agent scaffolding** — generates modular multi-agent applications with containerized services and event-driven communication
- **Dynamic model awareness** — agents adapt to model and schema changes without restarts; full dependency mapping and rollback support
- **Evaluation & observability** — agent-level logging, model version tagging, LLM output scoring, correlation across agent executions
- **Zero-downtime component swapping** — hot-swap agents and models safely in running systems
- **Deployment-first** — Kubernetes-ready, Docker Compose for local dev, environment-based configuration separation

```bash
# Generate a production-ready multi-agent application
multiagent new my-system --template rfp

# Or from natural language
multiagent new "build a CRM with lead scoring"

# Interactive schema editor with live agent impact analysis
multiagent model Customer
```

**Templates:** RFP evaluation workflow · CRM with lead scoring · Content Generation · Generic multi-agent starter · ERP · Marketplace

**Stack:** TypeScript / Node.js · Docker · Kubernetes · Event-driven orchestration · RAG pipelines

---

### FORGE Method — Execution Architecture for AI-Augmented Delivery
> *Graph-native project management built for the age of AI coding agents*

**[Documentation →](https://cloudtrainerwork.github.io/Forge/)**

**v1.0 shipped February 25, 2026.** v1.1 (specification layer + GSD export engine) in milestone closeout.

Every engineering leader maintains a parallel system — a mind map, spreadsheet, or Slack thread — alongside their Agile tool to track what's actually happening. That shadow system is the real status infrastructure. The Agile tool is theater.

FORGE replaces the **data model** of Agile tooling while preserving the intent. Work is modeled as a directed graph with typed edges. Readiness is measured across six dimensions, not inferred from sprint ritual. Release confidence is computed from actual state — not reconstructed from ticket counts.

**The five practices:**

| Practice | Replaces | Core Idea |
|---|---|---|
| Graph-Based Work Modeling | Flat backlogs | Work as nodes in a directed graph with typed edges |
| Multi-Dimensional Readiness | Single status fields | Six-axis state: Requirements, Design, FE, BE, Integration, Test |
| Shovel-Ready Specifications | Vague acceptance criteria | Structured completeness gates before sprint entry |
| Sprint Execution Windows | Grooming + negotiation | Pull from ready queue; overhead is first-class budget |
| Closed-Loop Reconciliation | Manual status updates | Code commits flow back to graph via CI pipeline |

**Why this matters for AI-powered development:**
AI coding agents (Cursor, Claude Code, GitHub Copilot, Windsurf) are mainstream. They also operate in a context vacuum — no tool connects the work graph to the development context. FORGE's Shovel-Ready Specs become the structured input contract for these tools. The closed-loop reconciliation system maps code completions back to graph readiness automatically. The CI pipeline is the reconciliation agent. Developer workflow is unchanged.

**Architecture:** Neo4j + PostgreSQL hybrid · GSD / BMAD / Claude Code export engine · GitHub Action for reconciliation · VS Code Extension · Manifest Schema

**In development:** `forge-map` — reverse-engineer any existing repo into a FORGE graph in under 10 minutes. Point it at a codebase, get nodes, edges, and dependency structure automatically imported into your project. Solves cold-start adoption for teams that already have a codebase.

**Submitted to present at:** Agile Alliance — Future of Work & Careers track (*"Your Agile Tools Can't Survive AI Agents"*)

> Raise your hand if you maintain a spreadsheet, mind map, or Slack thread alongside your Agile tool to track what's actually happening.
>
> That parallel system is the real status infrastructure. Your Agile tool is the theater.
>
> This session makes the case that Jira, Linear, and every mainstream project management tool share the same fatal architectural flaw: they model work as flat lists with single-status fields. Meanwhile, AI coding agents — Cursor, Claude Code, GitHub Copilot, Windsurf — are mainstream and accelerating. They generate code at unprecedented speed. And they operate in a complete context vacuum.
>
> The collision of these two facts is where modern delivery breaks down.
>
> This talk introduces Execution Architecture: a graph-native approach to modeling work, measuring readiness across six dimensions, and creating a closed-loop system where code commits flow back to the delivery graph automatically. Live demos. Real data. A working system — not a framework.

---

### Kroniqa — Developer-First Compliance Evidence Platform
> *Connect a change in law to code evidence, a decision, remediation, and later verification*

Small software teams rarely have a repeatable way to answer: *what personal data, trackers, payment flows, or risky access patterns does this codebase contain — and which reviewed legal obligations actually apply?* Kroniqa treats scanner, legal-news, ticketing, and audit as **one connected workflow** instead of four separate products.

- **Deterministic local scanner** — identifies compliance signals on your machine, emitting a source-free scan manifest and redacted previews
- **Explicit snippet-approval boundary** — source never leaves the machine for hosted analysis without deliberate, scoped approval
- **Versioned legal rule cards** — reviewed authoritative sources become applicability rules; the system matches them to *this* app and audience
- **Deliberate GitHub issue flow** — confirmed gaps become review-ready issues, not noise
- **The chronicle** — an auditable artifact linking *law change → code evidence → applicability decision → remediation → verification*
- **Self-hosted Cadence orchestration** for the hosted analysis path

**Architecture:** pnpm monorepo — scanner · analysis · api · legal-orchestrator · MCP · web dashboard · Cadence

**Stack:** TypeScript · Next.js · PostgreSQL · OpenAI · MCP (Model Context Protocol) · Cadence

---

### IPv4 Intelligence / Konetix — Production Multi-Tenant Platform
> *Registry, routing, and reputation intelligence as self-service SaaS*

A production, multi-tenant SaaS platform for an IPv4 address brokerage — turning registry, routing, and reputation data into self-service customer tools and AI-driven sales automation.

- **IPv4 estate resolution** — resolves an org's owned prefixes, utilization, and value from RDAP/RIR data
- **Route Assurance** — validates prefixes against BGP, RPKI, and IRR route objects and surfaces exactly what to clean up
- **Blacklist reputation scanning** — scans owned space against 100+ blocklist providers, graded and reported
- **Executive estate dashboard** — unifies all three systems per tenant, with per-prefix drill-down
- **Scan engine** — chunked and horizontally scaled, with a BigQuery data firehose and self-owned /24 egress, sized to enumerate up to a /16 with zero data truncation
- **AI email agent** — human-in-the-loop CRM agent that enriches inbound leads with live lookups, drafts replies from an editable SOP matrix, and learns from reviewer decisions
- **Platform** — multi-tenant monetization (Stripe), client/internal/admin RBAC, SOC 2 Type 1 (Security) posture, and several Cloud Run microservice gateways

**Stack:** TypeScript · Piral micro-frontends · Node/Express · Google Cloud (Cloud Run, Cloud SQL/Postgres, BigQuery, GCS, Secret Manager, Load Balancing) · Clerk · Stripe · BGP / RPKI / IRR / RDAP

---

### ShipRight Portal — Production-Readiness Planner & Portal
> *Define what "ready to ship" means, then plan and track it*

A Next.js production-readiness planner and signed-in portal — analyzer, scorecard, cost model, and export, with a Blueprints / Add-ons / Wallet workspace — built on a pure, testable domain analyzer behind a clean data seam.

**Stack:** Next.js (App Router) · Supabase (auth + data, Google OAuth) · Stripe · Cloudflare (edge + Worker)

---

### ⚡ Solana Flash Loan Arbitrage Bot
> *High-performance multi-DEX arbitrage system with a custom Rust route optimizer*

Built to explore the performance boundary between Python orchestration and Rust's native execution characteristics. The system detects and executes arbitrage opportunities across 6 Solana DEXes using a custom flash loan program deployed on mainnet.

**The core engineering problem:** route generation is a tight computational loop — evaluating thousands of potential arbitrage paths per second. Python's GIL makes this impractical at scale. Solution: a Rust engine exposed to Python via PyO3/Maturin.

| Component | Python | Rust | Delta |
|---|---|---|---|
| Route generation | ~100/sec | 239,732/sec | 2,397x |
| Memory usage | Baseline | Zero-copy structures | 10x reduction |

**Key engineering decisions:**
- Atomic flash loan execution — transaction completes profitably or reverts entirely; no partial positions, no stranded capital
- 5-wallet MEV rotation — prevents front-running by mempool searchers
- Configurable circuit breakers — daily loss limits and consecutive failure stops
- Full observability — opportunity logging with rejection reason tracking, wallet balance monitoring, performance analytics

**DEX integrations:** Jupiter · Orca · Raydium · Phoenix · Meteora · Lifinity

**Stack:** Python · Rust (PyO3/Maturin) · Solana · Anchor · PostgreSQL · GitHub Actions

> Research and educational project. Flash loan arbitrage involves substantial financial risk.
