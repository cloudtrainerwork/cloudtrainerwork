# Brian Nielsen

**Field CTO · AI Architect · Execution Systems**
Dallas–Fort Worth, TX

I design systems where AI moves from demo to production. My work sits at the intersection of agent orchestration, delivery architecture, and developer ergonomics — building the scaffolding that lets teams ship AI systems with operational discipline from the start.


---

## Projects

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

### Kroniqa - Multi-Agent Application Platform with LiquidMetal 
> *CLI-driven scaffolding for production-grade agentic systems*

Most AI agent systems fail when transitioning from demo to production — they lack structured evaluation loops, observability, safe schema evolution, and clear separation between orchestration and business logic.

Kroniqa is an architectural experiment in solving those problems from the ground up:

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

