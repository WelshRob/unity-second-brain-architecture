# Unity / CITADEL v2 — Initial Architecture Review

**Date:** 24 August 2026  
**Review basis:** Sanitised read-only Unity/CITADEL v2 review bundle supplied by Gareth.  
**Execution:** None. No provider/API calls, credentials or runtime execution used.

## Overall conclusion

The v2 target architecture is materially stronger than the architecture currently enforced by the legacy/current mixed runtime. Continue with v2, but pause expansion of agent capability until the control-plane boundary is made authoritative and difficult to bypass.

## Target model

- **Unity = Control Plane** — state machine/orchestration, permissions, routing, provider selection, approvals, budgets and audit.
- **Brain = Knowledge Plane** — provider-neutral durable memory, ideally human-readable and portable.
- **AI + Tools = Execution Plane** — replaceable models and explicitly permitted tools.

Agents should be roles rather than models. Authoritative workflow state should remain with Unity. Agents should not bypass Unity to communicate directly.

## Principal findings

### 1. Authority must be split clearly

Unity should own live workflow state and the audit/event ledger. The Brain should own approved durable knowledge and memory. Raw model output is never authoritative by itself.

### 2. Replace completion-by-text with state transitions

Agents should propose outcomes in structured results. Unity alone should validate and perform state transitions.

### 3. Introduce a formal task envelope

Every handoff should carry identity, role, objective, context/evidence references, permissions, budgets, acceptance criteria, provenance and a required result schema.

### 4. Separate roles, providers and models

Role identity must not contain model identity. Unity should map task requirements to a role, then to capability, policy, provider and model.

### 5. Provider fallback decisions belong to Unity

Provider adapters should report failure rather than silently selecting another provider. Unity should decide retry, fallback, pause or human escalation.

### 6. Privacy policy must be capability/data-class based

Free/paid is not a security boundary. Providers should be approved against explicit data classes, retention/training policy, region, network destination and tool permissions.

### 7. Eliminate control-plane bypasses

Direct routing, direct Claude Code execution, direct skill writes/deletes and direct Kanban mutation must eventually pass through the same Unity authorisation boundary.

### 8. Treat execution engines as tools

Codex, Claude Code, shell, browser automation, filesystem mutation and similar capabilities should sit behind a Tool Broker controlled by Unity permissions and approval policy.

### 9. Keep the Brain principles

Strong principles worth preserving include:
- Markdown as canonical durable memory,
- Obsidian as interface,
- graph/indexes as derived data,
- local/browser state as non-authoritative,
- raw evidence distinct from confirmed knowledge,
- Discuss → Propose → Approve → Persist.

### 10. Make Brain location configurable

The architectural identity of the Brain should be stable, while its filesystem location is configuration rather than a hard-coded core assumption.

### 11. Make Council a structured review protocol

Council should be Unity-mediated fan-out/review/arbiter flow rather than an unrestricted agent chat room. Same-provider multi-role review is useful but should not be mistaken for independent model diversity.

### 12. Build an append-only audit/event ledger

A reproducible job should record state transitions, role/policy versions, context identifiers, provider/model, prompt/result hashes, tool activity, approvals, retries/fallbacks, token/cost data and timestamps.

### 13. Centralise execution budgets

Each job should have hard limits for role handoffs, model calls, tool calls, tokens, cost, elapsed time, retries and Council rounds. Child jobs consume the parent budget.

### 14. Use capability-based permissions

Roles define maximum eligibility. Each job receives only the concrete capabilities it needs, for example READ(project), WRITE(src), TEST(project), with privileged actions requiring explicit approval.

### 15. Migrate legacy code by strangler pattern

Keep legacy runtime quarantined. Build the new Unity gateway/control plane beside it, then migrate useful capabilities one by one through the new boundary. Do not retrofit scattered safety checks throughout old code and call that v2.

## Recommended checkpoint before further agent expansion

Build and agree these core components first:
1. State Machine
2. Policy Engine
3. Capability Engine
4. Budget Engine
5. Approval Engine
6. Append-only Audit/Event Ledger
7. Role Registry
8. Provider/Model Registry
9. Task Envelope and Result Packet
10. Tool Broker

## Core recommendation

The next breakthrough is not another AI agent. It is making Unity itself authoritative and non-bypassable. Once that is true, models and tools can genuinely remain replaceable workers beneath the system.
