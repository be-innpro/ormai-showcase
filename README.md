# ORMAI

> **A 9-agent virtual development team — running on your VPS, orchestrated through 64 MCP tools.**
> A be-innpro product. Submitted to the **START Rise Challenge 2026**.

[![Status](https://img.shields.io/badge/status-MVP%20%C2%B7%20TRL%206--7-blue)]()
[![License](https://img.shields.io/badge/license-Proprietary%20%C2%B7%20INPI%20filed-orange)]()
[![Stack](https://img.shields.io/badge/stack-Python%20%E2%80%A2%20LangGraph%20%E2%80%A2%20MCP-success)]()

---

## What it is

ORMAI is a **multi-agent orchestration platform** that delivers a complete, virtual software-development team — 9 specialised agents working autonomously and in coordination, embedded in your customer's own infrastructure (VPS or dedicated server).

It automates the **non-coding 50%** of every engineering team's capacity: requirements analysis, architecture, planning, UX/accessibility review, security veto, QA, DevOps, knowledge management. Humans stay in the loop at every gate — the agents do the work; the team makes the decisions.

## Problem

CTOs and engineering leads at SMEs and scale-ups can't hire — let alone retain — the senior talent they need:

- **66% deficit** in qualified Portuguese tech professionals
- **€180K/year minimum** for a 3-FTE foundational team (architect, security, DevOps)
- **70% failure rate** on enterprise consulting engagements
- **Black-box** AI dev tools provide acceleration but no auditability — unsuitable for regulated sectors

ORMAI delivers the team they can't hire — at a fraction of the cost — with full audit trail and IP control.

## Architecture

```
                         ┌───────────────────────────────────────────┐
                         │       ORMAI on Customer's VPS / Cloud      │
                         │                                           │
                         │  ┌─────────────────────────────────────┐  │
                         │  │     LangGraph StateGraph (Core)     │  │
                         │  └─────────────────────────────────────┘  │
                         │   │                                  │    │
                         │   ▼                                  ▼    │
                         │  ┌────────┐ ┌────────┐ ┌────────┐ ┌────┐  │
                         │  │ Iris   │ │ Hermes │ │Promet. │ │... │  │
                         │  │ CX     │ │ PO     │ │Architect│ │ +6 │  │
                         │  └────────┘ └────────┘ └────────┘ └────┘  │
                         │                                           │
                         │  ┌─────────────────────────────────────┐  │
                         │  │        64 MCP Tools                 │  │
                         │  │  Figma · GitHub · Azure DevOps ·    │  │
                         │  │  OpenProject · Discord · Paper.des. │  │
                         │  │  Postgres · Mongo · Filesystem      │  │
                         │  └─────────────────────────────────────┘  │
                         │                                           │
                         │  ┌─────────────────────────────────────┐  │
                         │  │  5-tier Model Router                │  │
                         │  │  Claude Sonnet 4.6 (5%)             │  │
                         │  │  → Claude Haiku 4.5 (35%)           │  │
                         │  │  → Qwen3 30B (60%)                  │  │
                         │  │  → OpenRouter fallback              │  │
                         │  │  → Local Ollama (circuit breaker)   │  │
                         │  └─────────────────────────────────────┘  │
                         └───────────────────────────────────────────┘
```

## 9 specialised agents

| Agent | Role | Hard-coded constraint |
|---|---|---|
| **Iris** | Customer Experience | Frame every artefact through user impact |
| **Hermes** | Product Owner | Translate business intent into specs |
| **Prometheus** | Architecture | Reject any design lacking failure modes |
| **Athena** | Planning | Decompose; respect dependencies |
| **Aphrodite** | UX / Accessibility (WCAG) | No release without WCAG AA verdict |
| **Leonidas** 🛡️ | Security | **Absolute veto** — overrides all other agents |
| **Veritas** | QA | Binary verdict only (pass/fail) |
| **Vulcan** | DevOps | Idempotent infra; reversible deploys |
| **Sophia** | Memory / Knowledge | Symmetric audit trail |

Each agent operates with **24/7 autonomous execution** within its function. **Leonidas has absolute veto authority** on security concerns — overriding any other agent's verdict.

## FORJA Process — methodology layer

ORMAI runs on the **FORJA Process**, a proprietary 9-phase software-delivery methodology with:

- 9 phases (Discover → Research → Architect → Govern → ... → Ship)
- 9 quality gates (each with binary pass/fail)
- 21 artefact types (specs, ADRs, threat models, runbooks, ...)
- 26 anti-patterns automatically detected

FORJA Process is registered with **IGAC** (copyright) and forms the operational substrate ORMAI's agents follow.

## Tech stack

| Layer | Technology |
|---|---|
| **Orchestration** | LangGraph (StateGraph + checkpointing) |
| **Tooling** | FastMCP — 64 tools across 4 MCP servers |
| **Backend** | Python 3.11+ · FastAPI dashboard |
| **State** | PostgreSQL 16 + pgvector · MongoDB 7 · Redis 7 |
| **LLM Routing** | 5-tier (Anthropic, OpenRouter, local Ollama) |
| **Integrations** | OpenProject · Azure DevOps · Figma · Discord · Paper.design |
| **Infra** | Docker Compose (8 services) → K8s for multi-tenant |
| **Resilience** | Circuit breaker + local Ollama fallback |
| **Observability** | Activity logs · LLM audit · cost tracking · phase-boundary commits |

## Computational footprint

- **Today**: dedicated VPS (8–16 vCPU, 32–64 GB RAM) per dev workstation. CPU-bound; no GPU required for current load.
- **Inference**: stateless API calls; 5-tier router optimises cost/latency/quality.
- **At 10× scale**: 130+ concurrent tenants, GPU-resident inference for latency-critical loops (architect, security veto). Latency target <100 ms from a SINES-class facility (~0.5 ms to Lisbon).

## Why "VPS workstation" delivery model

ORMAI is delivered as a **dedicated dev workstation on a managed VPS** — the customer's engineering team logs into the workstation; the agentic team is already running. The customer:

- **Controls the LLM** (Claude / Kiro / OpenClaw / OpenRouter / local) — never locked in
- **Owns the audit trail** (PostgreSQL local to the tenant)
- **Owns the data** (code, specs, designs never leave the tenant)
- **Pays per workstation, not per token** — predictable economics

This is the inverse of black-box dev assistants. **Sovereign by default.**

## Stage & evidence

- **TRL 6/7** · deployed internally as our own dev infrastructure for 6+ months
- **1,171 automated tests** across 30 test suites
- **9 production agents** with hard-coded constraints
- **14 LangGraph workflows** (13 core + 1 FORJA playbook)
- **Symmetric audit trail** — every gate decision durably logged to PostgreSQL + MongoDB
- **Phase-boundary git commits** generated automatically with Conventional Commits

## Intellectual property

- **INPI Utility Model** `20262007897460` (Portugal — under analysis)
- **INPI Utility Model BR** (in analysis)
- **IGAC copyright** on FORJA Process methodology

## Pricing

| Plan | Users | Monthly per user |
|---|---|---|
| **Starter** | 10 | €220 |
| **Professional** | 25 | €180 |
| **Enterprise** | 50 | €160 |

Custom plans for organisations with 100+ engineers. Trajectory: **13 customers in 2026 → 400 customers in 2030**.

## Roadmap

| Phase | Milestone |
|---|---|
| **Phase 1 (current)** | 9 agents · 64 MCP tools · 14 workflows · live integrations |
| **Phase 2 (H2 2026)** | Multi-tenant K8s GA · Microsoft Azure marketplace listing |
| **Phase 3 (2027)** | Sectoral agent packs (financial, healthcare, regulated) |
| **Phase 4 (2027+)** | Self-improving agents (RLHF on customer audit trails) |

## About be-innpro

be-innpro builds **sovereign agentic AI for Europe** — a unified stack of three production products (Datumlens, ORMAI, Nakori) on one orchestration core. Founded in Lisbon by **José Maria Duque (CEO)** and **Neilsen Alves Seixas (CTO)**.

Website: [https://be-innpro.com](https://be-innpro.com)

## Status of this repository

This repository hosts a **public showcase only** — architecture, screenshots, README. The ORMAI source code is **not public** because the corresponding INPI Utility Model is currently under analysis. The full product is available as a managed deployment; contact us for access.

## Contact

- **CEO & Founder** — José Maria Duque — `jose@be-innpro.com`
- **CTO & Co-Founder** — Neilsen Alves Seixas — `neilsen@be-innpro.com`

---

© 2026 be-innpro. All rights reserved. ORMAI, Datumlens, and FORJA Process are protected by pending INPI Utility Model and trademark filings.
