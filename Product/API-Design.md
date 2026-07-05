# API design

## Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/v1/auth/login` | Authenticate user |
| GET | `/api/v1/engagements` | List engagements the user has access to |
| POST | `/api/v1/engagements/{id}/documents/sync` | Trigger SharePoint document sync for an engagement |
| GET | `/api/v1/engagements/{id}/documents` | List ingested documents and status |
| POST | `/api/v1/engagements/{id}/chapters/generate` | Generate a chapter draft grounded in the engagement corpus |
| GET | `/api/v1/chapters/{id}` | Retrieve a chapter draft, including citations |
| PUT | `/api/v1/chapters/{id}` | Save an edit to a chapter, creating a new version |
| GET | `/api/v1/chapters/{id}/versions` | Retrieve version history for a chapter |
| POST | `/api/v1/chapters/{id}/validate` | Run the AI validation agent against a chapter |
| POST | `/api/v1/chapters/{id}/approve` | Record reviewer approval for a chapter |
| GET | `/api/v1/reports/{id}/export` | Export a finalized report |
| GET | `/api/v1/admin/ingestion-status` | Retrieve ingestion monitoring data (admin only) |

## Design principles
- **Engagement scoping is enforced at the API layer, not just the UI.** Every document, chapter, and version request is scoped to an engagement ID the requesting user has access to, so cross-client data isolation cannot be bypassed by a direct API call.
- **Validation is a separate, explicit step from generation.** `/chapters/{id}/validate` is its own endpoint rather than an automatic side effect of generation, so it can be re-run after an edit without regenerating the chapter itself.
- **Approval is a distinct, logged action.** `/chapters/{id}/approve` records who approved a chapter and when, since that record is what makes the human-in-the-loop guarantee auditable rather than just a described process.

See the [data model and entity relationship diagram](../Architecture/er-diagram.md) for how these endpoints map to underlying entities.
