# Pendências confirmadas — após a Campanha 0005

- [x] Portabilidade de dependências Termux/Android ARM64: overrides corrigidos, lockfile atualizado; install, typecheck e build passaram no dispositivo. Ver [REGISTROS/0003.md](REGISTROS/0003.md).
- [x] Remover fallback previsível de `SESSION_SECRET`, exigir chave forte, validar JWT e restringir CORS/headers. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [x] Remover senha demo reutilizável do código/documentação e condicionar seed explicitamente a ambiente dev/test. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [ ] Implementar enforcement RBAC na API; conferir rotas administrativas e registro público.
- [ ] Revisar referências por ID e joins para garantir escopo `condominiumId` em todas as operações e integridade tenant das FKs.
- [ ] Definir autenticação e enforcement de permissões das API Keys ou retirar funcionalidade sem uso.
- [x] Restringir CORS e adicionar headers Helmet. Revisão/mitigação XSS e armazenamento JWT em `localStorage` ainda pendente; cookie HttpOnly requer campanha coordenada.
- [x] Introduzir migration inicial Drizzle versionada e remover push automático do post-merge; migrations futuras exigem revisão e comando explícito. Estratégia de backup/rollback ainda precisa ser definida antes de operações com dados relevantes.
- [ ] Confirmar se existem dados no banco Replit/Neon que não vieram na importação e definir exportação.
- [ ] Criar testes para auth, RBAC, tenant/IDOR, financeiro, marketplace e contratos OpenAPI.
- [ ] Confirmar comportamento de upload/documentos; atualmente o schema/UI trabalham com URL/metadados, sem upload binário observado.
- [x] PostgreSQL CondoOS local provisionado isoladamente; migration inicial aplicada sem dados; API, health check e stack frontend/API passaram smoke técnico. Ver [REGISTROS/0004.md](REGISTROS/0004.md).
- [ ] Migrar JWT de `localStorage` para cookie HttpOnly, incluindo proteção CSRF e compatibilidade frontend/API.

Achados da auditoria estática em [REGISTROS/0002.md](REGISTROS/0002.md); portabilidade validada em [REGISTROS/0003.md](REGISTROS/0003.md).
