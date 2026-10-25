# Public HTTPS Mailroom Agent

FastAPI service implementing the `ga5-mailroom-action-gate/v2` propose/commit contract.

## Required environment

- `AIPIPE_TOKEN`: model API token (set as a deployment secret; do not commit it).
- `AIPIPE_BASE_URL`: defaults to `https://aipipe.org/openrouter/v1`.
- `AI_MODEL`: defaults to `openai/gpt-4.1-nano`.
- `DB_PATH`: defaults to `/data/mailroom_agent.sqlite3`; use persistent storage in deployment.

The POST endpoint is `/` (also accepts `/v1` and `/v2` for convenience). The public service URL must be HTTPS and must not include credentials, query parameters, or a fragment.

Only a cryptographically verified receipt can produce a terminal `executed` outcome. The service records the grader's receipt and outcome; it does not send mail or perform external side effects itself.
