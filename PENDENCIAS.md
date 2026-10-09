# Pendências confirmadas — após a Campanha 0003

- [x] Portabilidade de dependências Termux/Android ARM64: overrides corrigidos, lockfile atualizado; install, typecheck e build passaram no dispositivo. Ver [REGISTROS/0003.md](REGISTROS/0003.md).
- [ ] Segurança crítica: retirar fallback previsível de `SESSION_SECRET` e exigir configuração segura antes de iniciar API.
- [ ] Revogar/substituir credenciais demo versionadas; decidir se seed demo permanece e como é habilitado em ambiente local.
- [ ] Implementar enforcement RBAC na API; conferir rotas administrativas e registro público.
- [ ] Revisar referências por ID e joins para garantir escopo `condominiumId` em todas as operações e integridade tenant das FKs.
- [ ] Definir autenticação e enforcement de permissões das API Keys ou retirar funcionalidade sem uso.
- [ ] Restringir CORS e revisar proteção XSS/CSP e armazenamento de JWT.
- [ ] Introduzir migrations versionadas, backup/rollback e bloquear push destrutivo sem revisão.
- [ ] Confirmar se existem dados no banco Replit/Neon que não vieram na importação e definir exportação.
- [ ] Criar testes para auth, RBAC, tenant/IDOR, financeiro, marketplace e contratos OpenAPI.
- [ ] Confirmar comportamento de upload/documentos; atualmente o schema/UI trabalham com URL/metadados, sem upload binário observado.
- [x] Typecheck, build e smoke técnico do frontend no Termux concluídos. Startup da API segue pendente até haver PostgreSQL local; não houve conexão nesta campanha.

Achados da auditoria estática em [REGISTROS/0002.md](REGISTROS/0002.md); portabilidade validada em [REGISTROS/0003.md](REGISTROS/0003.md).
