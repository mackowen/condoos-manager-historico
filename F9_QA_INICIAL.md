# QA técnico inicial — Campanhas 0003 e 0004

Data: 2026-10-09. Este registro cobre portabilidade e infraestrutura local; não é QA funcional nem valida fluxos de negócio ou segurança. A validação PostgreSQL local está limitada ao schema vazio e à conexão descritos na Campanha 0004.

| Verificação | Resultado | Evidência |
|---|---|---|
| Instalação | PASS | `pnpm install` com pnpm 10.30.1 no Termux Android ARM64; binários nativos Android presentes. |
| Typecheck | PASS | `pnpm run typecheck`: libs, frontend, API server, mockup sandbox e scripts concluíram sem erros. |
| Build | PASS | `PORT=4173 BASE_PATH=/ pnpm run build`; esbuild, Vite, Rollup, Lightning CSS e Tailwind/Oxide exercitados no host. |
| Frontend startup | PASS | Vite em `localhost:4179`; smoke GET `/` retornou HTTP 200 `text/html`; processo encerrado. |
| API startup | ADIADO | Import do módulo DB exige `DATABASE_URL`; nenhum banco foi criado ou acessado. |

## Campanha 0004 — PostgreSQL local e stack técnico

| Verificação | Resultado | Evidência |
|---|---|---|
| PostgreSQL/schema | PASS | PostgreSQL 18.6; database `condoos` owned por `condoos_app`; migration `0000_initial_baseline` aplicada; 25 tabelas vazias e journal Drizzle. |
| API + health | PASS | API em porta 3101; GET `/api/healthz` HTTP 200 JSON; conexão da role de app validada por consulta read-only. |
| Frontend + API simultâneos | PASS | Vite porta 4179, raiz HTTP 200 e `/api/healthz` proxied para a API respondeu HTTP 200 JSON. Processos encerrados. |
| Typecheck | PASS | `pnpm run typecheck` após alterações: libs, frontend, API, mockup e scripts sem erros. |
| Build | PASS | `PORT=4179 BASE_PATH=/ pnpm run build`; mockup, API esbuild e frontend Vite/Rollup/Tailwind concluíram. Warnings de sourcemap, chunk e `DEP0205` sem bloqueio. |
| Seed/importação | NÃO EXECUTADO | Nenhum seed, dado demo ou importação Replit; contagens das 25 tabelas permaneceram zero. |

Evidência e limites: [REGISTROS/0004.md](REGISTROS/0004.md). O endpoint de health não consulta o banco; a conexão foi validada separadamente. Nenhum QA funcional foi executado.

Detalhes, comandos, avisos e limites: [REGISTROS/0003.md](REGISTROS/0003.md). Nenhum cenário funcional foi executado; não inferir cobertura além dos gates técnicos descritos.
