# ADMIN.md — Fila do Shopify admin

Ações que só se resolvem no admin. Regras de acesso: `CLAUDE.md` §4. Pendência de conteúdo (texto, preço, foto) vive em `etapas/`.

`[ ]` pendente · `[x]` feito (com data)

## Etapa 0

- [ ] **Export de conteúdo da loja** → `backups/`. Só produtos têm export nativo (CSV); páginas, políticas, coleções e menus são cópia manual. O corpo de `quem-somos` existe **só** no banco — sem isso, não há de onde restaurar.
- [ ] **Título da página Quem somos:** trocar `QUEM SOMOS?` por `Quem somos` — título e SEO.
- [ ] **Template da página Quem somos:** trocar para `page.quem-somos.json` quando eu criar (Etapa 3).
- [ ] **Rodapé:** WhatsApp · Rastreio · Trocas e devoluções · Política de privacidade · Instagram.

## Catálogo — trava a Etapa 2

- [ ] **Associar cada foto de cor à variante** — faz a foto trocar com a cor; "hide variants' media" já está ligado no template.
- [ ] **Desassociar as ~32 fotos excedentes** do produto (não apagar da biblioteca). Ficam 6–8: 1 por cor + cão calçado + kit + solado.
- [ ] **`alt` em pt-BR nas fotos que ficarem**, citando a cor (Edit alt text — vive no admin, não no tema).
- [ ] **Trocar a descrição do produto** pelo texto da Etapa 2 §4, como texto puro — o `body_html` sujo ainda alimenta SEO, busca e canais externos.
- [ ] **Conferir o nome da opção de tamanho** — precisa conter "tamanho" e manter os rótulos exatos (`0=`, `PP=`…), senão o "como medir" e as faixas em cm somem.
- [ ] **Metafields de specs** (material, composição) — Settings → Custom data → Products.
- [ ] **Revisar variantes** — cor, tamanho e kit com estoque correto.
- [ ] **Renomear os rótulos de tamanho** (tirar o `=`) — se renomear, muda junto em 3 lugares do tema; ver `todo.md`, Dívida técnica.

## Prova social

- [ ] **Loox** — verificar avaliação real acumulada no Booster e se dá pra exportar. Destrava seções das Etapas 1 e 2.

## Etapa 4 — só com "pode publicar" explícito

- [ ] Publicar o Craft (#164972953635) no lugar do Booster Premium 2.0.
- [ ] Desativar o modo senha — decisão separada da publicação.
- [ ] Revisar apps que o Craft não usa (Loox, Yampi).

## Feito

- [x] **Página Quem somos existe** (22/08) — ID `50586583145`, handle `quem-somos`, com a história do Duque no `body_html`. Matéria-prima da Etapa 3.
- [x] **Menu principal** (22/08) — Início · Sapatos Duque · Quem somos. Rastreio saiu; estado anterior em `backups/navegacao-2026-08-22.md`.
