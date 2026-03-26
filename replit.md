# Validador de Documentação

## Overview

Ferramenta interna para validação e geração de documentação técnica usando IA (Gemini).

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod, drizzle-zod
- **AI**: Gemini (via Replit AI Integrations)
- **Frontend**: React + Vite + Tailwind CSS + shadcn/ui
- **State**: TanStack Query

## Structure

```
├── artifacts/
│   ├── api-server/       # Express API (porta 8080)
│   └── doc-validator/    # Frontend React + Vite (porta 5000)
├── lib/
│   ├── api-spec/         # OpenAPI spec + codegen Orval
│   ├── api-client-react/ # React Query hooks gerados
│   ├── api-zod/          # Schemas Zod gerados
│   ├── db/               # Drizzle ORM + schema
│   └── integrations/     # Gemini AI integration
├── scripts/
├── pnpm-workspace.yaml
└── package.json
```

## Features

1. **Validar Documentação** — Cola documentação → IA analisa e sugere melhorias
2. **Gerar Documentação** — Cola card Jira → IA gera doc no padrão Outline
3. **Mapa de Campos** — Hierarquia Módulo > Tabela > Campo (react-flow)
4. **Histórico** — Lista de validações/gerações anteriores
5. **Wiki IXC** — Busca na wiki pública

## API Routes

- `GET /api/healthz` — Health check
- `POST /api/validator/validate` — Valida documentação existente
- `POST /api/validator/generate` — Gera documentação a partir de card Jira
- `POST /api/validator/wiki-search` — Busca na wiki pública
- `GET /api/fields` — Lista campos mapeados
- `POST /api/fields` — Cria mapeamento de campo
- `DELETE /api/fields/:id` — Remove campo

## Environment Variables

- `DATABASE_URL` — URL do PostgreSQL (provisionado automaticamente)
- `AI_INTEGRATIONS_GEMINI_BASE_URL` — URL do proxy Gemini (via Replit AI)
- `AI_INTEGRATIONS_GEMINI_API_KEY` — Chave dummy para SDK (automática)

## Workflows

- `artifacts/api-server: API Server` — Backend Express (porta 8080)
- `artifacts/doc-validator: web` — Frontend Vite (porta 5000, webview)
