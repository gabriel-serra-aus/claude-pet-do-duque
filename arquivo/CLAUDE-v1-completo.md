# Pet do Duque — Instruções do Projeto

## 1. Contexto

Loja Shopify da marca **Pet do Duque** (`https://petdoduque.com`), operando no tema **Craft**.

- **Produto principal:** sapatinhos para cachorros. somente um produto chamado "Sapatos Duque", foco em poucos SKUs bem apresentados.
- **Estado atual:** loja em modo senha ("Abertura em breve"). Vendas acontecem por WhatsApp (+55 21 99343-8017) enquanto o site está fora.
- **Mercado:** Brasil (Rio de Janeiro). Idioma **pt-BR**, moeda **BRL**, tráfego majoritariamente **mobile**.
- **Posicionamento:** acessível e prático — bom preço, variedade, entrega rápida. O argumento é resolver o problema do cliente, não sofisticação.

**Objetivo do projeto:** repaginada completa — reescrever o conteúdo existente, reorganizar as seções e modernizar o visual dentro do tema Craft. importante: deixat o site simples.

## 2. Como eu trabalho neste projeto

### Arquivos do projeto — quem manda em quê

| Arquivo | Papel |
|---|---|
| `CLAUDE.md` | Regras, tom de voz, padrões técnicos, backup. O que vale sempre. |
| `plano.md` | Só planejamento: escopo e estágios. Estágio concluído fica marcado e não se revisita. |
| `conteudo.md` | Fonte da verdade do texto e das imagens do site. |
| `images/` | Arquivos de imagem, referenciados pelo nome no `conteudo.md`. |
| `MEMORY.md` | Fatos, estado e decisões do projeto. Escrita só quando o Gabriel pede. |

Copy nunca é escrita direto no tema. Passa pelo `conteudo.md` primeiro; o tema recebe o que já foi aprovado ali. Se falta um dado, ele vira `[PENDENTE]` no `conteudo.md` — não vira texto inventado no Liquid.

### Uma página por vez

**Cada request trata de uma única página.** Nunca edito duas páginas na mesma sessão, mesmo que a mudança pareça se propagar naturalmente.

- No início do trabalho fica claro qual é a página alvo: **Home**, **Quem somos**, **Como medir** ou **Produto**.
- Se algo exigir tocar outra página — menu, seção compartilhada, snippet reusado — eu **paro, anoto como pendência e pergunto**. Não edito por conta.
- Arquivos globais (`locales/pt-BR.json`, `assets/custom.css`, `settings_data.json`) só mudam no que serve à página em foco.
- O antes/depois apresentado ao Gabriel é sempre de uma página só.

### Método e ferramentas

**Método definido: Shopify CLI com os arquivos do tema na pasta do projeto.**

O tema fica em `C:\Users\gabri\Documents\Claude Code\Code\pet-do-duque\theme`. Gabriel deixa `shopify theme dev` rodando num terminal; eu edito os arquivos direto na pasta e o CLI faz hot-reload no tema de desenvolvimento em segundos.

Comandos de referência (sempre rodados pelo Gabriel, na máquina dele):

```
shopify theme pull  --store sapatos-duque.myshopify.com     # trazer o tema para a pasta
shopify theme dev   --store sapatos-duque.myshopify.com     # loop de trabalho, hot reload
shopify theme check                            # linter de Liquid, antes de fechar
shopify theme push  --unpublished              # subir versão nova sem publicar
```

Regras de acesso, sem exceção:

- **Nunca digito senhas, credenciais, tokens ou dados de pagamento.** Gabriel autentica o CLI, Gabriel publica.
- **Nunca trabalho no tema publicado.** Toda edição vai para tema de desenvolvimento.
- **Nunca publico tema, nunca desativo a senha da loja, nunca instalo ou desinstalo app** sem "pode publicar" explícito do Gabriel.
- Antes de mudança em lote ou refactor de seção, mostro o antes/depois e espero o OK.
- **Nunca crio página, coleção, produto ou menu na loja.** Quando o trabalho depender de uma página que não existe (ex.: `/pages/como-medir`), eu **peço ao Gabriel antes** e espero ela existir para aplicar o template.
- **Nunca abro o admin da Shopify nem uso a extensão do Chrome por conta própria.** Tudo que só se resolve pelo admin vai para a fila em `ADMIN.md`. O Gabriel escolhe a hora, libera o acesso e me pede — aí eu executo a fila de uma vez.

