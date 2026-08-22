# ADMIN.md — Fila do Shopify admin

Ações que **só** se resolvem no admin da Shopify pelo navegador, porque não vivem no tema e a CLI não alcança.

**Regra:** eu não abro o admin nem a extensão do Chrome por conta própria. Vou acumulando a fila aqui. Quando o Gabriel liberar a permissão e pedir, executo tudo de uma vez, marco o que foi feito e anoto o que travou.

Pendência de **conteúdo** (texto, preço, medida, foto) não entra aqui — vive em `conteudo.md`. Aqui é só ação de admin.

Status: `[ ]` pendente · `[x]` feito (com data)

---

## Fila atual

### Acesso

- [ ] Liberar a extensão do Chrome para `admin.shopify.com` e `petdoduque.com`. Sem isso não faço nem QA visual.

### Criação de conteúdo estrutural — pré-requisito de template

- [ ] **Criar a página `Quem somos`** — Content → Pages → Add page. Título "Quem somos", handle `quem-somos`, corpo vazio; o conteúdo entra pelas sections de `templates/page.quem-somos.json`. Sem a página, o template não tem onde ser aplicado. Trava o E4.
- [ ] **Criar a página `Como medir`** — mesma coisa, handle `como-medir`, para `templates/page.como-medir.json`. Trava o E2.
- [ ] **Menu principal** — Content → Menus: Home · Quem somos · Como medir · Comprar. Só depois das páginas existirem. Trava o E5.
- [ ] **Rodapé** — WhatsApp · Trocas e devoluções · Política de privacidade · Instagram.

### Backup — aberto desde 16/08

- [ ] **Export de conteúdo da loja** (o backup de tema não cobre): CSV de produtos em Products → Export, coleções, páginas e navegação. Guardar em `backups/`. É o E0.

### Catálogo

- [ ] **Metafields de specs do produto** — Settings → Custom data → Products: tamanho, material, cor. Hoje está enterrado na descrição em texto corrido. Trava o E1.
- [ ] **Revisar variantes do "Sapatos Duque"** — tamanho e cor como variantes de verdade, com estoque, antes de refazer a página de produto.
- [ ] **Loox** — verificar se há avaliação real acumulada e se dá pra exportar. É o que destrava a prova social do E1 e do E3.

### Só com "pode publicar" explícito

- [ ] Publicar o tema Craft (#164972953635) no lugar do Booster Premium 2.0.
- [ ] Desativar o modo senha ("Abertura em breve").
- [ ] Revisar apps que o Craft não usa (Loox, Yampi) — cada script custa conversão.

---

## Feito

_(nada ainda)_
