# Pet do Duque — Instruções do Projeto

## 1. Contexto

Loja Shopify **Pet do Duque** (`petdoduque.com`), handle `sapatos-duque.myshopify.com`.
Um produto: **Sapatos Duque**, sapatinhos para cachorros. R$ 109,90 · 4 cores · 8 tamanhos · 3 kits.
Mercado: Brasil (Rio). **pt-BR, BRL, tráfego majoritariamente mobile.**
Posicionamento: acessível e prático — preço, variedade, entrega rápida. Resolver o problema do cliente, não sofisticação.

**Tema alvo:** Craft #164972953635 (unpublished). **No ar:** Booster Premium 2.0 — não tocar.
Loja em modo senha; vendas por WhatsApp +55 21 99343-8017.

**Regra do projeto: a Home educa, a página de produto vende.**

## 2. Arquivos

| Arquivo | Papel |
|---|---|
| `CLAUDE.md` | Este. Regras que valem sempre. |
| `etapas/*.md` | **Fonte da verdade da execução.** Uma etapa por sessão. |
| `ADMIN.md` | Fila de ações que só o Gabriel faz no admin. |
| `MEMORY.md` | Fatos, estado e decisões. Escrita só quando o Gabriel pede. |
| `Especificacao-Tecnica-*.docx` | Racional, diagnóstico e wireframes. Referência humana — não carregar em sessão. |
| `arquivo/` | Versões superadas. Não usar. |

## 3. Uma página por vez

Cada sessão trata de **uma única página**. Se algo exigir tocar outra — menu, seção compartilhada, snippet reusado — eu **paro, anoto como pendência e pergunto**. Arquivos globais (`locales/pt-BR.json`, `assets/custom.css`, `settings_data.json`) só mudam no que serve à página em foco. O antes/depois é sempre de uma página só.

## 4. Método e acesso

O tema está em `theme/`. O Gabriel roda `shopify theme dev` na máquina dele; eu edito os arquivos e o CLI faz hot-reload no tema de desenvolvimento.

```
shopify theme pull  --store sapatos-duque.myshopify.com
shopify theme dev   --store sapatos-duque.myshopify.com
shopify theme check                            # antes de fechar
shopify theme push  --unpublished              # congela um ponto de retorno
```

Sem exceção:

- **Nunca digito senha, credencial, token ou dado de pagamento.** Quem autentica é o Gabriel. Sessão de CLI já autenticada eu uso; login novo é sempre ele.
- **Nunca edito o tema publicado.** Toda edição vai para tema de desenvolvimento.
- **Nunca publico tema, nunca desativo a senha da loja, nunca instalo ou desinstalo app** sem "pode publicar" explícito.
- Antes de mudança em lote ou refactor de seção, mostro o antes/depois e espero o OK.

**Admin e CLI — posso, mas confirmo antes.** Eu abro o admin da Shopify e rodo comando da CLI quando o trabalho pede. **Pergunto antes de cada ação que escreve** e espero o "pode": digo qual comando, em que tema e o que ele altera. Sem resposta, não rodo. Uma confirmação vale para a ação combinada, não para as seguintes.

Comando que **só lê** — `shopify theme check`, `theme list`, `theme info`, `--help`, `git status`, `git log`, ler arquivo — roda direto, sem perguntar.

As proibições acima continuam de pé e **nenhuma confirmação de rotina as libera**: publicar tema, desativar a senha da loja, instalar ou desinstalar app exigem "pode publicar" explícito, dito na hora, para aquela ação.

**Conteúdo da loja vive no banco, não no tema.** Menu, páginas, produtos, coleções e navegação vivem no admin, não em `theme/`. Eu **não crio nem edito** esse conteúdo por conta: aponto, a pendência vai para `ADMIN.md` e o Gabriel decide. Se ele me pedir e confirmar, eu executo.

**Backup:** antes de refactor grande, `shopify theme push --unpublished --theme "Backup AAAA-MM-DD"`. Git local em `theme/` com commit a cada bloco fechado. Backup de tema **não** cobre produtos, páginas, navegação e clientes — isso precisa de export pelo admin.

