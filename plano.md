# Plano — Repaginada Pet do Duque

Documento vivo. Registra o que vamos mudar, o que já foi feito e o que ainda falta decidir.
Base de trabalho: tema **Craft #164972953635** (unpublished). O Booster Premium continua no ar até o Craft ficar pronto.

Última atualização: 16/08/2026

---

## 0. Regra de trabalho — uma página por vez

**Cada request trata de uma única página.** Nunca edito duas páginas na mesma sessão, mesmo que a mudança pareça se propagar naturalmente.

- No início do trabalho, fica claro qual é a página alvo: **Home**, **Quem somos**, **Como medir** ou **Produto**.
- Se algo exigir tocar outra página — menu, seção compartilhada, snippet reusado — eu **paro, anoto aqui como pendência e pergunto**. Não edito por conta.
- Arquivos globais (`locales/pt-BR.json`, `assets/custom.css`, `settings_data.json`) só mudam no que serve à página em foco.
- O antes/depois apresentado ao Gabriel é sempre de uma página só.

---

## 1. Escopo acordado

**Simplificar o site para 3 páginas + a página de produto refeita.**

| Página | Rota | Template | Status |
|---|---|---|---|
| Home | `/` | `templates/index.json` | a reescrever |
| Quem somos | `/pages/quem-somos` | `templates/page.quem-somos.json` (novo) | a criar |
| Como medir | `/pages/como-medir` | `templates/page.como-medir.json` (novo) | a criar |
| Produto — Sapatos Duque | `/products/...` | `templates/product.json` | a refazer |

Tudo que não estiver nessa lista sai do menu. Páginas legais (troca, privacidade, contato) ficam **só no rodapé**, não no menu principal.

---

## 2. Home — estrutura alvo

Ordem das seções (todas nativas do Craft, sem Liquid custom):

1. **Barra de anúncio** — frete/prazo ou oferta ativa. `[PENDENTE: qual a mensagem? frete grátis a partir de X?]`
2. **Banner principal** (`image-banner`) — um produto, uma promessa, um CTA "Ver tamanhos" / "Comprar agora"
3. **Prova social** (`multicolumn` ou `rich-text`) — avaliações ou "X clientes atendidos". `[PENDENTE: temos avaliações reais? número de vendas?]`
4. **Coleção em destaque** (`featured-collection`) — os sapatinhos, preço visível no card
5. **Por que comprar** (`multicolumn`) — 3 benefícios concretos, ícone + uma linha
6. **Guia de tamanho — chamada curta** (`image-with-text`) com CTA para `/pages/como-medir`
7. **Foto real de cliente / UGC** (`collage` ou `image-banner`). `[PENDENTE: temos fotos de clientes?]`
8. **FAQ** (`collapsible-content`) — troca, prazo, tamanho, lavagem
9. **Rodapé** — WhatsApp, políticas, redes

### O que sai da home atual

- `collage-0` — vazia e desativada → **remover**
- `custom_liquid_Dqpzcn` — bloco de 3 vídeos do YouTube com HTML/CSS inline → **remover da home**. O vídeo "Como medir" migra para a página *Como medir*; o "Como calçar" vai para a página de produto. O "Recomendado por especialistas" `[PENDENTE: mantemos? onde?]`
- `custom_liquid_Lpb6Vi` — vazia → **remover**
- `video_WRKBFz` — título placeholder "Vídeo", solta na página → **remover**
- `multicolumn_mRRbhi` (Entregamos / Pagamento seguro / Suporte) — **manter o conteúdo, reescrever**: título placeholder "Várias colunas" precisa sair, texto em CAIXA ALTA vira caixa normal, e o texto de "Pagamento seguro" não deve citar gateway (informação de bastidor, não benefício)
- `image_with_text_8MrkyH` — o texto sobre solado antiderrapante/displasia é bom, mas é **argumento de produto**, não abertura de home → move para a página de produto ou vira um dos 3 benefícios

---

## 3. Quem somos

Página institucional curta, um scroll no mobile. É onde o **Duque** aparece — a história da marca.

