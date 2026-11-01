# MCP & LLM Gateway Engineering Assessment

### Python • Model Context Protocol • LLM Infrastructure • Security • Reliability

A collection of four self-contained Python engineering projects demonstrating practical approaches to building secure, reliable, and production-minded infrastructure for MCP servers and LLM applications.

Each task is independently runnable and includes implementation code, automated tests, dependency management, and technical documentation.

---

## 📌 Project Overview

| Task | Project | Key Engineering Focus |
|---|---|---|
| 01 | MCP Server | Strict input validation & stdio transport |
| 02 | MCP Gateway | Tool-level authorization & secure proxying |
| 03 | Streaming Guardrail | Real-time PII detection & redaction |
| 04 | Rate Limit Router | Token-aware rate limiting & model fallback |

---

## 🏗️ Architecture at a Glance

```text
                    ┌──────────────────────┐
                    │     MCP / LLM Client │
                    └──────────┬───────────┘
                               │
              ┌────────────────┴────────────────┐
              │                                 │
      ┌───────▼────────┐               ┌────────▼─────────┐
      │  MCP Server    │               │   MCP Gateway   │
      │ Input Validation│              │ Tool-Level Auth  │
      └────────────────┘               └──────────────────┘

              ┌────────────────┐        ┌──────────────────┐
              │ Streaming      │        │ Rate Limit       │
              │ PII Guardrail  │        │ & Model Router   │
              └────────────────┘        └──────────────────┘
```

---

## 🚀 Task 01 — MCP Server with Strict Input Validation

**Directory:** `task1_mcp_server/`

Implements an MCP server over stdio with strict input validation to ensure incoming tool requests conform to expected schemas and constraints.

**Key features**
- MCP tool registration and execution
- Strict validation of incoming tool arguments
- Stdio-based MCP communication
- Error handling for invalid inputs
- Automated server and end-to-end tests

**Engineering consideration:** Uses the MCP SDK 1.x decorator-based server API, pinned to `mcp<2` for compatibility.

---

## 🔐 Task 02 — MCP Proxy Gateway with Tool-Level Authorization

**Directory:** `task2_mcp_gateway/`

Implements an MCP proxy gateway that filters tool access based on authorization rules before forwarding requests to a downstream server.

**Key features**
- MCP proxy and tool forwarding
- Tool-level authorization filtering
- Controlled access to downstream capabilities
- Deterministic mock downstream server
- Automated gateway tests

**Engineering consideration:** Separates authorization from tool execution to provide a clear security boundary between the client and downstream MCP server.

---

## 🛡️ Task 03 — Streaming LLM Proxy with Real-Time PII Redaction

**Directory:** `task3_streaming_guardrail/`

Implements a streaming LLM proxy that inspects generated content and redacts personally identifiable information (PII) before forwarding the response to the client.

**Key features**
- Streaming response processing
- Real-time PII detection and redaction
- Proxy-based response interception
- Deterministic mock LLM provider
- Automated redaction and streaming end-to-end tests

**Engineering consideration:** Demonstrates privacy-aware response handling while preserving the streaming behavior expected by LLM applications.

---

## ⚡ Task 04 — Token Rate Limiter & Model Fallback Router

**Directory:** `task4_rate_limit_router/`

Implements a token-aware rate limiter and model routing layer with primary/secondary provider fallback.

**Key features**
- Token-based request rate limiting
- Primary and secondary model routing
- Fallback handling for provider failures
- Timeout and error handling
- Configurable mock provider
- Deterministic fallback and timeout-race tests

**Engineering consideration:** Focuses on resilience and predictable behavior under rate limits, provider errors, and timeout conditions.

---

## 🧰 Tech Stack

| Category | Technologies |
|---|---|
| Language | Python |
| Protocol | Model Context Protocol (MCP) |
| Communication | stdio, streaming, proxy-based request forwarding |
| Security | Input validation, tool-level authorization, PII redaction |
| Reliability | Rate limiting, fallback routing, timeout handling |
| Testing | Automated unit tests, integration tests, end-to-end tests |
| Dependencies | Isolated `requirements.txt` per project |

---

## 📂 Repository Structure

```text
AI-Field-Developer-at-QuilrAI/
│
├── task1_mcp_server/
│   ├── requirements.txt
│   ├── server code
│   ├── test_server.py
│   ├── test_stdio_e2e.py
│   └── README.md
│
├── task2_mcp_gateway/
│   ├── requirements.txt
│   ├── gateway code
│   ├── test_gateway.py
│   └── README.md
│
├── task3_streaming_guardrail/
│   ├── requirements.txt
│   ├── proxy and redactor code
│   ├── test_redactor.py
│   ├── test_stream_e2e.py
│   └── README.md
│
├── task4_rate_limit_router/
│   ├── requirements.txt
│   ├── rate limiter and router code
│   ├── test_rate_limiter.py
│   ├── test_router.py
│   ├── test_gateway_e2e.py
│   └── README.md
│
└── README.md
```

---

## ▶️ Getting Started

Each task has isolated dependencies and can be executed independently.

### Prerequisites
- Python 3
- pip
- Git

### Run Task 01 — MCP Server

```bash
cd task1_mcp_server
pip install -r requirements.txt

python3 test_server.py
python3 test_stdio_e2e.py
```

### Run Task 02 — MCP Gateway

```bash
cd task2_mcp_gateway
pip install -r requirements.txt

python3 test_gateway.py
```

### Run Task 03 — Streaming Guardrail

```bash
cd task3_streaming_guardrail
pip install -r requirements.txt

python3 test_redactor.py
python3 test_stream_e2e.py
```

### Run Task 04 — Rate Limit Router

```bash
cd task4_rate_limit_router
pip install -r requirements.txt

python3 test_rate_limiter.py
python3 test_router.py
python3 test_gateway_e2e.py
```

---

## 🧪 Testing Philosophy

The assessment emphasizes deterministic, repeatable testing without requiring external API credentials.

- **Unit tests:** Validate individual components and core behavior.
- **Integration tests:** Verify interactions between components.
- **End-to-end tests:** Exercise complete request flows.
- **Failure scenarios:** Cover invalid inputs, authorization failures, provider errors, rate limits, and timeout behavior.

Mock providers and downstream services make the tests reproducible and suitable for local development.

---

## 💡 Engineering Principles

These projects demonstrate practical engineering considerations for AI infrastructure:

- **Security by design:** Validate inputs and enforce access controls at system boundaries.
- **Privacy awareness:** Inspect and redact sensitive information before delivering streamed responses.
- **Resilience:** Handle provider failures, rate limits, and timeouts through controlled fallback behavior.
- **Testability:** Use deterministic mocks to validate behavior without external dependencies.
- **Modularity:** Keep each task independently runnable and maintainable.
- **Clear documentation:** Include setup instructions, implementation details, and design considerations.

---

## 👩‍💻 Author

**Shiva Priya Pillalamarri**

AI/ML Engineer | Python | Generative AI | Agentic AI | LLM Infrastructure

[GitHub Profile](https://github.com/shiva-priya123)

---

*Submitted as part of the AI Field Developer Engineering Assessment for QuilrAI.*
