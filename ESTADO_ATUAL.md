# Estado atual após a Campanha 0005

Data: 2026-10-13.

O principal mantém `main` em `b2cb8bb22d331251126c73a988c571c15edf6a02` e a tag `baseline-replit-import` nesse baseline. A Campanha 0003 criou `codex/0003-termux-arm64` e o commit local `d412a2f`. A Campanha 0004 parte desse commit no branch `codex/0004-postgresql-local`; seu commit local e publicação do registro estão documentados em [REGISTROS/0004.md](REGISTROS/0004.md). Não houve push do principal. A alteração local preexistente de `.replit` (porta 8083 → 3002) continua intacta e fora dos commits.

A instalação foi concluída em Termux Android 13/aarch64, Node `v26.4.0`, usando pnpm `10.30.1`. A Campanha 0005 endureceu JWT, configuração de segredo, CORS, headers HTTP e seed demo. A branch `codex/0005-auth-security` parte de `cd6c6ca` e contém o commit local `021e5a8`; o registro dos smokes está em [REGISTROS/0005.md](REGISTROS/0005.md). Typecheck, build, API/health e frontend/API simultâneos passaram.

PostgreSQL 18.6 local tem role `condoos_app`, database `condoos` e migration Drizzle aplicada; as 25 tabelas seguem vazias após os testes. RotaMoto não foi alterado; nenhum seed ou importação ocorreu. Detalhes em [REGISTROS/0004.md](REGISTROS/0004.md) e [REGISTROS/0005.md](REGISTROS/0005.md).
