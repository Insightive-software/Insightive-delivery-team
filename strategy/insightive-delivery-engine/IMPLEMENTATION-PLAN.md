# Insightive Delivery Engine Implementation Plan

**Status:** Draft v0.1  
**Date:** 2026-07-05

## Build Principle

Build the smallest hosted system that lets Insightive run a real project with agent assistance, human approval, cost control, and evidence-backed delivery.

Do not start by making every agent autonomous. Start by making the delivery process legible, governable, and repeatable.

## Phase 0: Repo Tuning

**Goal:** Turn the broad catalog into an Insightive-ready operating layer.

Tasks:

- [ ] Keep upstream role files unchanged unless a role is clearly wrong.
- [ ] Use `strategy/insightive-delivery-engine/` for Insightive-specific operating doctrine.
- [ ] Define the minimum delivery team and specialist bench.
- [ ] Define model routing and approval policy.
- [ ] Create project lifecycle templates that can be converted into Teamwork tasks.

Exit criteria:

- Umar can look at the repo and know which roles run by default.
- New projects can be routed without reading hundreds of agent files.

## Phase 1: Manual-Orchestrated Delivery

**Goal:** Use ChatGPT/Codex plus Teamwork MCP manually, but follow the operating rules.

Tasks:

- [ ] Create a Teamwork project/tasklist template for software delivery.
- [ ] Create a Teamwork project/tasklist template for website delivery.
- [ ] Create a Teamwork project/tasklist template for automation/integration delivery.
- [ ] Define standard statuses, milestones, dependencies, and approval gates.
- [ ] Draft AgentMail message templates for client questions, status updates, and decision requests.
- [ ] Use local models manually for low-risk summaries and extraction where practical.

Exit criteria:

- One real project can be run with Teamwork task graph, dependencies, approvals, and status updates.
- Umar approves all external communication.

## Phase 2: Hosted Intake And Approval Queue

**Goal:** Build the first hosted service that receives inputs and controls approvals.

Minimum components:

- Chainlit internal operator console.
- Intake form/API for Umar, client, and team inputs.
- Request normalizer.
- Approval queue.
- Teamwork sync worker.
- Audit log.
- Cost ledger.

Suggested stack:

- Internal UI: Chainlit for first operator console.
- Web app: Next.js or FastAPI.
- Database: Postgres.
- Queue: Redis/BullMQ, Celery, or a managed queue.
- Object storage: S3-compatible storage for files/evidence.
- Model runtime: Ollama for local/small models; paid provider gateway for frontier models.

Exit criteria:

- Inputs become structured requests.
- Approved requests can create/update Teamwork tasks.
- Every agent/tool run has an audit entry and estimated cost.
- Team members can use Chainlit to submit requests, review approvals, and inspect agent runs.

## Phase 3: Agent Runner

**Goal:** Run selected Insightive roles as controlled jobs.

Tasks:

- [ ] Implement role registry from the minimum delivery team.
- [ ] Add job types: intake triage, scope draft, task breakdown, dependency planning, QA review, status draft.
- [ ] Add model routing policy.
- [ ] Add tool permission scopes per role.
- [ ] Add retry and partial failure handling.
- [ ] Add evidence attachments to Teamwork.

Exit criteria:

- Agents can draft and update internal delivery artifacts.
- High-risk actions route to approval.
- Failed tool calls are visible and recoverable.

## Phase 4: AgentMail And External Communication

**Goal:** Let agents prepare formal external communication with approval.

Tasks:

- [ ] Connect AgentMail.
- [ ] Add outbound message approval.
- [ ] Add client/person/project context injection.
- [ ] Add message templates.
- [ ] Add audit trail for sent messages.

Exit criteria:

- Agents can draft client emails.
- Umar can approve/edit/send.
- Sent messages are linked to project/task/request records.

## Phase 5: Guarded Automation

**Goal:** Automate repeated low-risk actions after enough evidence.

Candidates:

- Internal task cleanup.
- Routine status comments.
- Meeting note summarization.
- Duplicate request detection.
- QA checklist creation.
- Client update drafts.
- Staging deployment checks.

Still approval-gated:

- Production deployment.
- Client commitments.
- Budget or scope changes.
- Legal/security-sensitive messages.
- Vendor purchases.
- Destructive data/code operations.

## Data Model Sketch

Core records:

- `clients`
- `people`
- `projects`
- `requests`
- `decisions`
- `tasks`
- `artifacts`
- `approvals`
- `agent_runs`
- `tool_calls`
- `model_usage`
- `messages`
- `risks`
- `evidence`

Important fields:

- `source`: Umar, client, team, email, Teamwork, upload, system.
- `authority_level`: draft, internal, client-visible, external-send, production.
- `approval_status`: not_required, pending, approved, rejected, expired.
- `cost_center`: project/client/internal.
- `model_route`: local, paid-small, paid-frontier.
- `confidence`: low, medium, high.

## First Real Workflow

Use Malco-style software delivery as the first reference workflow.

1. Intake comes from Umar/client/team.
2. Product Analyst creates scope and acceptance criteria.
3. Solution Architect creates approach and risks.
4. Delivery Producer creates Teamwork task graph and dependencies.
5. Umar approves plan.
6. Implementation Lead executes or delegates specialist work.
7. QA Reality Gate verifies evidence.
8. Client Comms Agent drafts status/update.
9. Umar approves external message.
10. System records cost, time, outcome, and lessons.

## Metrics To Track From Day One

- Cost per request.
- Cost per project phase.
- Paid vs local model usage.
- Approval rejection rate.
- Tool failure rate.
- Task rework rate.
- QA pass/fail rate.
- Client response time.
- Cycle time from intake to approved task graph.
- Cycle time from task start to verified done.

## Immediate Next Decisions

1. Hosted stack: Next.js worker app, FastAPI worker app, or another base.
2. Model runtime: Ollama first, vLLM first, or both.
3. Input channels for v0: web form, AgentMail, Teamwork comments, or all three.
4. Whether Teamwork becomes the single PM surface or the agent/client PM surface while ClickUp remains internal.
5. The first project template to formalize: software delivery, website delivery, or automation delivery.
