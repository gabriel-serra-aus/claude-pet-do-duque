# skiped.md — o que foi pulado, e por quê

Itens que a etapa previa e **não** foram feitos. Cada um diz qual etapa, o motivo
e o que falta para destravar.

Item resolvido sai daqui e vai para o histórico no fim do arquivo.
Ação que só se resolve no admin da Shopify continua em `ADMIN.md`.
Trabalho pendente meu continua em `todo.md`.

---

## Etapa 0 — Preparação

### Export de produtos, páginas, coleções e navegação

**Status:** pulado por decisão do Gabriel em 22/08.

**Motivo:** a decisão foi olhar primeiro quais páginas ficam de pé, e só então
exportar — evita fazer backup de conteúdo que vai sair. Ninguém além dele mexe
no admin, então o risco de perda por terceiro é nulo.

**O que a Etapa 0 assumia errado:** ela pedia "export de páginas e navegação"
como se fosse um botão. Não é. A Shopify exporta nativamente **produtos,
clientes, pedidos, descontos e estoque** — e nada além disso. Página, coleção,
blog e menu **não têm export nativo**: é cópia manual ou app de terceiro.

**O que fazer quando voltar:**
1. Products → Export → CSV. Guardar em `backups/`.
2. Content → Pages: abrir cada página, botão `<>` (Show HTML), salvar o corpo
   em `backups/pages/<handle>.html`. Anotar título, handle e campos de SEO.
3. Settings → Policies: as políticas (troca, privacidade, termos) vivem aqui,
   separadas das páginas, e também são só banco.
4. Products → Collections: título, handle, se é manual ou automática, e as
   regras ou a lista de produtos.
5. Navegação já está capturada em `backups/navegacao-2026-08-22.md`.

**Risco enquanto isso:** o corpo da página `quem-somos` — a história do Duque,
o diagnóstico de displasia, o primeiro protótipo — existe **só** no banco da
Shopify. Não está em `theme/`, nem no git, nem no tema `Backup 2026-08-22`.
Se ela for editada ou apagada, não há de onde restaurar.

---

## Etapa 1 — Home e layout

### Menu de links do rodapé

**Status:** não construído.

**Motivo:** a Etapa 1 pede WhatsApp · Rastreio · Trocas e devoluções · Política
de privacidade · Instagram no rodapé. O Instagram já está (é setting do tema).
Os outros quatro precisam de um **menu de rodapé**, que não existe na loja — o
rodapé hoje não tem nenhuma coluna de links. Criar menu é ação de admin.

**O que fazer:** ver `ADMIN.md`, seção Etapa 1.

### Ícones dos benefícios na seção nativa

**Status:** resolvido por outro caminho, mas fora do previsto.

**Motivo:** a Etapa 1 pedia 3 ícones WebP 96×96 na seção `multicolumn` nativa.
O campo de imagem dela só aceita arquivo da biblioteca de Files, e não havia
nada lá. Em vez de travar, os ícones foram desenhados em SVG e embutidos no
snippet `pdd-beneficios.liquid`.

**O custo:** o texto das três colunas saiu do theme editor e passou a viver no
snippet. Reversível — ver `todo.md`.

### Chamada final como `image-banner`

**Status:** trocada por `rich-text` em esquema escuro.

**Motivo:** a etapa pedia `image-banner`, mas não definiu imagem. Sem imagem, o
Craft renderiza o próprio placeholder cinza, o que reprovaria no critério
"zero placeholder do tema visível".

**O que fazer:** havendo uma foto boa, trocar o tipo da seção e apontar a
imagem. Uma configuração, sem reescrever conteúdo.

### Miniatura dos vídeos vinda do CDN da Shopify

**Status:** vem do YouTube, não do CDN da Shopify.

**Motivo:** a seção `video` nativa monta a capa a partir de `cover_image`, que
exige arquivo em Files. Sem ele, aparecia o placeholder de camisetas do Craft.
A solução usa a miniatura publicada pelo próprio YouTube.

**O custo:** `shopify theme check` acusa `RemoteAsset` — a imagem não passa pelo
CDN da Shopify. Aceito conscientemente: em troca, nenhum iframe carrega antes do
clique, o que deixa a home mais leve do que estava.

**O que fazer se quiser tudo no CDN:** subir 3 capas em Files e voltar às seções
`video` nativas.

### Seções desativadas por falta de conteúdo real

**Status:** construídas e desligadas. Não é atraso, é o método —
`[A DEFINIR]` nunca vira texto inventado.

| Seção | O que falta |
|---|---|
| Prova social | número ou depoimento real. Verificar o Loox: 1.979 pedidos podem ter avaliação acumulada |
| Depoimentos | 3 depoimentos reais de cliente |
| FAQ | 4 das 5 respostas: prazo de entrega, custo do frete, política de troca, instruções de lavagem |

### Barra de anúncio

**Status:** desativada.

**Motivo:** o texto no ar era "Seja bem-vindo à nossa loja!", que não informa
nada. A etapa manda desativar quando não houver frete ou prazo real.

**O que fazer:** havendo mensagem real de frete ou prazo, escrever e reativar.

---

## Etapa 2 — Página de produto

### Frete e prazo na caixa de compra

**Status:** construído e desativado.

**Motivo:** a etapa pede caixa destacada com frete e prazo, e os dois são
`[PENDENTE: Gabriel informa]`. O bloco `custom_liquid` existe no template com
a caixa pronta (`.pdd-frete`), desligado. `[PENDENTE]` nunca vai ao ar.

**O que fazer:** com o dado real, escrever o texto e tirar o `disabled` do
bloco `frete_prazo` em `templates/product.json`.

### Prova social ao lado do preço

**Status:** construído e desativado — mesmo caso da home.

**Motivo:** `[A DEFINIR]` até a verificação do Loox (ver `ADMIN.md`).

### Parcelamento junto ao preço

**Status:** não construído.

**Motivo:** o bloco `price` do Craft não mostra parcelamento — no Brasil isso
vem do checkout ou de app, e a regra é nenhum app novo. Além disso o nº de
parcelas é `[PENDENTE]`. Quando houver o dado, dá para escrever a linha em
`custom_liquid` abaixo do preço, sem app.

### Faixa em cm ao lado de cada tamanho

**Status:** feito, com dependência frágil assumida.

**Motivo:** os rótulos das variantes (`PP=` etc.) não carregam a faixa em cm,
então o mapa rótulo → faixa está no snippet `product-variant-options.liquid`,
espelhando a tabela "Como medir" — que desde 22/08 vive na home **e** na página
de produto. São **quatro** lugares que têm que casar: variantes no admin,
tabela da home, tabela do produto, mapa do snippet. Já registrado em `todo.md`
junto da pendência de renomear os rótulos.

---

## Histórico

- **22/08 — Menu principal.** Estava pendente na Etapa 0. Resolvido: 3 itens,
  Rastreio fora, "Sapatos Duque" apontando direto ao produto.
- **22/08 — Miniatura dos vídeos.** A primeira correção não funcionou porque
  assumi que o YouTube devolveria erro quando falta `maxresdefault`. Ele devolve
  404 **com um JPEG válido no corpo** — o logo cinza de 120×90 — e o navegador
  trata como imagem carregada. A queda passou a ser decidida pela largura.
