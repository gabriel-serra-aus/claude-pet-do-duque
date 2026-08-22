# ADMIN.md — Fila do Shopify admin

Ações que **só** se resolvem no admin da Shopify pelo navegador: não vivem no tema e a CLI não alcança.

**Regra:** eu não abro o admin nem a extensão do Chrome por conta própria. Acumulo a fila aqui. Quando o Gabriel liberar a permissão e pedir, executo, marco o que foi feito e anoto o que travou.

Pendência de **conteúdo** (texto, preço, medida, foto) não entra aqui — vive na seção "Bloqueia a publicação" de cada arquivo em `etapas/`.

Status: `[ ]` pendente · `[x]` feito (com data)

---

## Etapa 0 — antes de qualquer código

- [ ] **Export de conteúdo da loja** — o backup de tema não cobre. Products → Export (CSV), coleções, páginas e navegação. Guardar em `backups/`.
- [x] **Página `Quem somos` já existe** (22/08) — ID `50586583145`, handle `quem-somos`, visível, template "Página padrão". **Não estava vazia:** tem a história do Duque no `body_html`, texto real e bom, que só existe no banco. Matéria-prima da Etapa 3.
- [ ] **Título da página em CAIXA ALTA** — está `QUEM SOMOS?`. Trocar para `Quem somos`. Vale para o título e para o SEO.
- [ ] **Template da página** — hoje "Página padrão". Depois que eu criar `templates/page.quem-somos.json`, trocar no dropdown "Modelo". Etapa 3.
- [x] **Menu principal** (22/08) — 3 itens: `Início` · `Sapatos Duque` (aponta direto ao produto) · `Quem somos`. Rastreio saiu. Verificado no servidor de dev. Estado anterior em `backups/navegacao-2026-08-22.md`.
- [ ] **Rodapé** — WhatsApp · Rastreio · Trocas e devoluções · Política de privacidade · Instagram.
- [ ] **Ferramenta de navegador na sessão** — o Gabriel já autorizou o acesso ao admin (ver `CLAUDE.md`), mas a sessão do Claude Code não tem ferramenta de navegador. Autorização não instala ferramenta. Caminho: `claude mcp add playwright -- npx -y @playwright/mcp@latest`, reiniciar a sessão e apontar para o Chrome já logado. Ver `todo.md`.

## Catálogo — trava a Etapa 2

- [ ] **Associar cada foto de cor à variante** — é o que faz a foto principal trocar quando o cliente muda a cor. Nativo, sem app. O template já está com "hide variants' media" ligado: associada a foto, selecionar uma cor esconde as fotos das outras.
- [ ] **Desassociar do produto as ~32 fotos excedentes** da galeria. Não apagar da biblioteca. Ficam 6–8: 1 por cor (4) + cão calçado + kit completo + detalhe do solado.
- [ ] **`alt` em pt-BR nas fotos que ficarem**, citando a cor — o alt de mídia de produto vive no admin (Edit alt text), não no tema.
- [ ] **Trocar a descrição do produto pelo texto novo** — Etapa 2, §4. Colar como texto puro: zero imagem, zero HTML à mão. Desde 22/08 a página **não renderiza mais** a descrição do admin (o texto vive numa seção do template), então os banners e vídeos antigos já não aparecem — mas o `body_html` sujo continua alimentando SEO, busca e canais externos. Limpar continua valendo.
- [ ] **Conferir o nome da opção de tamanho** — o link "como medir" e as faixas em cm no seletor casam pelo nome da opção conter "tamanho" e pelos rótulos exatos (`0=`, `PP=`…). Se a opção tiver outro nome, nada aparece; se os rótulos mudarem, a faixa some — e as tabelas da home e da página de produto têm que mudar junto.
- [ ] **Metafields de specs** — Settings → Custom data → Products: material e composição. Hoje está enterrado na descrição em texto corrido.
- [ ] **Revisar variantes do "Sapatos Duque"** — cor, tamanho e kit com estoque correto.
- [ ] **Renomear os rótulos de tamanho** — hoje são `0=`, `PP=`, `P=`, `M=`, `G=`, `GG=`, `XG=`, `XXG=`. O `=` é ruído. As faixas em cm estão certas. Se renomear, a tabela da Home precisa mudar junto — os dois têm que casar.

## Etapa 1 — rodapé

- [ ] **Criar o menu de rodapé** — Content → Menus → Add menu. Sem ele o rodapé não tem coluna de links. Itens:
  - `Fale no WhatsApp` → `https://wa.me/5521993438017`
  - `Rastrear pedido` → `/pages/rastreamento-1`
  - `Trocas e devoluções` → política de reembolso (Settings → Policies)
  - `Política de privacidade` → política de privacidade (Settings → Policies)
  - Instagram já está no tema, não precisa entrar no menu.
- [ ] **Conferir se as políticas existem** — Settings → Policies. Se estiverem vazias, os dois links acima não têm destino.

## Prova social

- [ ] **Loox** — verificar se há avaliação real acumulada no Booster e se dá pra exportar. É o que destrava as seções desativadas da Etapa 1 e o bloco da Etapa 2.

## Só com "pode publicar" explícito — Etapa 4

- [ ] Publicar o Craft (#164972953635) no lugar do Booster Premium 2.0.
- [ ] Desativar o modo senha ("Abertura em breve"). **Decisão separada da publicação.**
- [ ] Revisar apps que o Craft não usa (Loox, Yampi) — cada script custa conversão.

---

## Feito
_(nada ainda)_
