# Decisões registradas

## Campanha 0002 — 2026-10-08

- Manter a baseline `baseline-replit-import` intacta; a auditoria foi somente leitura no repositório principal.
- Não executar instalação, build, typecheck, seed ou operações de banco até resolver compatibilidade e estabelecer um fluxo seguro de migrations.
- Tratar a incompatibilidade potencial de binários Android ARM64 como bloqueador de validação local, pois o workspace exclui explicitamente esses pacotes.
- Priorizar correção de segurança (segredo JWT, credenciais demo, RBAC e isolamento tenant) antes de expor a aplicação.
- Não preencher `PLANO_FINALIZACAO.md` com hipóteses; não atualizar `F9_QA_INICIAL.md` sem execução concreta.
- Nenhuma dessas decisões alterou o código do produto.
