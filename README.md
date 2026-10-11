# Tokenis

**Let any LLM answer questions about confidential data without ever seeing a row.**

Tokenis is an open-source gateway between an organisation's protected data and a
language model. The model gets a few [MCP](https://modelcontextprotocol.io) tools that
answer aggregate questions over **encrypted** columns, under admission control and a
signed audit trail. It can ask "total 2025 revenue for tech companies in Seoul?" and get a
number with the size of the group behind it. It cannot ask for one company's revenue, cannot
get it by differencing two overlapping questions, and cannot learn *why* a question was refused.

## Works with

Claude · ChatGPT and the OpenAI API · Gemini · Codex · Cursor · VS Code · Windsurf ·
local models (Ollama, vLLM, SARA)

Any AI app that speaks MCP, and any model with tool calling through the APIs. The gateway
treats them all the same, so what a model can learn does not depend on which one it is.

## What it enforces

- **Minimum group size.** No total or average over fewer than *k* records.
- **Differencing check.** A question that, combined with earlier answers to anyone, would
  isolate a record is refused.
- **Budgets per person**, and refusals that never say which rule fired.
- **A signed, hash-chained audit trail** of every answer and refusal. Values are never recorded.
- **Identity from the credential**, not from anything the model says.

## For teams

Shared state across replicas (PostgreSQL), an admin console with single sign-on and roles,
**Tokenis Ask** (a browser chat screen in English and Korean for people without an AI app),
Docker Compose and Helm, Prometheus metrics. Apache-2.0.

## Read more

- Code and docs: [tokenismcp/tokenis-mcp](https://github.com/tokenismcp/tokenis-mcp)
- Connect your AI app: [docs/clients.md](https://github.com/tokenismcp/tokenis-mcp/blob/main/docs/clients.md)
- Threat model: [docs/threat-model.md](https://github.com/tokenismcp/tokenis-mcp/blob/main/docs/threat-model.md)
- Papers and reproduction code: [papers/](https://github.com/tokenismcp/tokenis-mcp/tree/main/papers)
  (disclosure boundaries, leakage quantification, admission control, and the Tokenis whitepaper)

## Status

Pre-release: v0.1.0 is in preparation. Not independently audited yet; feedback on the threat
model is the most useful thing you can give us.

*Built by 4Chains Inc. Research published through J1729Labs.*
