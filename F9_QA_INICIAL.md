# QA técnico inicial — Campanha 0003

Data: 2026-10-09. Este registro cobre apenas portabilidade e infraestrutura local; não é QA funcional nem valida fluxos de negócio, segurança ou PostgreSQL.

| Verificação | Resultado | Evidência |
|---|---|---|
| Instalação | PASS | `pnpm install` com pnpm 10.30.1 no Termux Android ARM64; binários nativos Android presentes. |
| Typecheck | PASS | `pnpm run typecheck`: libs, frontend, API server, mockup sandbox e scripts concluíram sem erros. |
| Build | PASS | `PORT=4173 BASE_PATH=/ pnpm run build`; esbuild, Vite, Rollup, Lightning CSS e Tailwind/Oxide exercitados no host. |
| Frontend startup | PASS | Vite em `localhost:4179`; smoke GET `/` retornou HTTP 200 `text/html`; processo encerrado. |
| API startup | ADIADO | Import do módulo DB exige `DATABASE_URL`; nenhum banco foi criado ou acessado. |

Detalhes, comandos, avisos e limites: [REGISTROS/0003.md](REGISTROS/0003.md). Nenhum cenário funcional foi executado; não inferir cobertura além dos gates técnicos descritos.
