# Etapa 1 — Home e layout global

**CONCLUÍDA em 22/08/2026.** Não bloqueia mais as Etapas 2 e 3.
O que ficou de fora, e por quê, está em `skiped.md`. O que sobrou de trabalho
está em `todo.md`.

Depende da Etapa 0.
Arquivo alvo: `theme/templates/index.json` + configurações globais.

## Objetivo
Home vira a página de venda. Toda a educação sobre o produto vive aqui.

## Como executar

Antes de editar, mostrar o estado atual das seções de `index.json`.

Trabalhar em 5 blocos. **Ao fim de cada um, parar e mostrar o antes/depois ao Gabriel antes de seguir:**

1. Remover as 4 seções (item 1)
2. Banner principal · Produto em destaque · Por que comprar (seções 3, 5, 6)
3. Como medir, com a tabela de tamanhos · Vídeos de uso (seções 7, 8)
4. FAQ · Chamada final · Prova social e Depoimentos, ambas `disabled` (seções 4, 9, 10, 11)
5. Layout global · `locales/pt-BR.json` (item 4)

Fechar com `shopify theme check` e a checklist "Pronto quando" preenchida.

---

## 0. Dados confirmados (22/08, via `shopify theme dev`)

Verificado contra a loja, não presumido. Substitui qualquer valor divergente abaixo.

| Dado | Valor real |
|---|---|
| Handle do produto | `sapatos-duque-c2-original` |
| Preço | R$ 109,90 a R$ 344,90 — `price_min` confere com "A partir de R$ 109,90" |
| Variantes | 96 no total, 92 em estoque |
| Cores (4) | Preto, Branco, Roxo, Vermelho |
| Kits (3) | Kit One (4 patas), Double Duque (8), Duque Economy (16) |
| Vermelho da marca | `#B3342B` — 6,10:1 com branco, 5,19:1 sobre `#efecec`. Passa AA. Provisório. |

**Tamanhos — os nomes do plano original não existem na loja.** As faixas em cm batem,
os rótulos não. Usar sempre os reais, senão o cliente não casa a tabela com o seletor:

| Rótulo real | Comprimento da patinha |
|---|---|
| `0=` | 7,0 – 7,5 cm |
| `PP=` | 7,6 – 9,0 cm |
| `P=` | 9,1 – 11,0 cm |
| `M=` | 11,1 – 13,0 cm |
| `G=` | 13,1 – 14,0 cm |
| `GG=` | 14,1 – 16,0 cm |
| `XG=` | 16,1 – 19,0 cm |
| `XXG=` | 19,1 – 21,0 cm |

O sufixo `=` parece erro de digitação virado permanente. Renomear é ação de admin — fila da Etapa 2.

### Decisões técnicas tomadas

- **Tabela de tamanhos vai em `custom_liquid`, não em `rich-text`.** O campo `text` do
  rich-text é tipo `richtext`, que a Shopify limita a `<p>`, `<strong>`, `<a>` e listas —
  `<table>` é removido. Caso claro de "custom_liquid quando ganha".
- **`4 cores · 8 tamanhos · 3 kits` vai no campo `description` da featured-collection**
  (opção A, aprovada pelo Gabriel). Não editar `snippets/card-product.liquid`: é
  compartilhado com a página de coleção e com produtos relacionados.
- **Chamada final vira `rich-text` em esquema escuro, não `image-banner`.** Não há imagem
  definida para ela, e `image-banner` sem imagem mostra o placeholder do Craft — reprova
  no "zero placeholder". Trocar para `image-banner` quando houver foto.

### Menu principal

Estado anterior registrado em `backups/navegacao-2026-08-22.md`. Alvo:
`Início` · `Sapatos Duque` (→ produto) · `Quem somos`. Rastreio sai.

---

## 1. Remover da home

Deletar de `templates/index.json`:

| Seção | Motivo |
|---|---|
| `collage-0` | vazia e desativada |
| `custom_liquid_Dqpzcn` | vídeos duplicados — passam a existir uma vez só, na seção 8 |
| `custom_liquid_Lpb6Vi` | vazia |
| `video_WRKBFz` | placeholder "Vídeo" do tema |

