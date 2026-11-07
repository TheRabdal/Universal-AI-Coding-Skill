# Strict Execution Policy

Default: no execution without explicit permission for the exact action.

Do not run project, server, build, compile, tests, benchmark, migrations, seed, formatter, generator, analyzer that executes code, package install/update/remove, scripts, Docker, CI, deployment, publishing, active scanners, fuzzing, or penetration tests.

Read-only inspection (read files, list directories, search text, inspect diffs) is allowed when safe.

If execution is needed, state the exact command, purpose, and side effects, then ask permission and wait. Permission for one command does not authorize other commands. Never claim unperformed verification.
