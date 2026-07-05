# ADR-0001: Hosted Agentic Delivery Engine For Insightive

**Status:** Proposed  
**Date:** 2026-07-05  
**Deciders:** Umar / Insightive

## Context

Insightive is a software house that receives varied work: websites, web apps, automation, integrations, marketing, AI/data tasks, and client operations. The current repo is a broad catalog of agent role prompts. It is useful as a role library, but it is not yet a delivery engine.

The target system needs:

- A minimum delivery team that can handle most projects.
- Inputs from Umar, clients, and team members.
- A hosted server so work can run continuously and be observable.
- Project management with dependency support.
- Formal external communication, potentially through AgentMail.
- Cost control through local models and paid model routing.
- Human approval at first, with increasing automation over time.

Teamwork MCP has been live-tested in this environment. It can create tasklists, tasks, and task predecessor dependencies, including updating dependencies after task creation.

## Decision

Build Insightive's first delivery engine as a hosted orchestration layer on top of:

1. This repo as the role catalog and operating doctrine.
2. Teamwork MCP as the first project/task/dependency control plane.
3. A hosted Intake Gateway and Approval Queue.
4. A Model Gateway that routes routine work to local models and high-risk work to paid frontier models.
5. AgentMail as the external communication adapter, gated by approval in early phases.
6. An audit and cost ledger for every agent run.

The engine should not start as a fully autonomous company. It should start as a semi-autonomous delivery team that drafts, plans, routes, executes, verifies, and asks for approval at the right points.

## Options Considered

### Option A: Use Teamwork MCP plus hosted orchestration

| Dimension | Assessment |
|---|---|
| Complexity | Medium |
| Cost | Medium, controllable through model routing |
| Scalability | Good for agency delivery workflows |
| Team familiarity | Good after initial setup |

**Pros:**

- Teamwork MCP already supports dependency writes.
- Fits traditional project management expectations.
- Can serve as both internal and client-facing surface where appropriate.
- Hosted orchestrator can add approvals, cost control, memory, and custom routing.

**Cons:**

- Requires building an engine around Teamwork rather than relying on Teamwork alone.
- MCP/tool latency can be high.
- Some workflows may still require direct API or browser fallback.

### Option B: Use ClickUp as the main agentic PM system

| Dimension | Assessment |
|---|---|
| Complexity | Low to Medium |
| Cost | Low if already subscribed |
| Scalability | Good for internal execution |
| Team familiarity | Existing familiarity |

**Pros:**

- Already used internally.
- Strong task/document flexibility.
- Good internal workflow surface.

**Cons:**

- Client expectations may prefer more traditional PM views.
- Dependency behavior and Gantt-style client monitoring were not the best fit for Malco-style delivery.
- ClickUp Brain/Super Agents are useful, but not enough as the governed company engine by themselves.

### Option C: Build the whole PM and workflow system from scratch

| Dimension | Assessment |
|---|---|
| Complexity | High |
| Cost | High upfront |
| Scalability | High eventually |
| Team familiarity | Low until built |

**Pros:**

- Full control over workflow, permissions, audit, and agent execution.
- Can become part of SMEFoundation later.

**Cons:**

- Too slow for the immediate delivery team need.
- Rebuilds project management basics before proving agent workflow.
- Higher risk of building infrastructure before discovering the real operating model.

## Trade-Off Analysis

Teamwork MCP plus a hosted orchestration layer is the best first move. It avoids building PM primitives from scratch while still giving Insightive a place to add the missing company-engine pieces: intake, approvals, model routing, audit, memory, and controlled external communication.

ClickUp can remain useful for internal work where it is already comfortable, but Teamwork should be the first tested surface for agent-controlled schedules because dependency creation and dependency update worked through MCP.

## Consequences

What becomes easier:

- Agents can create and update real project tasks and dependency chains.
- Client-facing traditional project plans become easier to maintain.
- Approval and cost controls can be built outside any single PM tool.
- The role catalog can stay clean while Insightive-specific operating rules live in `strategy/insightive-delivery-engine/`.

What becomes harder:

- The hosted orchestrator must become the source of governance rather than relying on Teamwork alone.
- We need robust error handling for MCP latency, partial failures, duplicate tasks, and API/tool drift.
- We need cost and quality telemetry from the beginning to tune model routing.

What to revisit:

- Whether Teamwork should replace ClickUp internally or remain the client/agentic PM layer.
- Whether AgentMail should send approved messages automatically or only prepare drafts.
- Whether SMEFoundation should eventually absorb this engine as a formal module.

## Action Items

1. [ ] Define the canonical Insightive project lifecycle in Teamwork.
2. [ ] Create an intake schema for client/Umar/team requests.
3. [ ] Build the approval queue model.
4. [ ] Define model routing policy and per-project budget guardrails.
5. [ ] Create the first hosted orchestrator prototype.
6. [ ] Run one real MalcoProp slice through the system.
7. [ ] Record cost, latency, approval rejection, task quality, and QA evidence metrics.
