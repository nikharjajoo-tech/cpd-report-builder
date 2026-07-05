# Lessons learned and future improvements

## What worked
**Standardizing quality mechanically, not through more review.** The AI validation agent caught tone and structure issues before a human reviewer ever saw them, which meant senior reviewer time went toward genuine judgment calls instead of mechanical consistency checks.

**Structured threshold testing over anecdotal bug reports.** Finding the exact 100MB and roughly 1,000-page ingestion failure point through deliberate testing got engineering a precise problem to solve, rather than a vague "large files sometimes fail" ticket.

**Chapter-by-chapter generation.** Keeping each section independently groundable made both AI quality issues and citation errors far easier to isolate than they would have been in a single full-report generation pass.

## What I'd do differently
**Build the re-ingestion cadence in from the start.** What happens when a project document is revised mid-engagement was an open question discovered after launch rather than designed for up front.

**Track reviewer edit rate as a standing metric.** Draft quality was validated mostly through prompt benchmarking and reviewer feedback in the moment, rather than a persistent dashboard metric that would show quality trends over time.

## Future improvements
- **Automated report formatting templates**, so chapter content and document formatting are handled by the same pipeline.
- **Multi-engagement comparative analytics** for product leadership, to see where AI-assisted drafting is saving the most time across the firm.
- **Expanded ingestion limits** beyond 300MB as document archives grow.

## The broader takeaway
Compressing a multi-month manual process safely required knowing exactly which parts of the workflow needed to stay human. The validation agent and reviewer approval gate were not slowdowns bolted onto a fast system, they were what made the speed trustworthy enough for a client to accept.
