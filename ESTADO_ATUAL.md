# Estado atual após a Campanha 0002

Data: 2026-10-08.

O repositório principal permanece em `main` no commit `b2cb8bb22d331251126c73a988c571c15edf6a02`, com a tag `baseline-replit-import` protegida. A branch `replit-agent` aponta para `e5d297ccc25a727c52ad9ad44210709ff4746a60`; sua árvore versionada é idêntica à de `main`. A alteração local preexistente em `.replit` (mapeamento da porta 8083 para 3002) foi preservada.

O produto é um monorepo pnpm/TypeScript com frontend React/Vite, API Express, PostgreSQL/Drizzle, OpenAPI/Orval e schemas/hooks gerados. A auditoria estática identificou bloqueador provável de instalação/build em Android ARM64: overrides do workspace excluem pacotes binários ARM64 de esbuild, Rollup, Lightning CSS e Tailwind Oxide.

Riscos prioritários registrados em [REGISTROS/0002.md](REGISTROS/0002.md): fallback JWT previsível, credenciais demo versionadas, RBAC sem enforcement server-side e risco de associações sem isolamento tenant. Não foram executados testes, build, instalação ou acesso ao banco. O código principal não foi alterado pela campanha.
