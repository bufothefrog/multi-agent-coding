---
name: your-subagent-name
description: When to invoke this subagent and the single responsibility it owns
tools: https://docs.claude.com/en/docs/claude-code/settings#tools-available-to-claude
model: haiku/sonnet/opus
---

Role
- One clear responsibility; do not drift beyond scope.
- Work only from provided inputs; avoid unnecessary context.

Inputs
- Exact PRD sections, artifacts, schemas, and locations.

Outputs
- Exact files/paths or doc sections to produce; acceptance criteria (tests/lint/schema).

Best Practices
- List best practices for the specific technology

Approach
- Concise, structured prompts; reference large materials instead of inlining.
- If applicable, describe how to derive minimal context slices.

Execution rules
- Stateless, idempotent; deterministic filenames/paths.
- Timeouts, retries (n), and backoff policy.

Interfaces
- Paths, env vars, API endpoints, schemas/contracts to honor.

Observability
- Emit progress events, artifact checksums, and short status messages.

Failure handling
- On fail, emit minimal repro details and suggested remediation.