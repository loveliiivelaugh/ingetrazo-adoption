# Adoption baseline

Upstream: https://github.com/ingelibre/ingetrazo
Pinned source: e5c016e5df74a18204b785edd0a8401300cb4353
Prepared: 2026-10-17
Status: evaluation only; not approved for production or everyday host installation.

## Initial scope

Retain core desktop CAD/modeling, local document save/open and useful local import/export. Exclude bundled AI assistant, MCP bridge, Python console and runtime third-party plugin loading from the adoption build. Preserve model-info/inspection functionality only if it can be statically integrated without arbitrary plugin execution. Keep network-backed georeferencing/library features opt-in and off by default.

## Workflow

The main branch preserves the upstream fork. The adoption branch starts from the reviewed source revision and removes inherited GitHub workflows. Cloud agents must propose focused changes through a PR targeting adoption. No automatic merges, releases, package publishing, deployments, secrets or private-network access are configured by this bootstrap.

Maintain upstream attribution and license obligations. Record dependency versions, checks, removed features and remaining gaps. Review the actual distributed artifacts separately. A minimal source fork still needs runtime and target-platform validation before adoption. Future upstream updates require explicit review; do not automatically sync main into adoption.

## Implementation task

Implement the first minimal local-only IngeTrazo adoption build on top of this adoption branch. Read ADOPTION.md and AGENTS.md.

Retain useful desktop modeling, local save/open, basic materials and local import/export. Remove the bundled AI assistant, MCP bridge and Python console from the adoption build and UI. Disable arbitrary plugin discovery and importing, including the per-user plugin folder; exclude these execution surfaces from packaging as well as menus. Preserve useful model-info/solid-inspection behavior only through static trusted integration if practical. Never start a bridge listener or load legacy API credentials from QSettings in this build. Network-backed map/terrain/model-library features must be off by default and require explicit opt-in; the initial app should be usable offline. Do not add replacement telemetry or cloud integrations.

Add bounded archive/document handling (member count, expanded byte budgets and safe path handling), maintaining normal local document compatibility; document any supported-large-model limits. Review the dependency manifest and establish exact, reviewed runtime versions plus an inventory. Do not claim a CVE clearance without checking a fresh local advisory database. Do not download or execute unverified release binaries or native converters; clearly document any excluded converter capability. Preserve GPL notices and upstream attribution.

Work only on a PR branch. Use GitHub-hosted execution with synthetic files, no secrets, and no production access. Review repository setup before executing it. Use headless Qt/offscreen tests when possible. Add meaningful regression checks that plugin files do not execute, forbidden features/listeners are absent, offline-default behavior holds, and oversized archives fail safely. Run relevant geometry, serialization and import/export checks; distinguish headless checks from real macOS GUI/OpenGL validation. If CI is needed, use a read-only workflow with immutable action SHAs and no publishing. Provide a PR explaining features retained/removed, exact validation and adoption gaps. Do not merge or deploy. Do not post vulnerability details to upstream issues.
