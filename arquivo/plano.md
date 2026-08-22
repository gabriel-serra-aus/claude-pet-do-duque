# Plano — Repaginada Pet do Duque

Só planejamento. Regras de trabalho ficam no `CLAUDE.md`; texto e imagens do site ficam no `conteudo.md`.

Base de trabalho: tema **Craft #164972953635** (unpublished). O Booster Premium continua no ar até o Craft ficar pronto.

Última atualização: 22/08/2026

---

## Escopo

Simplificar para **3 páginas + a página de produto refeita**.

| Página | Rota | Template |
|---|---|---|
| Home | `/` | `templates/index.json` |
| Quem somos | `/pages/quem-somos` | `templates/page.quem-somos.json` (novo) |
| Como medir | `/pages/como-medir` | `templates/page.como-medir.json` (novo) |
| Produto — Sapatos Duque | `/products/...` | `templates/product.json` |

Fora dessa lista sai do menu. Páginas legais (troca, privacidade, contato) ficam só no rodapé.

**Menu principal:** Home · Quem somos · Como medir · Comprar
**Rodapé:** WhatsApp · Trocas e devoluções · Política de privacidade · Instagram

---

## Estágios

Ordem: o dinheiro primeiro, o institucional por último. Um estágio por vez, uma página por request.

### E0 — Ponto de retorno
- [ ] `shopify theme push --unpublished --theme "Backup AAAA-MM-DD"`
- [ ] Export de produtos/páginas/navegação pelo admin (o tema não cobre isso)

### E1 — Página de produto
- [ ] Reordenar blocos do `main-product` conforme `conteudo.md`
- [ ] Descer o aviso "cor sujeita a estoque" para junto do seletor de cor
- [ ] Remover `disclosures` e `related-products`
- [ ] Migrar specs para metafields/variantes
- [ ] Seção "Como calçar" (vídeo `DgTqO9V_l_I`)
- [ ] FAQ (`collapsible-content`)
- [ ] `alt` em todas as imagens
- [ ] QA mobile + desktop, antes/depois para o Gabriel
- [ ] *Decidir depois da base de pé:* botão de compra fixo no mobile vale o CSS custom?

### E2 — Como medir
- [ ] Criar página no admin (Gabriel) + `templates/page.como-medir.json`
- [ ] Passo a passo em `rich-text`
- [ ] Vídeo `YjO_qQHzQL4` (migrado da home)
- [ ] Tabela de tamanhos em HTML — não imagem
- [ ] `collapsible-content` de dúvidas de medida
- [ ] CTA duplo: comprar + WhatsApp
- [ ] QA mobile + desktop, antes/depois

### E3 — Home
- [ ] Barra de anúncio
- [ ] Banner principal — um produto, uma promessa, um CTA
- [ ] Prova social *(só entra com dado real)*
- [ ] Coleção em destaque com preço no card
- [ ] "Por que comprar" — reescrever o `multicolumn_mRRbhi`
- [ ] Chamada do guia de tamanho → `/pages/como-medir`
- [ ] UGC *(só entra com foto real)*
- [ ] FAQ
- [ ] Remover: `collage-0` (vazia), `custom_liquid_Dqpzcn` (3 vídeos duplicados, largura fixa em pixel), `custom_liquid_Lpb6Vi` (vazia), `video_WRKBFz` (placeholder "Vídeo")
- [ ] Mover o argumento de solado antiderrapante/displasia para o produto ou para os 3 benefícios
- [ ] QA mobile + desktop, antes/depois

### E4 — Quem somos
- [ ] Criar página no admin (Gabriel) + `templates/page.quem-somos.json`
- [ ] `rich-text` com a história + `image-with-text` com foto do Duque
- [ ] CTA WhatsApp
- [ ] QA mobile + desktop, antes/depois

### E5 — Limpeza e fechamento
- [ ] Seções órfãs removidas
- [ ] Strings em inglês corrigidas em `locales/pt-BR.json`
- [ ] `alt` em 100% das imagens
- [ ] Menu e rodapé montados no admin (Gabriel)
- [ ] `shopify theme check` limpo
- [ ] QA final mobile + desktop
- [ ] Gabriel publica o Craft

---

## Bloqueios

Estágios travados até o `conteudo.md` sair do `[PENDENTE]`:

| Estágio | Depende de |
|---|---|
| E1 | preço, cores/tamanhos, frete, prazo, política de troca, material |
| E2 | tabela de tamanhos oficial, orientação de arredondamento |
| E3 | mensagem do anúncio, avaliações/nº de clientes, fotos de cliente |
| E4 | história do Duque, foto do Duque |

Lista completa: `conteudo.md` → *Pendências de conteúdo*.
