# todo.md — pendências

Tudo o que ainda falta fazer. Regras de acesso ao admin: `CLAUDE.md` §4.

## Gabriel — revisar no `shopify theme dev`

- [ ] **todas as imagens** — .
- [ ] **rodapé novo** — conferir em 390px e 1280px: coluna da marca (logo + tagline + Instagram), "Fale com a gente" com botão de WhatsApp, "Links rápidos" em coluna única sem seta, banner só com Pix e PayPal (confirmar que o ícone Pix renderiza). O modelo aprovado não mostra o banner de pagamento — ficou mantido do pedido anterior; se não quiser, é só desligar "payment_enable" na seção do rodapé.

## Admin da Shopify

Só se resolve no admin, pelo navegador.

- [ ] **Menu `footer` (navegação)** — remover os itens "Como comprar?" e "Fale conosco" (decisão do Gabriel, 2026-08-23). Ficam: "Perguntas frequentes" → `/pages/perguntas-frequentes` · "Envios e entregas" · "Trocas e garantia" (conferir se as duas últimas apontam para página com conteúdo real — o texto de troca ainda está pendente).


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
- [ ] Escrever frete e prazo no bloco `frete_prazo` e tirar o `disabled` (`templates/product.json`)
- [ ] Linha de parcelamento abaixo do preço, quando houver o nº de parcelas

## Dívida técnica

