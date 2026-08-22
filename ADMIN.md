# ADMIN.md — Fila do Shopify admin

Ações que **só** se resolvem no admin da Shopify pelo navegador: não vivem no tema e a CLI não alcança.

**Regra:** eu não abro o admin nem a extensão do Chrome por conta própria. Acumulo a fila aqui. Quando o Gabriel liberar a permissão e pedir, executo, marco o que foi feito e anoto o que travou.

Pendência de **conteúdo** (texto, preço, medida, foto) não entra aqui — vive na seção "Bloqueia a publicação" de cada arquivo em `etapas/`.

Status: `[ ]` pendente · `[x]` feito (com data)

---

## Etapa 0 — antes de qualquer código

- [ ] **Export de conteúdo da loja** — o backup de tema não cobre. Products → Export (CSV), coleções, páginas e navegação. Guardar em `backups/`.
- [ ] **Criar a página `Quem somos`** — Content → Pages → Add page. Título "Quem somos", handle `quem-somos`, corpo vazio. O conteúdo entra pelas sections de `templates/page.quem-somos.json`. Trava a Etapa 3.
- [ ] **Menu principal** — Content → Menus, exatamente 3 itens: `Início` · `Sapatos Duque` · `Quem somos`. Rastreio **sai** do menu. Trava a Etapa 1.
- [ ] **Rodapé** — WhatsApp · Rastreio · Trocas e devoluções · Política de privacidade · Instagram.
- [ ] **Liberar a extensão do Chrome** para `admin.shopify.com` e `petdoduque.com`. Sem isso não há nem QA visual.

## Catálogo — trava a Etapa 2

- [ ] **Associar cada foto de cor à variante** — é o que faz a foto principal trocar quando o cliente muda a cor. Nativo, sem app.
- [ ] **Desassociar do produto as ~32 fotos excedentes** da galeria. Não apagar da biblioteca.
- [ ] **Metafields de specs** — Settings → Custom data → Products: material e composição. Hoje está enterrado na descrição em texto corrido.
- [ ] **Revisar variantes do "Sapatos Duque"** — cor, tamanho e kit com estoque correto.

## Prova social

- [ ] **Loox** — verificar se há avaliação real acumulada no Booster e se dá pra exportar. É o que destrava as seções desativadas da Etapa 1 e o bloco da Etapa 2.

## Só com "pode publicar" explícito — Etapa 4

- [ ] Publicar o Craft (#164972953635) no lugar do Booster Premium 2.0.
- [ ] Desativar o modo senha ("Abertura em breve"). **Decisão separada da publicação.**
- [ ] Revisar apps que o Craft não usa (Loox, Yampi) — cada script custa conversão.

---

## Feito
_(nada ainda)_
