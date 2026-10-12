# ADR-004: External Embedding and Database Boundary

- **Status:** ACCEPTED
- **Date:** 2026-10-12
- **Scope:** Triminds VectorAI for Visual Studio Code

## Context

The extension generates embeddings through the Hugging Face Inference API and performs semantic search through PostgreSQL. The current source reads `vectorai.huggingfaceApiKey`, while the package configuration does not declare that setting. The PostgreSQL connector has placeholder defaults for user, database, and password.

These facts affect privacy, installation, and production readiness. The extension must not imply that embedding generation is fully local or that a default database configuration is ready for production.

## Decision

1. Treat embedding generation as an external data transfer to Hugging Face unless a local model provider is explicitly implemented and selected.
2. Document which text is sent to the embedding endpoint and advise users not to submit confidential code/text unless their organization's policy permits that provider.
3. Require explicit PostgreSQL configuration and a compatible `documents` schema/vector operator; placeholder defaults are development placeholders only.
4. Formalize the API-key setting and secret-handling mechanism before distribution. Do not place real keys in source control or documentation.
5. Describe query-improvement output as static guidance unless a real model call is implemented.
6. Claim build/test status only from an observed workflow run, not from workflow definitions or test files.

## Consequences

- The README states the external-provider and database boundaries.
- A follow-up implementation task remains for configuration schema and secret management.
- Privacy, provider behavior, database persistence, and release validation require separate tests.
