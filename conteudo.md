# Conteúdo — Pet do Duque

Fonte da verdade do **texto e das imagens** que vão para o site. O `plano.md` diz *quando* fazer; este arquivo diz *o que* escrever.

Regra: nada aqui é inventado. O que não existe fica marcado `[PENDENTE]` e o campo continua vazio até o Gabriel preencher.

Convenção de imagem: arquivos ficam em `images/`, referenciados pelo nome. Ver `images/README.md`.

Última atualização: 22/08/2026

---

## Marca

| Campo | Valor |
|---|---|
| Nome | Pet do Duque |
| Produto | Sapatos Duque — sapatinhos para cachorros |
| Site | `https://petdoduque.com` |
| WhatsApp | +55 21 99343-8017 |
| Instagram | `[PENDENTE: handle]` |
| Atendimento | Seg. a Sáb., 9h às 18h |
| Envio | Todo o Brasil, imediato após confirmação do pagamento |
| Pagamento | Mercado Pago (bastidor — não citar na copy) |

---

## Produto — Sapatos Duque

| Campo | Valor |
|---|---|
| Nome | Sapatos Duque |
| Preço | `[PENDENTE]` |
| Parcelamento | `[PENDENTE]` |
| Cores | `[PENDENTE: lista]` |
| Tamanhos | `[PENDENTE: lista]` |
| Material | `[PENDENTE]` |
| Solado | Borracha antiderrapante `[CONFIRMAR]` |
| Lavagem | `[PENDENTE]` |
| Frete | `[PENDENTE: valor, frete grátis a partir de X?]` |
| Prazo de entrega | `[PENDENTE]` |
| Troca / devolução | `[PENDENTE]` |

### Tabela de tamanhos

`[PENDENTE: medida da patinha em cm × tamanho. Não inventar.]`

| Tamanho | Comprimento da patinha (cm) | Largura (cm) |
|---|---|---|
| — | — | — |

### Benefícios (ordem de uso na copy — benefício primeiro, característica depois)

1. Protege a patinha do asfalto quente
2. Solado antiderrapante — segurança em piso liso
3. Apoio para cão com displasia ou lesão

> Texto de referência já existente no tema (reescrever, não copiar): argumento de solado antiderrapante + displasia.

---

## Página: Home (`/`)

### 1. Barra de anúncio
```
[PENDENTE: mensagem. Ex.: frete grátis acima de R$ X · entrega em Y dias]
```

### 2. Banner principal — `image-banner`
**Imagem:** `images/home-hero.webp` (atual na loja: `hero2_duque_v1.webp`)
**Alt:** `[PENDENTE: descrição em pt-BR]`

```
Título:     Mais segurança para o seu cão
Subtítulo:  Proteção, conforto e estabilidade em todos os passos.
CTA 1:      Comprar agora        → /products/sapatos-duque
CTA 2:      Ver tamanhos         → /pages/como-medir
```

### 3. Prova social
`[PENDENTE: temos avaliações reais? número de clientes atendidos? Sem dado real, esta seção não entra.]`

### 4. Coleção em destaque — `featured-collection`
```
Título: Sapatos Duque
```
Preço visível no card. Sem descrição de seção.

### 5. Por que comprar — `multicolumn`
Reescrita do bloco atual (tirar CAIXA ALTA, tirar menção a gateway, tirar título placeholder "Várias colunas"):

```
Título da seção: (vazio, ou) Por que comprar

Coluna 1 — Entregamos em todo o Brasil
  Envio imediato após a confirmação do pagamento.
  Imagem: images/icone-entrega.webp

Coluna 2 — Compra segura
  Pagamento protegido e confirmação na hora.
  Imagem: images/icone-seguro.webp

Coluna 3 — Suporte de verdade
  Atendimento de segunda a sábado, das 9h às 18h.
  Imagem: images/icone-suporte.webp
```

### 6. Guia de tamanho — chamada curta — `image-with-text`
**Imagem:** `images/home-medida.webp`
```
Título: Não sabe o tamanho?
Texto:  Uma fita métrica e trinta segundos resolvem. A gente te mostra como.
CTA:    Ver como medir → /pages/como-medir
```

### 7. Foto real de cliente / UGC
**Imagens:** `images/ugc-01.webp`, `images/ugc-02.webp`, `images/ugc-03.webp`
`[PENDENTE: temos fotos de clientes com autorização de uso?]`

### 8. FAQ — `collapsible-content`
Ver bloco **FAQ mestre** no fim deste arquivo.

### 9. Rodapé
```
WhatsApp: +55 21 99343-8017
Links: Trocas e devoluções · Política de privacidade · Instagram
```

---

## Página: Quem somos (`/pages/quem-somos`)

Um scroll no mobile. É a única página onde o Duque aparece.

