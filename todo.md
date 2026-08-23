# todo.md — pendências

Tudo o que ainda falta fazer. Regras de acesso ao admin: `CLAUDE.md` §4.

## Gabriel — revisar no `shopify theme dev`

- [ ] **todas as imagens** — .
- [ ] **rodapé novo** — conferir em 390px e 1280px: coluna da marca (logo + tagline + Instagram), "Fale com a gente" com botão de WhatsApp, "Links rápidos" em coluna única sem seta, banner só com Pix e PayPal (confirmar que o ícone Pix renderiza). O modelo aprovado não mostra o banner de pagamento — ficou mantido do pedido anterior; se não quiser, é só desligar "payment_enable" na seção do rodapé.

## Admin da Shopify

Só se resolve no admin, pelo navegador.

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

