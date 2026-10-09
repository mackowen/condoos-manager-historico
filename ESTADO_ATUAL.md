# Estado atual após a Campanha 0003

Data: 2026-10-09.

O principal mantém `main` em `b2cb8bb22d331251126c73a988c571c15edf6a02` e a tag `baseline-replit-import` nesse baseline. A Campanha 0003 criou `codex/0003-termux-arm64` e o commit local `d412a2f`; não houve push do principal. A alteração local preexistente de `.replit` (porta 8083 → 3002) continua intacta e fora do commit.

A instalação foi concluída em Termux Android 13/aarch64, Node `v26.4.0`, usando pnpm `10.30.1`. O workspace/lockfile agora permitem os optional dependencies Android ARM64 de esbuild, Rollup, Lightning CSS e Tailwind Oxide nas versões já fixadas. Typecheck e build passaram; o frontend respondeu HTTP 200 em smoke local. Startup da API foi adiado porque o módulo de banco exige `DATABASE_URL` imediatamente.

Não foi criado ou alterado PostgreSQL; não houve migration, push de schema ou seed. Nenhuma alteração funcional/de segurança da Campanha 0002 foi feita. Detalhes, warnings e limites em [REGISTROS/0003.md](REGISTROS/0003.md).
