# Product decisions

## 1. Isolating the vector index per engagement
**The call:** each client engagement gets its own retrieval scope, rather than a single shared knowledge base across all engagements.

**Why:** cross-client confidentiality is not negotiable in a consulting context. A shared index risks one client's project details surfacing in another client's report.

**Trade-off accepted:** loses any potential efficiency from cross-engagement pattern reuse. Worth it, because the isolation guarantee protects the firm's core client relationships.

## 2. Making the AI validation agent a required gate
**The call:** every AI-generated chapter must pass an automated tone, structure, and consistency check before a human reviewer sees it.

**Why:** early testing showed generated chapters varied enough in tone and structure that human reviewers were spending time catching mechanical inconsistencies rather than making genuine judgment calls.

**Trade-off accepted:** adds a processing step to every chapter. Worth it, because it freed senior reviewer time for the parts of the job that actually need a senior reviewer.

## 3. Chapter-by-chapter generation instead of a single full-report pass
**The call:** generate a roughly 125-page report section by section, not in one continuous pass.

**Why:** a single massive generation pass makes citation accuracy much harder to verify, and any single error is harder to isolate and fix.

**Trade-off accepted:** requires more orchestration to stitch chapters into one coherent final report. Worth it, because it kept every section independently groundable and reviewable.

## What I'd reconsider
I would build the re-ingestion cadence for mid-engagement document revisions into the MVP, rather than treating it as an open question that surfaced after launch. See [Lessons Learned](./Lessons-Learned.md).
