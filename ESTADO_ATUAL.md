# Estado atual após a Campanha 0004

Data: 2026-10-09.

O principal mantém `main` em `b2cb8bb22d331251126c73a988c571c15edf6a02` e a tag `baseline-replit-import` nesse baseline. A Campanha 0003 criou `codex/0003-termux-arm64` e o commit local `d412a2f`. A Campanha 0004 parte desse commit no branch `codex/0004-postgresql-local`; seu commit local e publicação do registro estão documentados em [REGISTROS/0004.md](REGISTROS/0004.md). Não houve push do principal. A alteração local preexistente de `.replit` (porta 8083 → 3002) continua intacta e fora dos commits.

A instalação foi concluída em Termux Android 13/aarch64, Node `v26.4.0`, usando pnpm `10.30.1`. O workspace/lockfile agora permitem os optional dependencies Android ARM64 de esbuild, Rollup, Lightning CSS e Tailwind Oxide nas versões já fixadas. Typecheck e build passaram; o frontend respondeu HTTP 200 em smoke local. Startup da API foi adiado porque o módulo de banco exige `DATABASE_URL` imediatamente.

PostgreSQL 18.6 local agora tem role `condoos_app`, database `condoos` e a baseline integral do schema aplicada por migration Drizzle versionada; as 25 tabelas estão vazias. API `/api/healthz` respondeu HTTP 200, e frontend/API passaram smoke simultâneo com proxy Vite configurável. Typecheck e build de regressão passaram. RotaMoto não foi alterado; nenhum seed ou importação ocorreu. Detalhes e limites em [REGISTROS/0004.md](REGISTROS/0004.md).