---

## 2. Ordem final das seções

```
1  announcement-bar      Barra de anúncio
2  header                Cabeçalho
3  image-banner          Banner principal
4  rich-text             Prova social          [DESATIVADA]
5  featured-collection   Produto em destaque
6  multicolumn           Por que comprar
7  rich-text + video     Como medir
8  video ×2              Vídeos de uso
9  multicolumn           Depoimentos           [DESATIVADA]
10 collapsible-content   FAQ
11 image-banner          Chamada final
12 footer                Rodapé
```

---

## 3. Conteúdo por seção

### 1. announcement-bar
`[PENDENTE: frete/prazo]` — se não houver mensagem real, **desativar a seção**.

### 3. image-banner (reusar `image_banner_hero`)
```
Título:     Mais segurança para o seu cão
Texto:      Proteção, conforto e estabilidade em todos os passos.
Preço:      A partir de R$ 109,90        ← NOVO, adicionar bloco text
Botão 1:    Comprar agora    → produto
Botão 2:    Ver tamanhos     → âncora da seção 7
```
- Imagem: `hero2_duque_v1.webp`
- Alt: `Labrador chocolate usando Sapatos Duque vermelhos sobre piso liso`
- Mobile: `show_text_below: true`

### 4. rich-text — Prova social
Criar com `"disabled": true`. Conteúdo `[A DEFINIR]`. **Não inventar número.**

### 5. featured-collection (já existe)
```
Título: Sapatos Duque
```
Adicionar no card a linha: `4 cores · 8 tamanhos · 3 kits`
Botão: `Escolher tamanho e cor`

### 6. multicolumn — reescrever `multicolumn_mRRbhi`
Apagar o título placeholder `Várias colunas`. Sair da CAIXA ALTA. Não citar gateway.
```
Título: Por que os donos escolhem

Piso liso sem escorregão
Solado antiderrapante que dá firmeza em cerâmica, porcelanato e madeira.

Proteção no asfalto quente
Malha respirável que protege a patinha sem abafar.

Apoio para displasia e artrose
Mais estabilidade na caminhada de cães com problema articular.
```
Ícones: 3 arquivos WebP 96×96 `[PENDENTE]`. Alt em pt-BR.

> O conteúdo antigo (Entregamos / Pagamento / Suporte) migra para o rodapé ou sai.

### 7. rich-text + video — Como medir
```
Título: Como medir a patinha

1. Coloque a patinha do cão sobre uma folha de papel, com o peso apoiado.
2. Marque o ponto mais atrás e o ponto mais à frente da patinha.
3. Meça a distância entre as duas marcas. Esse é o comprimento.
```
`[PENDENTE: Gabriel confirma os 3 passos contra o vídeo]`

Vídeo: `YjO_qQHzQL4`

**Tabela em HTML dentro do rich-text. Nunca imagem.**

**Usar a tabela da seção 0** — os rótulos aqui estavam errados (`P-`, `PP+`…) e foram removidos para ninguém copiar por engano.

Dar `id` à seção para a âncora do botão 2 do banner.

### 8. video ×2
```
Como calçar                      → DgTqO9V_l_I
Recomendado por especialistas    → XTAnYxuBwWg
```
Seção nativa `video`, com facade.

### 9. multicolumn — Depoimentos
Criar com `"disabled": true`. 3 colunas, conteúdo `[A DEFINIR]`.

### 10. collapsible-content — FAQ
5 blocos. **Bloco sem resposta real fica desativado.**
```
Qual o prazo de entrega?          [PENDENTE]
Quanto custa o frete?             [PENDENTE]
E se o tamanho não servir?        [PENDENTE — política de troca]
Como lavo os sapatinhos?          [PENDENTE]
Meu cão vai se acostumar?         [Gabriel confirma texto]
```

