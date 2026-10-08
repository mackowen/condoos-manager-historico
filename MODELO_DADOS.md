# Modelo de dados observado — Campanha 0002

Banco PostgreSQL acessado por `pg` e Drizzle. O schema está em `lib/db/src/schema`; não há migrations versionadas encontradas. O pacote oferece `drizzle-kit push` e `push-force`; nenhum foi executado.

Tabelas identificadas: `condominiums`, `roles`, `users`, `units`, `residents`, `charges`, `payments`, `notices`, `issues`, `deliveries`, `vehicles`, `reservations`, `documents`, `suppliers`, `service_orders`, `contracts`, `events`, `activity_logs`, `api_keys`, `marketplace_categories`, `marketplace_listings`, `marketplace_listing_images`, `marketplace_favorites`, `marketplace_reports`, `marketplace_settings`.

PKs UUID com default aleatório; FKs e índices declarados por tabela. A maioria dos registros de negócio tem `condominiumId` e FK para condomínio. Há FKs de unidade, fornecedor, usuário, papel, cobrança e anúncios; nem todas as relações verificam coerência com o mesmo tenant. Email de usuário tem unique global; marketplace settings unique por condomínio; favoritos unique por usuário/anúncio. Estados e categorias são texto, sem enums PostgreSQL. `charges`/`payments` usam `numeric`; timestamps geralmente têm timezone. Exclusão é física na maioria das tabelas; API keys têm `is_active`.

O inventário de campos, cascatas e limitações consta em [REGISTROS/0002.md](REGISTROS/0002.md), seção 7. Nenhuma conexão ao PostgreSQL foi feita.
