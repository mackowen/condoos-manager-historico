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

## Campanha 0005 — 2026-10-13

- Exigir `SESSION_SECRET` com pelo menos 32 bytes; não gerar segredo em startup. Manter o valor real apenas em `.env.local`, ignorado pelo Git.
- Usar HS256 explicitamente, claims mínimos validados e validade máxima de 24 horas.
- Configurar CORS por allowlist exata `CORS_ORIGINS`; permitir somente loopback conhecido por default em desenvolvimento e exigir configuração em produção.
- Aplicar Helmet; HSTS somente em produção para não forçar HTTPS no frontend local.
- Preservar o Bearer token/localStorage por compatibilidade nesta campanha. Migração para HttpOnly exige campanha de sessão/CSRF coordenada.
- Manter seed fora de startup/build/post-merge; execução manual requer ambiente dev/test, opt-in explícito e senha fornecida em variável.
- Não executar seed, não criar usuários, não alterar banco/migration nem tocar em RotaMoto.
- Manter `main` e baseline intactos; commit apenas local no principal. Commit/push somente do histórico.

## Campanha 0006 — 2026-10-13

- Buscar usuário ativo e role/permissões atuais no PostgreSQL após validar o JWT; não carregar permissões nos claims e não confiar no estado do cliente.
- Centralizar `requirePermission` com 401 para identidade inválida e 403 para permissão ausente; manter `*` exclusivamente para role `Administrador` e descartar wildcard em roles legadas com outro nome.
- Autorizar a concessão de permissões somente dentro do conjunto do ator; conferir atribuição de role no mesmo condomínio e não permitir escopo `*` para API Keys.
- Manter o vocabulário de recurso/ação já usado pelo editor e preservar compatibilidade de `update` em roles antigas.
- Não alterar schema: middleware depende de dados já disponíveis em `users` e `roles`; sem migration ou seed.
- Testar somente em `condoos` com dados temporários via HTTP e remover o condomínio de teste ao final; preservar RotaMoto e `.replit`.
- Manter `main`/baseline intactos; commit somente local no principal e publicar apenas documentação no histórico.

## Campanha 0007 — 2026-10-13

- Usar o `condominiumId` carregado no contexto autenticado como única autoridade para consultas e escrita tenant-scoped; conferir IDs de relações no mesmo condomínio antes de criar/alterar registros.
- Manter 404 para recursos cross-tenant quando apropriado, evitando revelar existência por UUID; preservar a ordem de autenticação/RBAC da Campanha 0006.
- Não criar migration: os endpoints HTTP validam relações antes de gravar, e a API não permite alterar o tenant de um registro existente. FKs compostas podem ser consideradas se houver escrita confiável fora da API.
- Corrigir o tamanho do prefixo de API Key ao limite `varchar(8)` encontrado durante o smoke; a autenticação das chaves permanece fora desta campanha.
- Criar dados A/B somente para testes HTTP e excluir os condomínios ao terminar; nenhum seed. Preservar RotaMoto, `.replit`, `main` e baseline; não fazer push do principal.
- Commit local no branch da campanha; publicar somente documentação no histórico.

## Campanha 0008 — 2026-10-14

- Identificar cada API Key por UUID público embutido e guardar somente SHA-256 do segredo aleatório de 256 bits; comparar hashes com `timingSafeEqual`. A chave completa aparece só na resposta de criação.
- Usar `X-API-Key` nas rotas de recursos protegidas por RBAC. O tenant e scopes vêm da linha ativa no banco; scopes exigem correspondência exata e não aceitam `*` nem alias de ações.
- JWT e API Key juntos são rejeitados. Login, registro e health permanecem públicos; perfil e administração de chaves permanecem JWT-only.
- Alargar `key_prefix` para 42 por migration gerada/revisada/aplicada. Não usar push. Recriação de chaves antigas e rotação ficam para procedimento explícito.
- Atualizar `last_used_at` após autenticação e consultar `is_active` em cada requisição para revogação imediata.
- Preservar `main`, baseline, `.replit` e RotaMoto; commit principal local, sem push. Publicar somente documentação no histórico.

## Campanha 0009 — 2026-10-14

- Manter o JWT de 24 horas como conteúdo assinado da sessão, mas enviá-lo somente em cookie `HttpOnly`, `Path=/api`, `SameSite=Lax` e `Secure` em produção; apagar o cookie no logout.
- Usar token CSRF aleatório assinado por HMAC-SHA256 com `SESSION_SECRET` e vinculado ao JWT. Guardar CSRF somente em memória no frontend; exigir Origin/Referer autorizado e token nas mutações web.
- Retirar suporte Bearer do fluxo JWT web; manter `X-API-Key` independente nas rotas de recursos e rejeitar credenciais concorrentes. Login/registro exigem origem autorizada e health permanece público.
- Permitir CORS credentials somente com origem exata allowlisted; exigir `CORS_ORIGINS` em produção e listar `X-CSRF-Token` nos headers aceitos.
- Não alterar schema nem criar migration. Testar via proxy com dados mínimos temporários e removê-los ao final; não executar seed.
- Preservar `main`, baseline, `.replit` e RotaMoto; commit principal local, sem push. Publicar somente documentação no histórico.

## Campanha 0010 — 2026-10-16

- Usar `node:test` e `tsx` já presente em `@workspace/scripts`; não adicionar framework ou dependência de teste.
- Executar o Express app em porta efêmera loopback e usar PostgreSQL somente no banco `condoos_e2e`, usuário `condoos_app`. Obter a URL de `.env.e2e.local` ignorado ou do ambiente; nunca reescrever uma URL recebida. O guard verifica nome, usuário, host local e identidade da conexão viva antes de migrations ou testes.
- Rejeitar banco oficial, RotaMoto, RotaMoto E2E e qualquer nome não autorizado antes de conexão. Não criar banco/role; não dropar banco; aplicar somente migrations Drizzle versionadas.
- Criar fixtures únicas para cada execução e removê-las no teardown por cascade. Nunca executar seed demo.
- Manter `pnpm test` como entrada da suíte; não permitir push, `db:push` ou `db:push-force` como parte do fluxo.
- Preservar `main`, baseline, `.replit` e RotaMoto; commit do principal somente local e publicação apenas da documentação no histórico.
