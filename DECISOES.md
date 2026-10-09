# Decisões registradas

## Campanha 0002 — 2026-10-08

- Manter a baseline `baseline-replit-import` intacta; a auditoria foi somente leitura no repositório principal.
- Não executar instalação, build, typecheck, seed ou operações de banco até resolver compatibilidade e estabelecer um fluxo seguro de migrations.
- Tratar a incompatibilidade potencial de binários Android ARM64 como bloqueador de validação local, pois o workspace exclui explicitamente esses pacotes.
- Priorizar correção de segurança (segredo JWT, credenciais demo, RBAC e isolamento tenant) antes de expor a aplicação.
- Não preencher `PLANO_FINALIZACAO.md` com hipóteses; não atualizar `F9_QA_INICIAL.md` sem execução concreta.
- Nenhuma dessas decisões alterou o código do produto.

## Campanha 0003 — 2026-10-09

- Manter as versões nativas já fixadas e reabilitar somente os quatro pacotes Android ARM64 de esbuild, Rollup, Lightning CSS e Tailwind Oxide; manter as exclusões de outras plataformas.
- Usar pnpm 10.30.1 no Termux. A tentativa de pnpm 12.4.0 abortou no runtime Android observado; pnpm 11 não aplicou o allowlist legado `onlyBuiltDependencies` existente.
- Manter o allowlist de scripts existente; não executar `scripts/post-merge.sh`, migrations, pushes de schema ou seed.
- Passar `PORT` e `BASE_PATH` ao build local, conforme exigido pelas configs Vite; nenhuma mudança de aplicação foi necessária.
- Adiar startup da API até existir PostgreSQL local e validação autorizada; não criar uma URL artificial.
- Manter `main` e a tag protegida; commit apenas local no branch da campanha e sem push do principal.
- Nenhuma alteração funcional ou de segurança da Campanha 0002 está autorizada nesta campanha.

## Campanha 0004 — 2026-10-09

- Criar somente `condoos_app` e `condoos`; manter os bancos e roles RotaMoto intactos.
- Usar `drizzle-kit generate` → revisar SQL/snapshot → `drizzle-kit migrate`. `drizzle-kit push`/`push-force` não são fluxo operacional; post-merge não aplica schema automaticamente.
- Manter `.env.local` ignorado e carregar `DATABASE_URL` explicitamente no shell, sem adicionar loader ou versionar credencial.
- Não executar seed nem importar dados; a migration inicial representa o schema vazio atual.
- Manter `main` e a tag baseline intactos; commit apenas local no branch 0004. Publicar somente documentação no repositório histórico.
- Nenhuma correção funcional/de segurança da Campanha 0002 foi incluída.
