# Pendências confirmadas — após a Campanha 0011

- [x] Portabilidade de dependências Termux/Android ARM64: overrides corrigidos, lockfile atualizado; install, typecheck e build passaram no dispositivo. Ver [REGISTROS/0003.md](REGISTROS/0003.md).
- [x] Remover fallback previsível de `SESSION_SECRET`, exigir chave forte, validar JWT e restringir CORS/headers. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [x] Remover senha demo reutilizável do código/documentação e condicionar seed explicitamente a ambiente dev/test. Ver [REGISTROS/0005.md](REGISTROS/0005.md).
- [x] Implementar enforcement RBAC server-side nas rotas administrativas e de recursos; registro e health permanecem públicos conforme o contrato. Ver [REGISTROS/0006.md](REGISTROS/0006.md).
- [x] Revisar referências por ID e joins da API; validar FKs recebidas contra o tenant autenticado, incluindo dashboard, busca, marketplace e API Keys. Ver [REGISTROS/0007.md](REGISTROS/0007.md). O schema ainda não declara FKs compostas por tenant; avaliar se surgirem caminhos de escrita confiáveis fora da API.
- [x] Implementar autenticação e enforcement de scopes de API Keys, mantendo segredo apenas como hash e gestão JWT-only. Ver [REGISTROS/0008.md](REGISTROS/0008.md).
- [x] Restringir CORS e adicionar headers Helmet. JWT foi removido de `localStorage` e a sessão web usa cookie HttpOnly com CSRF validado server-side. Superfícies XSS/frontend auditadas e endurecidas na Campanha 0011; ver [REGISTROS/0011.md](REGISTROS/0011.md).
- [x] Introduzir migration inicial Drizzle versionada e remover push automático do post-merge; migrations futuras exigem revisão e comando explícito. Estratégia de backup/rollback ainda precisa ser definida antes de operações com dados relevantes.
- [ ] Confirmar se existem dados no banco Replit/Neon que não vieram na importação e definir exportação.
- [x] Adicionar suíte automatizada durável para sessão/CSRF, RBAC, IDOR multi-tenant e API Keys, com isolamento entre tenants verificado nas listas de financeiro, marketplace e contratos. Ver [REGISTROS/0010.md](REGISTROS/0010.md).
- [ ] Expandir testes funcionais de domínio financeiro/marketplace/contratos e validar contratos OpenAPI.
- [ ] Confirmar comportamento de upload/documentos; atualmente o schema/UI trabalham com URL/metadados, sem upload binário observado.
- [x] PostgreSQL CondoOS local provisionado isoladamente; migration inicial aplicada sem dados; API, health check e stack frontend/API passaram smoke técnico. Ver [REGISTROS/0004.md](REGISTROS/0004.md).
- [x] Migrar JWT de `localStorage` para cookie HttpOnly, incluindo proteção CSRF e compatibilidade frontend/API. Ver [REGISTROS/0009.md](REGISTROS/0009.md).
- [ ] Definir procedimento de rotação das API Keys; o formato legado requer recriação e não tem segredo recuperável.
- [x] Adicionar testes automatizados duráveis de isolamento multi-tenant; A→B/B→A, GET/UPDATE/DELETE, relações cross-tenant e isolamento de listagem cobertos em [REGISTROS/0010.md](REGISTROS/0010.md).
- [x] Auditar saídas frontend, restringir URLs de documentos/imagens, neutralizar fórmula CSV e cobrir payloads adversariais XSS em [REGISTROS/0011.md](REGISTROS/0011.md).
- [ ] Configurar e validar CSP no host que serve o frontend em produção; Helmet atual cobre as respostas da API, mas o host estático é externo à configuração deste repositório. Ver [REGISTROS/0011.md](REGISTROS/0011.md).

Achados da auditoria estática em [REGISTROS/0002.md](REGISTROS/0002.md); portabilidade validada em [REGISTROS/0003.md](REGISTROS/0003.md).

## RotaMoto Campanha 0231 — itens abertos

- [x] Provedores S3 SigV4 e SFTP/SSH pinado, catálogo cifrado, UI administrativa, política de destinos e teste sintético local em Browser. Commit do Restaurante `12104d2`.
- [ ] Implementar inventário remoto, capacidade, histórico de sincronização e alertas por destino.
- [ ] Implementar download e recuperação externa em PostgreSQL descartável; nenhum restore operacional é autorizado.
- [ ] Implementar retenção remota independente, remoção segura e invariantes de cópia mínima/última cópia recuperável.
- [ ] Comprovar retomada após interrupção de rede com estado durável e teste de falha/reinício para S3 e SFTP.
- [ ] Exercitar integrações reais somente em campanha autorizada separada; a Campanha 0231 não utilizou contas ou servidores externos.
- [ ] Verificar o provisionamento Linux com UIDs/GID dedicados para a chave do cofre e confirmar limites de isolamento Termux sem root.

Estas pendências pertencem ao aplicativo Restaurante e não alteram o banco nem o código do CondoOS.
