# 🧠 Triminds VectorAI for Visual Studio Code

<img width="1024" height="1024" alt="vectorPlugin" src="https://github.com/user-attachments/assets/0e57484a-e59a-4f10-86b8-8af35b3b6b69" />

![VS Code](https://img.shields.io/badge/VS%20Code-Extension-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue)
![AI](https://img.shields.io/badge/Artificial%20Intelligence-Developer%20Tools-success)
![Embeddings](https://img.shields.io/badge/Vector-Embeddings-purple)
![MIT](https://img.shields.io/badge/License-MIT-yellow)

## AI-Powered Developer Assistant for Visual Studio Code

**Triminds VectorAI** is an AI-powered Visual Studio Code extension that enhances developer productivity through semantic search, embedding generation and intelligent code assistance directly inside the editor.

Unlike the enterprise applications in the Triminds ecosystem, **VectorAI is a standalone developer tool**. It is designed to assist software engineers building modern AI applications, including the Triminds products themselves.

---

# 🌐 Part of the Triminds Ecosystem

Triminds VectorAI is one of the engineering tools developed within the **Triminds** ecosystem.

Rather than consuming services from the Triminds Platform, VectorAI supports the development of the entire ecosystem by providing AI-assisted coding capabilities directly inside Visual Studio Code.

```text
                    Triminds

          ┌────────────────────────────┐
          │                            │
  Enterprise Products          Developer Tools
          │                            │
          │                    Triminds VectorAI
          │
   ├── Platform UI
   ├── Geo AI
   ├── Security
   ├── SmartImageLab
   └── ObjectScanner
```

This distinction allows VectorAI to remain completely independent while contributing to the productivity and quality of all Triminds projects.

---

# 🚀 Overview

VectorAI brings modern AI capabilities directly into the development environment through semantic search, vector embeddings and intelligent developer assistance.

The extension targets developers building applications involving:

* Large Language Models (LLMs)
* Retrieval-Augmented Generation (RAG)
* Vector Databases
* Semantic Search
* AI-powered Software Engineering
* PostgreSQL + pgvector
* Embedding-based Architectures

Built with TypeScript and the Visual Studio Code Extension API, VectorAI integrates modern AI models with a lightweight and extensible architecture.

---

# ✨ Features

## 🧠 Embedding Generation

Generate vector embeddings directly from selected code or text.

Capabilities include:

* Semantic indexing
* Embedding generation
* AI-ready document processing
* Knowledge retrieval preparation

---

## 🔍 Semantic Search

Search code and documentation using vector similarity instead of keyword matching.

Supports:

* Vector databases
* pgvector
* RAG pipelines
* AI-powered documentation search

---

## 💡 AI Optimization Suggestions

Receive AI-powered recommendations for improving developer workflows.

Examples:

* SQL optimization
* Prompt improvement
* Query suggestions
* Documentation enhancement
* Code quality recommendations

---

## ⚡ Native Visual Studio Code Integration

Integrated seamlessly into VS Code through:

* Command Palette
* Context Menus
* Notifications
* Extension Commands
* Editor Actions

---

# 🏗 Architecture

```text
VectorAI Extension

│

├── VS Code Commands

├── AI Services

├── Embedding Engine

├── Database Connectors

├── Provider Abstraction

└── Logging
```

```text
src/

├── extension.ts

├── commands/
│   ├── generateEmbedding.ts
│   ├── semanticSearch.ts
│   └── suggestOptimization.ts
│
├── services/
│   ├── huggingfaceService.ts
│   ├── dbConnector.ts
│   └── VectorAIService.ts
│
├── utils/
│   └── logger.ts
│
├── tests/
│
└── mocks/
```

---

## Implementation and data boundary

The current source code has these important operational boundaries:

- Embedding generation sends the supplied text to the Hugging Face Inference API endpoint for `sentence-transformers/all-MiniLM-L6-v2`. Do not assume that source text stays on the local machine.
- Semantic search uses a PostgreSQL client and queries a `documents` table with an embedding-distance operator. A working database, schema, compatible vector type/index, and valid credentials are required.
- The database connector currently contains placeholder default values for the user, database, and password. Configure valid values explicitly; the placeholders are not production credentials.
- The embedding service reads `vectorai.huggingfaceApiKey`, but the inspected `package.json` contributes only the database host and port settings. The Hugging Face key setting and secret-handling approach should be formalized before public distribution.
- The query-improvement command returns a fixed guidance string; it is not an LLM-generated optimization result.
- CI defines lint, compile, tests, and VSIX packaging. Workflow definitions and test files do not prove that a specific release passed.

See [ADR-001: External embedding and data boundary](docs/ADR-004-external-embedding-and-data-boundary.md).

# 🎯 Architectural Principles

* Modular Design
* Separation of Concerns
* Provider Abstraction
* AI Service Isolation
* Testability
* Extensibility
* Developer-First Experience

Architecture decisions are documented through ADRs (Architecture Decision Records).

---

# ⚙ Available Commands

| Command                        | Description                                      |
| ------------------------------ | ------------------------------------------------ |
| `vectorAI.generateEmbedding`   | Generate vector embeddings from selected content |
| `vectorAI.semanticSearch`      | Execute semantic similarity searches             |
| `vectorAI.suggestOptimization` | Generate AI-powered recommendations              |

---

# 🛠 Technology Stack

## Core

* TypeScript
* Node.js
* Visual Studio Code Extension API

## Artificial Intelligence

* Hugging Face Models
* Sentence Embeddings
* Semantic Search
* Vector Similarity

## Database

* PostgreSQL
* pgvector

## Testing

* Jest
* ts-jest
* VS Code API Mocks

## Tooling

* ESLint
* TypeScript Compiler
* VSCE Packaging
* GitHub Actions

---

# 🌟 Role within the Triminds Ecosystem

Unlike the enterprise applications developed by Triminds, **VectorAI is an engineering productivity tool**.

Its mission is to accelerate the development of AI solutions by providing intelligent capabilities directly inside the IDE.

As new Triminds products evolve, VectorAI evolves alongside them—helping developers build, test and maintain high-quality software through reusable AI-assisted workflows.

This independent architecture allows VectorAI to be adopted in any software project, whether inside or outside the Triminds ecosystem.
