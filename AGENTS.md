# AGENTS.md

## Communication

- Always reply in Korean unless the user explicitly requests another language.
- Keep answers direct and practical.
- Treat inspection, review, diagnosis, and explanation requests as analysis-only.
- Do not edit files unless the user explicitly requests implementation.
- For analysis-only requests, explain the cause, affected files, assumptions, and proposed fix without editing.
- An explicit implementation request already grants approval; do not ask for a second confirmation.
- Clearly distinguish verified facts from assumptions.

## Project

- This is a single-module Kotlin/JVM Spring Boot application built with Gradle.
- Production code is under `src/main/kotlin/com/example/spring_ai_tutorial`.
- Tests mirror the package structure under `src/test/kotlin`.
- Runtime configuration is in `src/main/resources/application.yml`.
- `monitoring/` contains Prometheus and Grafana configuration.
- `compose.yml` and `Dockerfile` define the application container.
- Preserve the existing package structure and project architecture.

## Architecture

- Keep HTTP mapping and request validation in controllers.
- Keep reusable business logic in services.
- Keep persistence and vector-store access in repositories.
- Keep transport models under `domain/dto`.
- Prefer existing services, repositories, DTOs, and response conventions.
- Do not duplicate business rules, validation, payload construction, or formatting logic.

## Kotlin Style

- Follow the Google Kotlin Style Guide and nearby project code.
- Use four-space indentation.
- Use `PascalCase` for types and `camelCase` for functions and properties.
- Use descriptive `*Controller`, `*Service`, `*Repository`, and `*Dto` names.
- Prefer one top-level type per file where practical.
- Do not introduce or change formatter/linter dependencies unless explicitly requested.
- Format changed Kotlin files with the IDE before committing.

## Commands

- Use `rg` first for searches.
- Use the Gradle wrapper:
    - `.\gradlew.bat test --tests <fully.qualified.TestClass>`
    - `.\gradlew.bat test`
    - `.\gradlew.bat build`
    - `.\gradlew.bat bootRun`
- Run focused tests before broad tests.
- Distinguish code failures from unavailable local infrastructure.
- The application requires `OPENAI_API_KEY`; never commit credentials.
- Actuator metrics are available on port `9091` under `/monitor`.

## Testing

- Use Spring Boot Test, JUnit 5, and Kotlin test support.
- Name test classes with the `Tests` suffix.
- Add focused service tests for business behavior.
- Add integration tests for endpoint or configuration changes.
- Do not claim verification succeeded unless the relevant command was executed.
- Report skipped or incomplete verification and its reason.

## Editing

- Preserve existing user changes.
- Keep changes narrowly scoped.
- Before editing, state the expected files and reasons.
- Explain before expanding the edit scope.
- Avoid unrelated refactoring, renaming, formatting, or dependency changes.
- After editing, list the changed files and verification performed.
- Never commit secrets, `.env` files, generated files, or unrelated changes.

## Git and Pull Requests

- Do not commit, push, open a PR, merge, or rewrite history unless explicitly requested.
- Use commit messages such as `[feat] 설명`, `[fix] 설명`, `[refactor] 설명`, and `[chore] 설명`.
- Keep each commit focused.
- Separate database migrations from application code commits.
- PRs must summarize motivation, changes, related issues, tests, and configuration updates.
- Include screenshots for UI or dashboard changes.
- Follow `.github/pull_request_template.md`.