Seções: `rich-text` (a história) + `image-with-text` (foto do Duque) + CTA para WhatsApp.

`[PENDENTE: Gabriel escreve ou conta a história do Duque e do começo da loja — não invento.]`

---

## 4. Como medir

Página que resolve a objeção nº 1 de calçado. Precisa ser **operacional**, não decorativa.

Estrutura:

1. `rich-text` — passo a passo em 3 passos, frase curta
2. **Vídeo** de medição (o `YjO_qQHzQL4` que hoje está enterrado na home)
3. **Tabela de tamanhos** — medida da patinha (cm) × tamanho
4. `collapsible-content` — dúvidas de medida ("ficou entre dois tamanhos?", "e se errar?")
5. CTA final: "Comprar agora" + "Falar no WhatsApp"

`[PENDENTE: a tabela de tamanhos oficial (cm por tamanho). Não invento medida.]`

Decisão técnica pendente: tabela em HTML dentro de `rich-text` vs. imagem. **Recomendo HTML** — imagem de tabela não é legível no mobile nem acessível.

---

## 5. Página de produto — refazer

### Problemas hoje

- Bloco de texto solto no topo: *"IMPORTANTE: Cor sujeita a estoque..."* — está **acima do preço**, matando a conversão com um aviso negativo. Vai para perto do seletor de cor, em texto menor
- `disclosures` (seletor de país/idioma) numa loja só do Brasil → **remover**
- `related-products` ("You may also like", em inglês) numa loja de **um produto** → **remover**
- Sem prova social, sem link para guia de tamanho, sem FAQ

### Estrutura alvo

Blocos do `main-product`, nesta ordem:

1. Título
2. Preço + parcelamento
3. Prova social curta (avaliação/nº de clientes) `[PENDENTE: dado real]`
4. Seletor de variante (tamanho e cor)
5. **Link "Não sei o tamanho — como medir"** → `/pages/como-medir`
6. Aviso de cor sujeita a estoque (texto pequeno, aqui)
7. Quantidade
8. Botões de compra
9. Frete e prazo — informação de primeira linha, não letra miúda
10. Descrição (benefício primeiro: asfalto quente, piso escorregadio, apoio para cão com displasia/lesão)

Seções abaixo do produto:

- **Como calçar** — o vídeo `DgTqO9V_l_I`
- **FAQ** (`collapsible-content`) — troca, prazo, lavagem, tamanho

Specs (tamanho, material, cor) vão em **metafields/variantes**, não em texto corrido na descrição.

`[PENDENTE: botão de compra fixo no mobile — vale o CSS custom? Decidir depois que a página base estiver de pé.]`

---

## 6. Navegação

**Menu principal:** Home · Quem somos · Como medir · Comprar
**Rodapé:** WhatsApp · Trocas e devoluções · Política de privacidade · Instagram

⚠️ Menu e páginas vivem no **banco da loja, não no tema** — Gabriel cria/edita pelo admin. O tema só referencia.

---

## 7. Ordem de execução

1. `shopify theme push --unpublished --theme "Backup AAAA-MM-DD"` antes de começar (ponto de retorno)
2. Página de produto — é onde o dinheiro entra
3. Como medir — desbloqueia a objeção do produto
4. Home
5. Quem somos
6. Limpeza: seções órfãs, strings em inglês em `locales/pt-BR.json`, `alt` em todas as imagens
7. `shopify theme check` + QA mobile/desktop no preview
8. Antes/depois para o Gabriel → só então publicar

---

## 8. Pendências bloqueantes

Conteúdo que **não invento** e trava a entrega:

- [ ] Tabela de tamanhos oficial (cm → tamanho)
- [ ] Prazo de entrega e política de frete (tem frete grátis? a partir de quanto?)
- [ ] Política de troca/devolução
- [ ] Avaliações reais ou número de clientes atendidos
- [ ] Fotos de clientes (UGC)
- [ ] História do Duque / da marca, para a página Quem somos
- [ ] Instruções de lavagem e material dos sapatinhos
