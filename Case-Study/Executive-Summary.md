# Executive summary

## The problem
An environmental consulting firm produced Continuing Professional Development reports through a fully manual process. Consultants spent 2 to 4 months per report manually reviewing hundreds of project documents and drafting content from scratch, with both quality and timeline tied to senior subject matter expert availability.

## My role
I owned this end to end as Project Manager / Associate Product Manager, leading a 15-member cross-functional team (development, AI/ML, QA, BA, DevOps, UI/UX) through 11 two-week Agile sprints. I ran requirements workshops with 6 client stakeholders, translated requirements into 200+ Jira stories, and coordinated UAT through to production release.

## What we built
A greenfield RAG platform on AWS using Anthropic Claude, ingesting 500 to 600 project documents per engagement from SharePoint and generating citation-grounded report chapters. Every AI-generated chapter passes through an AI validation agent for tone and structure consistency, then a human reviewer, before it can be marked final.

## Why it mattered
Speed without rigor would have damaged client trust. The platform had to compress the slowest part of the workflow, first-draft creation, without removing human judgment from the parts that require it.

## Impact at a glance
| Metric | Result |
|---|---|
| First-draft turnaround | 2 to 4 months down to 3 to 5 days (~90 to 95% faster) |
| Document ingestion limit | 100MB scaled to 300MB (3x improvement) |
| Documents processed per engagement | 500 to 600 |
| Team delivering | 15 cross-functional members, 200+ Jira stories, 11 sprints |
| Stakeholders aligned | 6 client stakeholders |

See the [full PRD](../PRD/Product-Requirements-Document.md) for complete requirements and architecture, or [Product Decisions](./Product-Decisions.md) for the reasoning behind the platform's hardest calls.
