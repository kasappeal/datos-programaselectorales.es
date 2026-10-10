# datos — programas electorales

Public dataset for [programaselectorales.es](https://programaselectorales.es).
This repo is data, not code. Point the site/collector at a checkout of it with
`PROGRAMAS_DATA_DIR=/path/to/this/repo`.

- **`registry.yaml`** — curated: elections → parties → documents → sources.
  Human-maintained; `document.id` is the join key and must be unique.
- **`observations/*.jsonl`** — append-only. One JSON object per check we run
  (timestamp, HTTP status, content type, size, `sha256_bytes`, `sha256_text`).
  **Never rewrite or reorder these files.** The history is the audit trail.

We publish facts *about* documents, never the documents. Original payloads and
extracted per-page text live in a private archive (Cloudflare R2), not here.
The site always links to the party's own URL.

Schema and validation live in the code repo (`@programas/core`). Timestamps are
platform detection times, not party publication dates — see the methodology page.
