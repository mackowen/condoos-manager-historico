# Pendências confirmadas — após a Campanha 0009

- [x] Portabilidade de dependências Termux/Android ARM64: overrides corrigidos, lockfile atualizado; install, typecheck e build passaram no dispositivo. Ver [REGISTROS/0003.md](REGISTROS/0003.md).
- [x] Remover fallback previsível de `SESSION_SECRET`, exigir chave forte, validar JWT e restringir CORS/headers. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [x] Remover senha demo reutilizável do código/documentação e condicionar seed explicitamente a ambiente dev/test. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [x] Implementar enforcement RBAC server-side nas rotas administrativas e de recursos; registro e health permanecem públicos conforme o contrato. Ver [REGISTROS/0006.md](REGISTROS/0006.md).
- [x] Revisar referências por ID e joins da API; validar FKs recebidas contra o tenant autenticado, incluindo dashboard, busca, marketplace e API Keys. Ver [REGISTROS/0007.md](REGISTROS/0007.md). O schema ainda não declara FKs compostas por tenant; avaliar se surgirem caminhos de escrita confiáveis fora da API.
- [x] Implementar autenticação e enforcement de scopes de API Keys, mantendo segredo apenas como hash e gestão JWT-only. Ver [REGISTROS/0008.md](REGISTROS/0008.md).
- [x] Restringir CORS e adicionar headers Helmet. JWT foi removido de `localStorage` e a sessão web usa cookie HttpOnly com CSRF validado server-side. Revisão/mitigação XSS continua pendente.
- [x] Introduzir migration inicial Drizzle versionada e remover push automático do post-merge; migrations futuras exigem revisão e comando explícito. Estratégia de backup/rollback ainda precisa ser definida antes de operações com dados relevantes.
- [ ] Confirmar se existem dados no banco Replit/Neon que não vieram na importação e definir exportação.
- [ ] Adicionar testes automatizados duráveis para auth/RBAC e cobertura de financeiro, marketplace e contratos OpenAPI; os smokes RBAC da Campanha 0006 foram executados por HTTP.
- [ ] Confirmar comportamento de upload/documentos; atualmente o schema/UI trabalham com URL/metadados, sem upload binário observado.
- [x] PostgreSQL CondoOS local provisionado isoladamente; migration inicial aplicada sem dados; API, health check e stack frontend/API passaram smoke técnico. Ver [REGISTROS/0004.md](REGISTROS/0004.md).
- [x] Migrar JWT de `localStorage` para cookie HttpOnly, incluindo proteção CSRF e compatibilidade frontend/API. Ver [REGISTROS/0009.md](REGISTROS/0009.md).
- [ ] Definir procedimento de rotação das API Keys; o formato legado requer recriação e não tem segredo recuperável.
- [ ] Adicionar testes automatizados duráveis de isolamento multi-tenant; os testes A→B/B→A da Campanha 0007 foram executados via HTTP e limpos ao final.

Achados da auditoria estática em [REGISTROS/0002.md](REGISTROS/0002.md); portabilidade validada em [REGISTROS/0003.md](REGISTROS/0003.md).
