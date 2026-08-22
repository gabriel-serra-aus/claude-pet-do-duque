# Etapa 1 — Home e layout global

Depende da Etapa 0. Bloqueia as Etapas 2 e 3.
Arquivo alvo: `theme/templates/index.json` + configurações globais.

## Objetivo
Home vira a página de venda. Toda a educação sobre o produto vive aqui.

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

| Tamanho | Comprimento da patinha |
|---|---|
| P- | 7,0 – 7,5 cm |
| PP+ | 7,6 – 9,0 cm |
| P+ | 9,1 – 11,0 cm |
| M+ | 11,1 – 13,0 cm |
| G+ | 13,1 – 14,0 cm |
| GG+ | 14,1 – 16,0 cm |
| XG+ | 16,1 – 19,0 cm |
| XXG+ | 19,1 – 21,0 cm |

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

## Pronto quando
- [ ] 12 seções na ordem acima em `templates/index.json`
- [ ] `collage-0`, `custom_liquid_Dqpzcn`, `custom_liquid_Lpb6Vi` e `video_WRKBFz` removidas
- [ ] Zero placeholder do tema visível ("Várias colunas", "Vídeo")
- [ ] Tabela de tamanhos é texto HTML e pode ser selecionada com o cursor
- [ ] 100% das imagens com `alt` em pt-BR
- [ ] Rodapé e header em pt-BR
- [ ] Prova social e Depoimentos existem e estão `disabled`
- [ ] Preview em 390px e 1280px, sem rolagem horizontal
- [ ] `shopify theme check` sem erro
- [ ] Antes/depois apresentado ao Gabriel

## Bloqueia a publicação
frete · prazo · política de troca · instruções de lavagem · confirmação dos 3 passos de medida
