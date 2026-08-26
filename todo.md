# todo.md — pendências

Tudo o que ainda falta fazer. Regras de acesso ao admin: `CLAUDE.md` §4.

## Amanhã (2026-08-27) — prioridade

- [ ] **BUG — "Adicionar ao carrinho" trava ao voltar do carrinho** (2026-08-26).
  Com item no carrinho, o cliente vai para `/cart`, volta pelo botão do navegador
  e o "Adicionar ao carrinho" não responde mais. **É regressão da mudança de
  hoje** (`cart_type: notification → page`): antes o `this.cart` existia e o
  `.finally()` limpava o estado do botão.
  Diagnóstico em `assets/product-form.js`: `onSubmitHandler` marca
  `aria-disabled="true"` + `.loading` antes do fetch (linhas 26-28) e, sem
  `cart-notification`/`cart-drawer` na página, navega com
  `window.location = routes.cart_url` (linhas 70-73). No voltar, o bfcache
  restaura o DOM com o botão ainda desabilitado, e a linha 22
  (`if aria-disabled === true → return`) engole todo clique seguinte.
  Não existe listener de `pageshow` em nenhum JS do tema.
  Correção provável: ouvir `pageshow` com `event.persisted` e limpar
  `aria-disabled`, `.loading` e o spinner. Testar em celular real — bfcache se
  comporta diferente no Safari iOS.
  Verificar de passagem se o mesmo trava o botão novo `finalizar_compra`.
- [ ] **Conferir preço** (2026-08-26) — [PENDENTE: o Gabriel precisa dizer o que
  exatamente está errado]. R$ 109,90 é o preço de referência no `CLAUDE.md`.
  Falta saber se o problema é preço por variante, por kit, ou preço comparativo.
  Cruza com o rename dos kits, que já pede "conferir preço/estoque das variantes".
  Preço vive nas variantes, no admin — não é coisa de tema.

## Gabriel — revisar no `shopify theme dev`

- [ ] **todas as imagens** — .
- [ ] **rodapé novo** — conferir em 390px e 1280px: coluna da marca (logo + tagline + Instagram), "Fale com a gente" com botão de WhatsApp, "Links rápidos" em coluna única sem seta, banner só com Pix e PayPal (confirmar que o ícone Pix renderiza). O modelo aprovado não mostra o banner de pagamento — ficou mantido do pedido anterior; se não quiser, é só desligar "payment_enable" na seção do rodapé.

## Admin da Shopify

Só se resolve no admin, pelo navegador.

- [x] **Reinstalar o script do Yampi no tema Craft** (2026-08-26) — feito. Confirmado no tema publicado: `layout/theme.liquid` linhas 407-409 chamam `snippets/YampiSnippet.liquid`, injeção única. **Repetir toda vez que o tema publicado mudar** — os três pushes de 2026-08-26 usaram `--only` com `--nodelete` e não tocaram no `theme.liquid`, por isso não precisou repetir.
- [ ] **Decidir o app AReviews** (2026-08-26) — apareceu no `shopify theme pull` de hoje: dois blocos no `templates/product.json` (nota+estrelas abaixo do título, seção de reviews no fim) e o snippet `aliexpress_reviews.liquid` carregando script de `areviewsapp.com`. Ninguém decidiu se fica. O `CLAUDE.md` §7 diz "nenhum app novo — cada script injetado custa conversão". Se sair, é desinstalar no admin, não apagar arquivo.
- [ ] **Formato decimal das variantes de tamanho** (2026-08-26) — os rótulos usam ponto (`8.1cm a 10cm`) e o site usa vírgula (`8,1 – 10,0 cm`). Em pt-BR a vírgula é a forma certa. Renomear no admin se quiser padronizar.
- [ ] **Zona de envio** (2026-08-26) — o checkout ofereceu País "Austrália" / Estado "Vitória". Conferir Configurações → Frete e entrega: se a loja só entrega no Brasil, restringir a zona.

- [ ] **Menu `footer` (navegação)** — "Como comprar?" e "Fale conosco" já removidos pelo Gabriel (2026-08-23). Falta: conferir se "Envios e entregas" e "Trocas e garantia" apontam para página com conteúdo real — o texto de troca ainda está pendente.
- [ ] **Renomear valores da opção "Selecione o KIT"** no produto Sapatos Duque (2026-08-23): "Kit One = 4 PATAS" → "4 PATAS - Primeiro Rolê" · "Kit Double Duque = 8 PATAS" → "8 PATAS - Um Usa Outro Seca" · "Kit Duque Economy = 16 PATAS" → "16 PATAS - Matilha". Os valores vivem nas variantes do produto, não no tema. Conferir preço/estoque das variantes depois do rename.


## Conteúdo que falta — trava a publicação, não invento nenhum

- [ ] **Prazo de entrega** (FAQ)
- [ ] **Custo do frete** (FAQ + barra de anúncio)
- [ ] **Política de troca** (FAQ)
- [ ] **Instruções de lavagem** (FAQ)
- [x] **Confirmar os 3 passos de medida** contra o vídeo "SapatosDuque Como Medir" — texto final do Gabriel aplicado na home e no produto (2026-08-23)
- [ ] **Loox** — ver se há avaliação real nos 1.979 pedidos. Destrava Prova social e Depoimentos.

## Meu, quando o conteúdo chegar

- [ ] Escrever as 4 respostas do FAQ no `collapsible-content` e ligar a seção
- [ ] Ligar Prova social e Depoimentos (home e produto) com o material do Loox
- [ ] Reescrever e reativar a barra de anúncio com frete ou prazo real
- [ ] Escrever frete e prazo no bloco `frete_prazo` e tirar o `disabled` (`templates/product.json`)
- [ ] Linha de parcelamento abaixo do preço, quando houver o nº de parcelas

## Dívida técnica

- [ ] **Mapa rótulo→faixa morto** em `snippets/product-variant-options.liquid` — casa com `'0='`, `'PP='` etc., mas as variantes no admin agora se chamam `0= (7cm a 8cm)`, então nunca casa e o `<span class="pdd-faixa-cm">` não renderiza. Os valores foram corrigidos em 2026-08-26 para não ser armadilha, mas o código continua morto. Decidir: remover, ou encurtar os rótulos no admin e deixar o tema renderizar a faixa.
- [ ] **Rótulo longo dos chips de tamanho no mobile** — `0= (7cm a 8cm)` numa pill em 390px. Conferir se quebra. Some se a decisão acima for encurtar o rótulo no admin.

