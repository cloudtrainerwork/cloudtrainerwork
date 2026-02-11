

# LiquidMetal Multi-Agent App Generator

Generate production-ready multi-agent applications with structured orchestration, model lifecycle awareness, and deployment scaffolding.

LiquidMetal is a CLI-based reference implementation exploring how multi-agent systems should be designed for real-world deployment. It focuses on modular agent architecture, event-driven workflows, evaluation hooks, and schema evolution without system downtime.

This repository reflects architectural thinking around how AI agents move from prototype to production.

---

## Why This Exists

Most AI agent systems fail when transitioning from demo to production because they lack:

* Structured evaluation loops
* Observability and traceability
* Safe schema and model evolution
* Clear separation of orchestration and business logic

LiquidMetal was built to explore solutions to those problems through:

* Modular agent scaffolding
* Event-driven orchestration
* Model dependency awareness
* Zero-downtime component swapping
* Deployment-first architecture

It is not a commercial product. It is an architectural experiment in production agent design.

---

## Core Capabilities

### Agent Scaffolding

* Generates modular multi-agent applications
* Separates orchestration, business logic, and configuration
* Containerized agent services with Docker support
* Event-driven communication model

### Dynamic Model Awareness

Agents automatically adapt to model and schema changes without system restarts.

Capabilities include:

* Model version tracking
* Dependency mapping between models and agents
* Change notifications via internal event system
* Safe validation before applying changes
* Rollback support

This enables real-time iteration without downtime.

---

## Evaluation and Observability

LiquidMetal includes structured support for:

* Agent-level logging
* Model version tagging
* Change event history
* Evaluation hooks for LLM output scoring
* Correlation between agent executions

The goal is to move beyond demo agents toward traceable, inspectable systems suitable for enterprise use.

---

## CLI Overview

### Generate an Application

```bash
multiagent new my-system --template rfp
```

Or from natural language:

```bash
multiagent new "build a CRM with lead scoring"
```

### Interactive Model Editing

```bash
multiagent model Customer
```

Features:

* Add, modify, or remove fields
* See affected agents
* Validate schema changes
* Deploy updates with agent notifications
* Watch model changes in real time

---

## Architecture Overview

A generated application follows this structure:

```
my-app/
├── raindrop/
│   ├── models/
│   ├── embeddings/
│   ├── pipelines/
│   └── storage/
├── agents/
│   └── AgentName/
│       ├── handler.ts
│       ├── Dockerfile
│       └── config.yaml
├── deploy/
├── tests/
├── docker-compose.yaml
└── README.md
```

The architecture is designed around:

* Event-driven workflows
* Containerized agents
* Clear agent responsibility boundaries
* Schema-driven system behavior

---

## Production Constraints Considered

The design explicitly addresses:

* Idempotent agent execution
* Retry and backoff handling
* Safe model evolution
* Zero-downtime component swapping
* Rollback strategies
* Environment-based configuration separation

---

## Template Library

Currently implemented templates:

* RFP evaluation workflow
* CRM with lead scoring
* Generic multi-agent starter

Planned templates explore ERP, auction systems, e-commerce, and marketplace workflows.

The templates exist to demonstrate how structured agent systems can map to real business processes.

---

## Deployment

Supports:

* Local development with Docker Compose
* Kubernetes-ready deployment
* Infrastructure provider abstraction
* Environment-based configuration

The deployment layer is intentionally separated from agent logic to preserve portability.

---

## Strategic Context

LiquidMetal represents my thinking around:

* Production-ready agent lifecycle management
* Enterprise-grade architecture patterns
* Evaluation-aware system design
* Technical GTM readiness for AI systems
* Developer ergonomics for multi-agent platforms

It is a demonstration of how agent systems can be scaffolded with operational discipline from the beginning rather than retrofitted later.

---

## Status

This repository is an active architectural exploration and is not intended as a commercial platform.

Contributions and architectural discussion are welcome.


