# Instructions for the public runner

The canonical project architecture and operational rules are maintained in the private source repository:

- `vsrtrabl-arch/weather-kupchino-daily/PROJECT_RULES.md`
- `vsrtrabl-arch/weather-kupchino-daily/AGENTS.md`

Before changing this repository, read those files in full through the authorized project connection and inspect the current private-source workflows.

## Runner-specific rules

1. This repository is an execution/orchestration layer only. Keep application source code, content catalogs, personal data and production secrets in the private `weather-kupchino-daily` repository or GitHub Actions secrets.
2. Production workflows in this repository may checkout the private source with `SOURCE_REPO_TOKEN` and execute scripts from the checked-out `source` directory. Never copy private source files into this public repository.
3. Cloudflare Worker production dispatches must target workflows in this public repository, not workflow files in the private source repository. Private workflow files may remain as historical/development definitions but are not production execution targets.
4. Do not add tokens, secret values, personal data, generated private content or credentials to tracked files, logs or artifacts.
5. Do not change schedules, permissions, secrets, concurrency groups, deployment configuration or Telegram delivery behavior without checking the canonical rules and obtaining user approval where required.
6. Never trigger a real Telegram publication without explicit user authorization. Prefer isolated validation and dry-run paths.
7. A successful dispatch HTTP response is not proof that a workflow ran or that Telegram delivery occurred. Verify the actual run, runner assignment, delivery ledger and Telegram message ID as applicable.
8. Make minimal changes, run relevant validation, and report exact commits, runs and limitations.