O papel do **Chrome (Claude in Chrome) é QA visual e execução da fila do admin — sempre sob permissão explícita**: abrir o preview, tirar screenshot em viewport de celular e desktop, conferir se o que escrevi renderizou como devia, e mexer em configuração que só existe no admin. Eu **não abro o Chrome nem o admin sem o Gabriel pedir na hora**. Enquanto isso, tudo que exige admin vai anotado em `ADMIN.md` — a fila fica pronta e é executada em lote quando ele liberar. Precisa de permissão liberada na extensão para `admin.shopify.com` e `petdoduque.com`. Se der "permission denied", eu paro e aviso — não tento contornar.

**Limitações conhecidas deste método**, para não perder tempo redescobrindo:

- O CLI exige a máquina do Gabriel ligada com o terminal rodando. Eu executo na nuvem — se o notebook fecha, o loop morre e não tem trabalho assíncrono. Sessão de trabalho é sessão acompanhada.
- Não há versionamento fora da Shopify. O rollback disponível é o histórico de versões do tema. Antes de refactor grande, `shopify theme push --unpublished` para congelar um ponto de retorno.

## 3. Backup e restauração

Sem integração GitHub, o versionamento é responsabilidade nossa. Três camadas, da mais rápida de restaurar para a mais completa:

**Camada 1 — tema de backup na própria loja (rollback em segundos).**
Antes de qualquer refactor grande: `shopify theme push --unpublished --theme "Backup AAAA-MM-DD"`. Restaurar é publicar esse tema pelo admin. É a saída de emergência. Limite: a biblioteca de temas da Shopify comporta poucas dezenas de temas — limpar os antigos periodicamente.

**Camada 2 — git local na pasta do tema (histórico e diff).**
A pasta `theme` é um repositório git comum (`git init`), com commit a cada bloco de trabalho fechado. Isso dá diff real, histórico e `git checkout` para qualquer ponto — sem a integração GitHub da Shopify e, portanto, **sem** o problema do theme editor commitando de volta. Se o Gabriel criar um repositório privado, o push é manual e vira backup fora da máquina.

**Camada 3 — snapshot .zip datado.**
`shopify theme pull` seguido de zip com data, guardado na pasta do projeto. Redundância boba que já salvou muita gente.

**Restaurar um ponto anterior:**

```
git checkout <commit>                  # ou descompactar o zip
shopify theme push --unpublished       # sobe como tema novo, não publica
```

Conferir o preview antes de publicar. Publicação é sempre manual, pelo admin, e sempre com OK do Gabriel.

**Conteúdo da loja vive no banco, não no tema.** Menu, páginas, produtos, coleções e blog são criados e editados pelo Gabriel no admin — o tema só referencia. Eu não crio página nem item de menu; aponto que precisa ser criado e sigo.

**O que backup de tema NÃO cobre:** produtos, coleções, páginas, blog, navegação e clientes vivem no banco da loja, não no tema. `settings_data.json` e os `templates/*.json` guardam as configurações e o conteúdo das seções — o resto precisa de export próprio (CSV de produtos pelo admin). Antes de mexer em catálogo, exportar separadamente.

## 4. Tom de voz e identidade da marca

**Como escrever:**

Português brasileiro, coloquial e direto. Frase curta. O cliente está no celular, com pressa, decidindo em segundos — cada linha precisa carregar informação. Benefício primeiro, característica depois: "protege a patinha no asfalto quente" antes de "solado em borracha antiderrapante".

O tom é de gente de loja atendendo bem, não de marketing corporativo. Pode ser afetuoso com os pets — é o assunto — mas sem infantilizar o dono. "Sapatinhos" é o termo da casa; usar sempre esse, não "calçado pet" ou "botinha". O Duque é a referência afetiva da marca e pode aparecer em copy institucional (Sobre, rodapé), nunca em página de produto.

CTA sempre em verbo de ação e específico: "Ver tamanhos", "Comprar agora", "Falar no WhatsApp". Nunca "Saiba mais", "Clique aqui", "Confira".

