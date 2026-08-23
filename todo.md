# todo.md — pendências

Tudo o que ainda falta fazer. Regras de acesso ao admin: `CLAUDE.md` §4.

## Gabriel — revisar no `shopify theme dev`

- [ ] **Ícones dos benefícios da home** — dizer se os 3 SVG servem. Se não: eu ajusto o desenho, você manda 3 ícones seus, ou foto real no lugar.
- [ ] **Texto dos benefícios editável?** Hoje vive no snippet `pdd-beneficios.liquid`, fora do theme editor. Para voltar ao nativo: subir os 3 SVG de `images/` em Files e trocar a seção para `multicolumn`.
- [ ] **Melhorias da home de 22/08** — vitrine `featured-product`, CTA depois da tabela de medida, vídeos em grade, botão flutuante de WhatsApp no mobile (vive no `theme.liquid`).
- [ ] **Página de produto** — conferir o link "como medir" entre Cor e Tamanho, a faixa em cm nos botões de tamanho e a galeria em `thumbnail_slider`.
- [ ] **Foto para a chamada final da home** — hoje é texto em fundo escuro; com uma foto boa vira `image-banner`.

## Admin da Shopify

Só se resolve no admin, pelo navegador.

- [ ] **Export de conteúdo da loja** → `backups/`. Só produtos têm export nativo (CSV); páginas, políticas, coleções e menus são cópia manual. O corpo de `quem-somos` existe **só** no banco — sem isso, não há de onde restaurar.
- [ ] **Título da página Quem somos:** trocar `QUEM SOMOS?` por `Quem somos` — título e SEO.
- [ ] **Template da página Quem somos:** trocar para `page.quem-somos.json` quando eu criar (Etapa 3).
- [ ] **Rodapé:** WhatsApp · Rastreio · Trocas e devoluções · Política de privacidade · Instagram.

### Catálogo — trava a Etapa 2

- [ ] **Associar cada foto de cor à variante** — faz a foto trocar com a cor; "hide variants' media" já está ligado no template.
- [ ] **Desassociar as ~32 fotos excedentes** do produto (não apagar da biblioteca). Ficam 6–8: 1 por cor + cão calçado + kit + solado.
- [ ] **`alt` em pt-BR nas fotos que ficarem**, citando a cor (Edit alt text — vive no admin, não no tema).
- [ ] **Trocar a descrição do produto** pelo texto da Etapa 2 §4, como texto puro — o `body_html` sujo ainda alimenta SEO, busca e canais externos.
- [ ] **Conferir o nome da opção de tamanho** — precisa conter "tamanho" e manter os rótulos exatos (`0=`, `PP=`…), senão o "como medir" e as faixas em cm somem.
- [ ] **Metafields de specs** (material, composição) — Settings → Custom data → Products.
- [ ] **Revisar variantes** — cor, tamanho e kit com estoque correto.
- [ ] **Renomear os rótulos de tamanho** (tirar o `=`) — muda junto em 3 lugares do tema; ver Dívida técnica.

### Etapa 4 — só com "pode publicar" explícito

- [ ] Publicar o Craft (#164972953635) no lugar do Booster Premium 2.0.
- [ ] Desativar o modo senha — decisão separada da publicação.
- [ ] Revisar apps que o Craft não usa (Loox, Yampi).

## Conteúdo que falta — trava a publicação, não invento nenhum

- [ ] **Prazo de entrega** (FAQ)
- [ ] **Custo do frete** (FAQ + barra de anúncio)
- [ ] **Política de troca** (FAQ)
- [ ] **Instruções de lavagem** (FAQ)
- [ ] **Confirmar os 3 passos de medida** contra o vídeo "SapatosDuque Como Medir"
- [ ] **Loox** — ver se há avaliação real nos 1.979 pedidos. Destrava Prova social e Depoimentos.

## Meu, quando o conteúdo chegar

- [ ] Escrever as 4 respostas do FAQ no `collapsible-content` e ligar a seção
- [ ] Ligar Prova social e Depoimentos (home e produto) com o material do Loox
- [ ] Reescrever e reativar a barra de anúncio com frete ou prazo real
- [ ] Montar as colunas de links do rodapé, depois que o menu existir no admin
- [ ] Escrever frete e prazo no bloco `frete_prazo` e tirar o `disabled` (`templates/product.json`)
- [ ] Linha de parcelamento abaixo do preço, quando houver o nº de parcelas

## Dívida técnica

- [ ] **Locks stale no git** — `index.lock`/`HEAD.lock` aparecem sozinhos e travam commit (3× em 22/08). Contorno: conferir que não há git rodando e apagar o lock. Causa não investigada.
- [ ] **MCP de navegador** — instalar `@playwright/mcp` apontando ao Chrome logado, para QA visual e a fila de admin acima. Montar antes da Etapa 4.
- [ ] **Rótulos de tamanho com `=`** — se renomear no admin, muda junto em 3 lugares do tema: tabela da home (`index.json`), tabela do produto (`product.json`) e mapa de faixas em cm (`product-variant-options.liquid`).
- [ ] **Capas dos vídeos vêm do YouTube**, não do CDN da Shopify (`theme check` acusa `RemoteAsset`) — aceito: nenhum iframe carrega antes do clique. Para zerar, subir 3 capas em Files e voltar à seção `video` nativa.
