# Insightive Curated Agent Roster

**Status:** Draft v0.1  
**Purpose:** Define the minimum practical agent set Insightive should activate from this repo.

This file is the human-readable companion to `agent-manifest.json`. The repo can keep the full upstream catalog, but the hosted Insightive delivery engine should load only this curated set unless Umar explicitly enables a specialist.

## Principles

1. Keep the upstream catalog intact for easy updates.
2. Curate at runtime instead of deleting source agents.
3. Keep always-on roles small.
4. Use specialists only when a project type requires them.
5. Prefer agents that map to real Insightive delivery work: websites, Shopify, software, automation, marketing, QA, PM, finance, and governance.

## Always-On Delivery Team

| Role | Agent file | Why active |
|---|---|---|
| Delivery Producer | `project-management/project-management-studio-producer.md` | Owns project flow, stakeholders, dependencies, and delivery cadence |
| Senior PM | `project-management/project-manager-senior.md` | Converts scope into actionable tasks and acceptance criteria |
| Project Shepherd | `project-management/project-management-project-shepherd.md` | Tracks blockers, follow-ups, and handoffs |
| Product Manager | `product/product-manager.md` | Clarifies problem, goals, non-goals, and success metrics |
| Solution Architect | `engineering/engineering-software-architect.md` | Owns architecture decisions and technical trade-offs |
| Senior Developer | `engineering/engineering-senior-developer.md` | General implementation lead |
| Minimal Change Engineer | `engineering/engineering-minimal-change-engineer.md` | Keeps edits scoped and avoids unnecessary rewrites |
| Code Reviewer | `engineering/engineering-code-reviewer.md` | Reviews implementation risk and maintainability |
| DevOps Automator | `engineering/engineering-devops-automator.md` | Handles deployment, automation, CI/CD, and environment tasks |
| SRE | `engineering/engineering-sre.md` | Reliability, monitoring, incident-readiness |
| QA Reality Checker | `testing/testing-reality-checker.md` | Prevents fantasy approvals and requires evidence |
| API Tester | `testing/testing-api-tester.md` | Verifies APIs and integrations |
| Evidence Collector | `testing/testing-evidence-collector.md` | Captures proof for approvals and client updates |
| Client Comms | `support/support-support-responder.md` | Drafts client responses and follow-ups |
| Executive Summary Generator | `support/support-executive-summary-generator.md` | Creates short stakeholder summaries |
| Chief of Staff | `specialized/specialized-chief-of-staff.md` | Helps coordinate cross-project priorities and operating rhythm |
| Agents Orchestrator | `specialized/agents-orchestrator.md` | Plans multi-agent workflows |
| Automation Governance Architect | `specialized/automation-governance-architect.md` | Defines approval, safety, and autonomy rules |

## Software Delivery Bench

| Role | Agent file |
|---|---|
| Backend Architect | `engineering/engineering-backend-architect.md` |
| Frontend Developer | `engineering/engineering-frontend-developer.md` |
| Database Optimizer | `engineering/engineering-database-optimizer.md` |
| Data Engineer | `engineering/engineering-data-engineer.md` |
| AI Engineer | `engineering/engineering-ai-engineer.md` |
| AI Data Remediation Engineer | `engineering/engineering-ai-data-remediation-engineer.md` |
| Prompt Engineer | `engineering/engineering-prompt-engineer.md` |
| Technical Writer | `engineering/engineering-technical-writer.md` |
| AppSec Engineer | `security/security-appsec-engineer.md` |
| Security Architect | `security/security-architect.md` |

## Website And E-Commerce Bench

| Role | Agent file | Source |
|---|---|---|
| Astro Web Developer | `engineering/engineering-astro-web-developer.md` | Local Pi skill + repo frontend conventions |
| Shopify Website Developer | `engineering/engineering-shopify-website-developer.md` | Local Pi skill + repo delivery conventions |
| Shopify App Developer | `engineering/engineering-shopify-app-developer.md` | Local Pi skill + repo architecture/security conventions |
| UX Architect | `design/design-ux-architect.md` | Repo |
| UI Designer | `design/design-ui-designer.md` | Repo |
| Brand Guardian | `design/design-brand-guardian.md` | Repo |
| Image Prompt Engineer | `design/design-image-prompt-engineer.md` | Repo |
| CMS Developer | `engineering/engineering-cms-developer.md` | Repo |

## Marketing And Growth Bench

| Role | Agent file |
|---|---|
| Content Creator | `marketing/marketing-content-creator.md` |
| SEO Specialist | `marketing/marketing-seo-specialist.md` |
| AEO Foundations | `marketing/marketing-aeo-foundations.md` |
| Agentic Search Optimizer | `marketing/marketing-agentic-search-optimizer.md` |
| AI Citation Strategist | `marketing/marketing-ai-citation-strategist.md` |
| Email Strategist | `marketing/marketing-email-strategist.md` |
| LinkedIn Content Creator | `marketing/marketing-linkedin-content-creator.md` |
| Social Media Strategist | `marketing/marketing-social-media-strategist.md` |
| PR Communications Manager | `marketing/marketing-pr-communications-manager.md` |
| Growth Hacker | `marketing/marketing-growth-hacker.md` |
| Paid Media Tracking Specialist | `paid-media/paid-media-tracking-specialist.md` |
| PPC Strategist | `paid-media/paid-media-ppc-strategist.md` |
| Paid Social Strategist | `paid-media/paid-media-paid-social-strategist.md` |

## Sales, Finance, And Operations Bench

| Role | Agent file |
|---|---|
| Sales Discovery Coach | `sales/sales-discovery-coach.md` |
| Sales Proposal Strategist | `sales/sales-proposal-strategist.md` |
| Sales Account Strategist | `sales/sales-account-strategist.md` |
| Sales Engineer | `sales/sales-engineer.md` |
| Finance Tracker | `support/support-finance-tracker.md` |
| Bookkeeper Controller | `finance/finance-bookkeeper-controller.md` |
| Financial Analyst | `finance/finance-financial-analyst.md` |
| FP&A Analyst | `finance/finance-fpa-analyst.md` |
| Business Strategist | `specialized/business-strategist.md` |
| Operations Manager | `specialized/operations-manager.md` |
| Pricing Analyst | `specialized/specialized-pricing-analyst.md` |
| Legal Compliance Checker | `support/support-legal-compliance-checker.md` |

## Archive By Default

These remain in the upstream catalog but should not be active for Insightive by default:

- `academic/`
- `game-development/`
- `gis/`
- `spatial-computing/`
- Most China-specific marketing agents
- Blockchain, zk, and Solidity agents unless a project needs them
- Healthcare, hospitality, real-estate, loan-officer, study-abroad, and government niche agents
- Embedded firmware, network engineering, WeChat, and Feishu agents unless a client requires them

## Additions From Local Pi Skills

The following Insightive agents were created by blending Umar's local Pi skills with this repo's agent style:

- `engineering/engineering-shopify-website-developer.md`
- `engineering/engineering-shopify-app-developer.md`
- `engineering/engineering-astro-web-developer.md`

These should be treated as first-class Insightive delivery capabilities.