Preço, frete e prazo são informação de primeira linha, não letra miúda. Prova social (foto real de cliente, avaliação, contador de vendas) entra perto do botão de compra.

**Evitar:**

- Superlativo vazio: "incrível", "revolucionário", "o melhor do mercado", "amamos o que fazemos".
- Inglês desnecessário: é "frete grátis", não "free shipping"; "novidades", não "new in".
- Emoji em excesso. 🐾 pontual em banner ou WhatsApp é ok; em descrição de produto, não.
- Parágrafo longo. Máximo 3 linhas no mobile.
- Texto de preenchimento em seção que ainda não tem conteúdo real — deixo o placeholder marcado como `[PENDENTE: ...]` em vez de inventar.

**Nunca inventar:** medidas, materiais, prazos de entrega, política de troca, avaliações de cliente ou números de venda. Se o dado não existe, marco como pendente e pergunto.

## 5. Padrões técnicos — tema Craft

Craft é um tema Online Store 2.0 da família Dawn. As consequências práticas:

- **Nativo quando empata, `custom_liquid` quando ganha.** Se a seção nativa do Craft (image banner, collage, multicolumn, rich text, featured collection, collapsible content, email signup) faz exatamente o que precisa, uso a nativa — é editável pelo theme editor e herda tema de graça. Se o `custom_liquid` entrega algo que a nativa não entrega, ou deixa o bloco mais simples de manter, uso `custom_liquid` sem cerimônia. A escolha é por resultado, não por dogma, e fica registrada no commit.
- **`custom_liquid` bem escrito.** Quando for usado: cor e tipografia via variáveis CSS do tema, nunca hex ou font-family fixos; largura em unidade relativa, nunca `min-width` em pixel; CSS reusável vai para `assets/custom.css`, não inline; e um comentário no topo dizendo o que o bloco faz e por que não é nativo.
- **Templates são JSON** (`templates/*.json`). Ordem e configuração de seções se editam pelo theme editor, não na mão.
- **Cor e tipografia vivem em Theme settings / color schemes.** Nunca hardcodar hex ou font-family dentro de uma seção — quebra a consistência e some na próxima atualização do tema.
- **CSS custom vai em arquivo próprio** (`assets/custom.css` carregado no `theme.liquid`) ou no campo Custom CSS da seção. Não editar `base.css`.
- **Mobile-first.** Toda mudança é avaliada primeiro em viewport de celular. Se quebra no mobile, não vai pro ar.
- **Imagens:** WebP, dimensionadas para o slot (nada de 4000px num card), lazy loading fora da dobra, `alt` descritivo em pt-BR em todas — é acessibilidade e SEO no mesmo movimento.
- **Performance:** cada app que injeta script custa conversão. Antes de sugerir app, checar se dá pra fazer nativo.
- **Nomenclatura:** nomes técnicos (seções, templates, handles, classes) em inglês, padrão Shopify. Conteúdo visível, sempre pt-BR.
- **Specs de produto** (tamanho, material, cor) via metafields ou variantes — não enterradas na descrição em texto corrido.
- **Traduções** em `locales/pt-BR.json`. Não substituir string de tema direto no Liquid.

**Tensão a administrar:** o Craft foi desenhado para catálogo artesanal — muito respiro, ritmo editorial, pouca densidade. O posicionamento do Pet do Duque é prático e focado em conversão. A direção é manter a base limpa do Craft e **aumentar a densidade nos pontos de decisão**: badge de preço e frete visíveis no card, prova social acima da dobra do produto, botão de compra fixo no mobile, FAQ de tamanho e troca em collapsible content. Respiro no institucional, objetividade no comercial.

## 6. Definição de pronto

Nenhuma entrega é considerada pronta sem: copy vinda do `conteudo.md` (nenhum `[PENDENTE]` no ar), `shopify theme check` limpo, preview no mobile e no desktop, todas as imagens com `alt`, nenhum texto placeholder do tema sobrando, links testados, e o antes/depois apresentado ao Gabriel. Fechada a entrega, marco o estágio no `plano.md`.

## 7. Comunicação

Respondo em **português**. Direto, sem resumir o que acabei de fazer — o resultado está à vista. Quando houver decisão de marca ou de dinheiro envolvida, aponto o trade-off em vez de escolher sozinho.
