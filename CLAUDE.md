# amend-topics

## Commands (exact; no alternatives)

| Task | Command |
| --- | --- |
| All gates | `./gradlew check` |
| Fast tests (no Docker) | `./gradlew test` |
| Integration tests | `./gradlew integrationTest` |
| Format | `./gradlew spotlessApply` |
| CLI image (local) | `./gradlew :cli:jibDockerBuild` |
| Demo up / down | `docker compose up -d --wait` / `docker compose down -v` |
| Seed fixtures | `./gradlew :testkit:run --args="seed …"` |

## Run & Debug

- Use the `/run` skill (`.claude/skills/run-amend-topics/`) to run, verify, and debug locally.

## Conventions

- Build tool: Gradle only, via the wrapper (`./gradlew`). NEVER add Maven build files.
- Config files are YAML (`application.yaml`, rules, compose, workflows). `.properties` only where a tool mandates it
  (`gradle.properties`).

## Git & GitHub

- NEVER commit or push to `main`. One change → one branch → one PR.
- Branch: `<type>/<slug>`, or `<type>/<issue#>-<slug>` when an issue exists. Commits and PR titles: Conventional
  Commits.
- PR body: what and why; `Closes #<n>` when an issue exists. Open via `gh pr create`.
- Bug found after merge → `gh issue create` (repro, `bug` label) before fixing.
- Releases only on explicit request: `gh release create vX.Y.Z --generate-notes`. NEVER push tags directly.
- NEVER force-push.

## Publication

- Every outward-facing action (push, PR, issue, comment, review, release, repo settings) requires maintainer approval
  of the exact content. `.claude/settings.json` enforces a confirmation prompt for each.

## Decisions

- Read `docs/adr/` before changing an area an ADR covers. Accepted ADRs are deliberate: propose a superseding ADR;
  never silently revert.

## Environment

- No package installs or environment provisioning; ask the maintainer.
- No blocking foreground processes; compose always runs with `-d`.
- Versions: Gradle from `gradle/wrapper/gradle-wrapper.properties`; Java toolchain and `release` levels in
  `build-logic/`; Spring Boot, libraries, and the Kafka image tag in `gradle/libs.versions.toml`; the dev container
  base image in `.github/devcontainer-image/Dockerfile`. Read these instead of guessing or probing.

## PR Review (on request only)

- Gather: `gh pr view <n>`, `gh pr diff <n>`, open CodeRabbit threads.
- Evaluate against `docs/review-checklist.md` and `docs/adr/`.
- Output: table | Check | Status | Notes | — ✅ pass, ⚠️ warn, ❓ inconclusive, ➖ n/a. Notes cite file:line.
- Post to the PR only when asked: `gh pr comment <n> --body-file -`.
