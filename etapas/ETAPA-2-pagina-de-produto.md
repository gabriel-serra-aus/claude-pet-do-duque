# Etapa 2 — Página de produto

Depende da Etapa 1 (layout global). Independente da Etapa 3.
Arquivo alvo: `theme/templates/product.json`.

## Objetivo
Produto = só comprar. Nada de vídeo, banner ou FAQ.
Toda educação já está na home (Etapa 1).

> **Decisão do Gabriel (22/08), muda o objetivo acima:** a coluna de compra
> fica enxuta, mas a página ganha corpo abaixo dela — seção de texto
> "O que são os Sapatos Duque" e os **3 vídeos** no formato leve da home
> (capa + play, iframe só no clique). A descrição do admin (com os banners)
> saiu da coluna direita: o bloco `description` não é mais renderizado.

---

## 1. Remover

| Seção / bloco | Motivo |
|---|---|
| `disclosures` | seletor de país/idioma — loja só do Brasil |
| `related-products` | "You may also like" — a loja tem um produto |
| 3 vídeos | já estão na home |
| banners de imagem da descrição | viram texto; o resto já migrou para a home |

Banners a eliminar: `O QUE SÃO?`, `CONFORTÁVEIS`, `AREJADOS`, `QUALIDADE DE VIDA`, `PISOS LISOS`, `FEEDBACKS ABAIXO`.

---

## 2. Galeria

- Reduzir de ~40 para **6 a 8 fotos**: 1 por cor (4) + cão calçado + kit completo + detalhe do solado.
- **Associar cada foto de cor à variante no admin** → a foto principal troca ao mudar a cor. Nativo do Craft, sem app.
- As ~32 restantes: **desassociar do produto, não apagar da biblioteca.**
- WebP, lazy loading fora da dobra, `alt` em pt-BR citando a cor.

---

## 3. Ordem dos blocos em `main-product`

```
1  Título               Sapatos Duque
2  Preço                R$ 109,90 + parcelamento  [PENDENTE: nº parcelas]
3  Prova social         [A DEFINIR]  → bloco DESATIVADO
4  Variante Cor         Preto · Branco · Rosa · Vermelho
5  Link medida          "Não sei o tamanho — como medir" → âncora Como medir na home
6  Variante Tamanho     P- · PP+ · P+ · M+ · G+ · GG+ · XG+ · XXG+
7  Variante Kit         Kit One (4) · Kit Double Duque (8) · Kit Duque Economy (16)
8  Quantidade
9  Botões               Adicionar ao carrinho (primário) · Comprar agora
10 Frete e prazo        [PENDENTE] — caixa destacada, corpo normal
11 Aviso de cor         corpo menor, por último
```

### Regras da caixa de compra
- **Os 3 seletores com todas as opções visíveis, peso visual igual.** Nenhum menu suspenso, nenhum pré-selecionado em detrimento dos outros.
- Mostrar a faixa em cm ao lado de cada tamanho.
- O link de medida fica **colado ao seletor de tamanho** (item 5, antes do 6).

### Aviso de cor — texto novo
Hoje está **acima do preço**. Mover para o item 11 e reescrever:
```
Cor sujeita a estoque. Se faltar, avisamos antes de enviar.
```
> Antes: "Outra opção será enviada se a cor não estiver disponível" — soa como imposição.

### Frete e prazo
`[PENDENTE: Gabriel informa]` — caixa destacada abaixo dos botões, **corpo normal, não letra miúda**.

---

## 4. Descrição

4 a 6 linhas de **texto**. Zero imagem, zero HTML escrito à mão.

```
Asfalto quente queima a patinha. Piso liso derruba. Os Sapatos Duque
resolvem os dois: solado antiderrapante e malha respirável que protege
sem abafar. Para cães com displasia ou artrose, o apoio extra faz
diferença real na caminhada — foi exatamente assim que eles nasceram.
```
`[PENDENTE: material, altura do cano, se é impermeável]`

Fecho — caixa discreta:
```
Como medir, como calçar e dúvidas frequentes  →  na Home
```

Specs (material, composição) em **metafields**. Tamanho/cor/kit em **variantes**. Nunca em texto corrido.

---

## Pronto quando
- [ ] Galeria com 6–8 fotos; a principal troca ao mudar a cor — *admin, ver `ADMIN.md` (tema já com `hide_variants` e `thumbnail_slider`)*
- [x] Cor, Tamanho e Kit com todas as opções visíveis, sem menu suspenso *(22/08 — conferir no dev que a opção se chama "Tamanho", ver `todo.md`)*
- [x] Aviso de cor abaixo dos botões, corpo menor, texto novo *(22/08)*
- [ ] Frete e prazo dentro da caixa de compra, corpo normal — *caixa construída e desativada; falta o dado, ver `skiped.md`*
- [x] Descrição é texto selecionável, 4–6 linhas, zero banner *(22/08 — virou a seção rich-text "O que são os Sapatos Duque" no template; o bloco `description` saiu da página. Limpar o `body_html` no admin continua na fila, por SEO — ver `ADMIN.md`)*
- [x] `disclosures` e `related-products` não existem no template *(22/08)*
- [x] ~~Zero vídeo na página~~ — *decisão do Gabriel (22/08): os 3 vídeos entram, no formato leve da home*
- [ ] Compra de teste completa: variante → carrinho → checkout
- [ ] 100% das fotos com `alt` em pt-BR citando a cor — *admin, junto da limpeza da galeria*
- [ ] Preview em 390px e 1280px; caixa de compra inteira alcançável sem zoom
- [x] `shopify theme check` sem erro *(22/08 — 0 erros; 11 warnings, todos do Craft de fábrica + o `RemoteAsset` aceito na Etapa 1)*
- [x] Antes/depois apresentado ao Gabriel *(22/08)*

## Bloqueia a publicação
parcelamento · frete · prazo · material