**Imagem:** `images/duque.webp` — foto do Duque
**Alt:** `[PENDENTE]`

```
Título: [PENDENTE]

História: [PENDENTE — Gabriel escreve ou conta a história do Duque e do
começo da loja. Não invento.]

CTA final: Falar no WhatsApp → https://wa.me/5521993438017
```

---

## Página: Como medir (`/pages/como-medir`)

Operacional, não decorativa. Resolve a objeção nº 1.

### Passo a passo
```
Título: Como medir a patinha do seu cão

1. Coloque a patinha do cão sobre uma folha de papel, com o peso apoiado.
2. Marque o ponto mais atrás e o ponto mais à frente da patinha.
3. Meça a distância entre as marcas com uma régua. Esse é o comprimento.

[CONFIRMAR os 3 passos com o Gabriel antes de publicar.]
```

### Vídeo
YouTube `YjO_qQHzQL4` — "Como medir o tamanho dos sapatinhos"
Hoje enterrado num bloco de Liquid custom na home.

### Tabela de tamanhos
Ver seção **Produto** acima. `[PENDENTE]`
Formato: HTML em `rich-text` — não imagem (ilegível no mobile e inacessível).

### Dúvidas de medida — `collapsible-content`
```
Ficou entre dois tamanhos?
  [PENDENTE: qual a orientação — arredondar pra cima?]

E se eu errar o tamanho?
  [PENDENTE: política de troca]

Meço as quatro patas?
  [PENDENTE]
```

### CTA final
```
Comprar agora → /products/sapatos-duque
Falar no WhatsApp → https://wa.me/5521993438017
```

---

## Página: Produto — Sapatos Duque

### Ordem dos blocos e copy

```
1. Título          Sapatos Duque
2. Preço           [PENDENTE] + parcelamento
3. Prova social    [PENDENTE: dado real]
4. Variantes       Tamanho · Cor
5. Link            Não sei o tamanho — como medir  → /pages/como-medir
6. Aviso (pequeno) Cor sujeita a estoque. Se a cor escolhida estiver em
                   falta, enviamos outra opção e avisamos antes.
7. Quantidade
8. Botões de compra
9. Frete e prazo   [PENDENTE] — primeira linha, não letra miúda
10. Descrição
```

### Descrição do produto (benefício primeiro)
```
Asfalto quente queima a patinha. Piso liso derruba. Sapatos Duque resolve
os dois: solado antiderrapante e proteção térmica em todos os passos.

Para cão com displasia ou lesão, o apoio extra faz diferença na caminhada.

[CONFIRMAR: material, altura do cano, se é impermeável.]
```

Specs (tamanho, material, cor) vão em **metafields/variantes** — não em texto corrido.

### Abaixo do produto
- **Como calçar** — vídeo YouTube `DgTqO9V_l_I`
- **FAQ** — ver bloco mestre abaixo

### O que sai
- Bloco de aviso acima do preço → desce para o item 6
- `disclosures` (seletor de país/idioma) — loja só do Brasil
- `related-products` "You may also like" — loja de um produto

---

## FAQ mestre

Fonte única. Home e Produto reusam daqui.

```
Qual o prazo de entrega?
  [PENDENTE]

Quanto custa o frete?
  [PENDENTE — tem frete grátis? a partir de quanto?]

Como sei o tamanho certo?
  Meça o comprimento da patinha e compare com a tabela.
  Passo a passo em /pages/como-medir.

E se o tamanho não servir?
  [PENDENTE: política de troca]

Como lavo os sapatinhos?
  [PENDENTE]

Meu cão vai se acostumar?
  [PENDENTE: orientação de adaptação]
```

---

## Vídeos disponíveis

| Vídeo | ID YouTube | Destino |
|---|---|---|
| Como medir o tamanho dos sapatinhos | `YjO_qQHzQL4` | Página Como medir |
| Como calçar os Sapatos Duque | `DgTqO9V_l_I` | Página de produto |
| Recomendado por especialistas | `XTAnYxuBwWg` | `[PENDENTE: mantemos? onde?]` |

---

## Pendências de conteúdo

Trava a entrega. Não invento nenhum destes:

- [ ] Preço, parcelamento e lista de cores/tamanhos
- [ ] Tabela de tamanhos oficial (cm → tamanho)
- [ ] Frete: valor, frete grátis a partir de quanto
- [ ] Prazo de entrega
- [ ] Política de troca e devolução
- [ ] Avaliações reais ou número de clientes atendidos
- [ ] Fotos de clientes (UGC) com autorização
- [ ] História do Duque / da marca
- [ ] Material e instruções de lavagem
- [ ] Mensagem da barra de anúncio
- [ ] Handle do Instagram
- [ ] Foto do Duque para a página Quem somos