**Commits.** Commit que **não** toca o site — `CLAUDE.md`, `ADMIN.md`, `etapas/`, `backups/`, `arquivo/`, documento de referência — leva o prefixo `Non code files - `. Commit que toca `theme/` não leva prefixo nenhum. Se um bloco de trabalho mexeu nos dois, são **dois commits separados** — nunca um misto.

## 5. Tom de voz

Português brasileiro, coloquial e direto. Frase curta. O cliente está no celular, com pressa, decidindo em segundos.

**Benefício antes de característica:** "protege a patinha no asfalto quente" antes de "solado em borracha antiderrapante".

Tom de gente de loja atendendo bem, não de marketing corporativo. Afetuoso com os pets, sem infantilizar o dono. **"Sapatinhos" é o termo da casa** — nunca "calçado pet" ou "botinha". O Duque aparece em copy institucional, nunca em página de produto.

CTA em verbo de ação e específico: "Ver tamanhos", "Comprar agora", "Falar no WhatsApp". Nunca "Saiba mais", "Clique aqui", "Confira".

Preço, frete e prazo são informação de primeira linha, não letra miúda.

**Evitar:** superlativo vazio ("incrível", "o melhor do mercado") · inglês desnecessário (é "frete grátis", não "free shipping") · emoji em descrição de produto · parágrafo com mais de 3 linhas no mobile.

**Nunca inventar** medida, material, prazo, política de troca, avaliação ou número de venda. Se o dado não existe, marco `[PENDENTE]` e pergunto.

## 6. Padrões técnicos — Craft (Online Store 2.0, família Dawn)

- **Nativo quando empata, `custom_liquid` quando ganha.** Se a seção nativa faz exatamente o que precisa, uso a nativa — é editável pelo theme editor e herda tema de graça. Se o `custom_liquid` entrega algo que a nativa não entrega, ou simplifica a manutenção, uso sem cerimônia. Escolha por resultado, registrada no commit.
- **`custom_liquid` bem escrito:** variáveis CSS do tema, nunca hex ou font-family fixos · unidade relativa, nunca `min-width` em pixel · CSS reusável em `assets/custom.css` · comentário no topo dizendo o que faz e por que não é nativo.
- **Templates são JSON.** Ordem e configuração de seções pelo theme editor, não na mão.
- **Cor e tipografia** em Theme settings / color schemes. Nunca hardcodar dentro de uma seção.
- **CSS próprio** só em `assets/custom.css`. Nunca editar `base.css`.
- **Mobile-first.** Se quebra em 390px, não vai ao ar.
- **Imagens:** WebP, dimensionadas para o slot, lazy loading fora da dobra, `alt` descritivo em pt-BR em 100% delas.
- **Texto é texto.** Nada que precise ser lido, buscado ou traduzido entra como imagem.
- **Traduções** em `locales/pt-BR.json`. Não substituir string de tema direto no Liquid.
- **Specs de produto** em metafields e variantes, nunca em texto corrido.
- **Apps:** nenhum novo. Cada script injetado custa conversão.

**Densidade:** o Craft foi feito para catálogo artesanal — muito respiro, pouca densidade. Manter a base limpa e aumentar a densidade só nos pontos de decisão: preço e frete visíveis, prova social perto do botão, FAQ acessível. Respiro no institucional, objetividade no comercial.

## 7. Definição de pronto

Nenhuma entrega é pronta sem: copy sem `[PENDENTE]` no ar · `shopify theme check` limpo · preview em 390px e 1280px · `alt` em todas as imagens · nenhum placeholder do tema sobrando · links testados · antes/depois apresentado ao Gabriel. Fechada a entrega, marco a checklist no arquivo da etapa.

## 8. Comunicação

Respondo em **português**. Direto, sem resumir o que acabei de fazer — o resultado está à vista. Em decisão de marca ou de dinheiro, aponto o trade-off em vez de escolher sozinho.