### 11. image-banner — Chamada final
```
Título:  Pronto para dar mais segurança ao seu cão?
Botão 1: Comprar agora      → produto
Botão 2: Falar no WhatsApp  → https://wa.me/5521993438017
```
Incluir uma linha com link para `/pages/quem-somos`.

### 12. footer
Traduzir em `locales/pt-BR.json`:
- `Subscribe to our emails` → `Assine e receba novidades`
- o texto da lista de e-mails

Links: WhatsApp · Rastreio · Trocas e devoluções · Política de privacidade · Instagram `[PENDENTE: handle]`

---

## 4. Layout global

Configurar em **Theme settings** (não em CSS, não dentro de seção):

- **2 esquemas de cor apenas.** Claro para o corpo; escuro para announcement-bar, footer e chamada final.
- **Acento:** vermelho da marca, só em botão primário e badge de preço.
- **Tipografia:** fontes do Craft, sem substituir. Reduzir a escala de títulos — o padrão do Craft empurra conteúdo para fora da dobra no mobile.
- **Espaçamento:** reduzir padding vertical das seções. É o ajuste de densidade principal — por configuração, sem CSS.
- **Header:** logo centralizado, sticky. Remover ícone de conta.
- **CSS próprio:** só em `assets/custom.css`, carregado no `theme.liquid`. Nunca `base.css`. Comentar a razão de cada regra.
- **`locales/pt-BR.json`:** auditar de ponta a ponta. Zero string em inglês visível.

---

## Pronto quando — fechado em 22/08/2026

- [x] Seções na ordem prevista — 11 em `index.json` (8 no ar, 3 desligadas),
      mais `header` e `footer` nos grupos. A contagem de 12 do plano original
      somava `announcement-bar`, `header` e `footer`, que não vivem no
      `index.json`; a barra de anúncio ficou desativada por falta de mensagem real
- [x] `collage-0`, `custom_liquid_Dqpzcn`, `custom_liquid_Lpb6Vi` e `video_WRKBFz` removidas
- [x] Zero placeholder do tema visível — saíram "Várias colunas", "Vídeo" e o
      desenho de camisetas que o Craft usava como capa dos vídeos
- [x] Tabela de tamanhos é texto HTML selecionável — 8 linhas, em `custom_liquid`
      porque o campo `richtext` da seção nativa remove `<table>`
- [x] 100% das imagens com `alt` em pt-BR — verificado no HTML renderizado
- [x] Rodapé e header em pt-BR — nenhuma string em inglês renderizando
- [x] Prova social e Depoimentos existem e estão `disabled`
- [x] Preview em 390px e 1280px, sem rolagem horizontal — aprovado pelo Gabriel em 22/08
- [x] `shopify theme check` sem erro — 0 erros; warnings restantes são
      pré-existentes ou esperados (`RemoteAsset` na miniatura do YouTube)
- [x] Antes/depois apresentado ao Gabriel

### Fora do previsto, decidido durante a execução

- Hero alinhado ao `.page-width` do tema; `page_width` de 1000 para 1200
- Vermelho da marca `#B3342B` no botão primário do esquema claro
- Vídeos e benefícios em snippet com SVG e miniatura do YouTube, por falta de
  arquivo na biblioteca de Files
- Chamada final como `rich-text` escuro em vez de `image-banner`, por falta de imagem

## Bloqueia a publicação
frete · prazo · política de troca · instruções de lavagem · confirmação dos 3 passos de medida

Estes cinco continuam abertos e estão em `todo.md`. Mantêm o FAQ, a Prova social
e os Depoimentos desligados, mas **não** impedem seguir para as Etapas 2 e 3.

- **Foto DSC_3182 nos Files** (22/08) — a seção "A História dos Sapatos Duque" da
  home referencia `shopify://shop_images/DSC_3182.jpg`. A foto não está no tema:
  precisa existir em Content → Files com esse nome exato (ideal: converter para
  WebP e ajustar a referência no theme editor). Enquanto não existir, a seção
  mostra o slot de imagem vazio. Falta também `alt` descritivo em pt-BR ao subir.
