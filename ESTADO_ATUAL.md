# Estado atual após a Campanha 0008

Data: 2026-10-14.

O principal mantém `main` em `b2cb8bb22d331251126c73a988c571c15edf6a02` e a tag `baseline-replit-import` nesse baseline. A Campanha 0003 criou `codex/0003-termux-arm64` e o commit local `d412a2f`. A Campanha 0004 parte desse commit no branch `codex/0004-postgresql-local`; seu commit local e publicação do registro estão documentados em [REGISTROS/0004.md](REGISTROS/0004.md). Não houve push do principal. A alteração local preexistente de `.replit` (porta 8083 → 3002) continua intacta e fora dos commits.

O ambiente usa Termux Android 13/aarch64, Node `v26.4.0` e pnpm `10.30.1`. A Campanha 0005 endureceu JWT, segredo, CORS, headers e seed demo. A Campanha 0006 aplica enforcement RBAC server-side; branch `codex/0006-rbac-server`, commit local `c6107b2`, descendente de `021e5a8`. Typecheck, build, API/health e frontend/API passaram; os dados temporários foram removidos. Registro em [REGISTROS/0006.md](REGISTROS/0006.md).

PostgreSQL 18.6 local tem role `condoos_app`, database `condoos` e duas migrations Drizzle aplicadas; as tabelas de aplicação terminaram vazias após os testes. A Campanha 0007 validou isolamento tenant-scoped e a 0008 adicionou autenticação de API Keys por `X-API-Key`, hash SHA-256, scopes exatos e revogação imediata. O principal da 0008 está em `codex/0008-api-key-auth`, commit local `963d804`, sem push. Typecheck, build, health e frontend/API passaram. RotaMoto não foi alterado; nenhum seed ou importação ocorreu. Ver [REGISTROS/0004.md](REGISTROS/0004.md), [REGISTROS/0005.md](REGISTROS/0005.md), [REGISTROS/0006.md](REGISTROS/0006.md), [REGISTROS/0007.md](REGISTROS/0007.md) e [REGISTROS/0008.md](REGISTROS/0008.md).
