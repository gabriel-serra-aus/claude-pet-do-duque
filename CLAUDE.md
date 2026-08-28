# Pet do Duque — Instruções do Projeto

**Este arquivo: regras que valem sempre. Pendências: `todo.md`. Execução: `etapas/`.**

## 1. Contexto

Loja Shopify **Pet do Duque** (`petdoduque.com`), handle `sapatos-duque.myshopify.com`.
Um produto: **Sapatos Duque**, sapatinhos para cachorros. R$ 109,90 · 4 cores · 8 tamanhos · 3 kits.
Mercado: Brasil (Rio). **pt-BR, BRL, tráfego majoritariamente mobile.** Posicionamento: acessível e prático.

**No ar:** Craft — "Craft - Novo site v2 2026-08-28" #165331992611, **publicado em 2026-08-28**. O v1 (#164972953635) virou não publicado e é a volta imediata se algo quebrar. Booster Premium 2.0 saiu do ar; ficou como tema não publicado, não usar.
Loja ainda em modo senha; vendas por WhatsApp +55 21 99343-8017.
**Checkout:** Yampi (checkout transparente). App personalizado legado "YAMPI - PET DO DUQUE" no admin, credenciais válidas, integração ativa no painel Yampi. O script do checkout vive no tema publicado — toda vez que o tema publicado muda, rodar "Reinstalar tema" no painel Yampi, senão o cliente cai no checkout nativo da Shopify.
Header do Craft sem busca e sem login (só carrinho) — cliente ainda loga pela URL direta `/account/login`.

**Regra do projeto: a Home educa, a página de produto vende.**

## 2. Arquivos

| Arquivo | Papel |
|---|---|
| `CLAUDE.md` | Este. Regras que valem sempre. |
| `etapas/*.md` | **Fonte da verdade da execução.** Uma etapa por sessão. |
| `todo.md` | Todas as pendências — minhas, do Gabriel e do admin. |
| `MEMORY.md` | Fatos, estado e decisões. Escrita só quando o Gabriel pede. |
| `arquivo/` | Versões superadas. Não usar. |

## 3. Uma página por vez

Cada sessão trata de **uma única página**. Se algo exigir tocar outra — menu, seção compartilhada, snippet reusado — paro, anoto como pendência e pergunto. Arquivos globais só mudam no que serve à página em foco. O antes/depois é sempre de uma página só.

## 4. Método e acesso

O tema está em `theme/`. O Gabriel roda `shopify theme dev`; eu edito os arquivos e o CLI faz hot-reload.

```
shopify theme pull  --store sapatos-duque.myshopify.com
shopify theme dev   --store sapatos-duque.myshopify.com
shopify theme check              # antes de fechar
shopify theme push --unpublished # congela um ponto de retorno
```

**Proibições — nenhuma confirmação de rotina as libera:**

- Nunca digito senha, credencial, token ou dado de pagamento. Quem autentica é o Gabriel.
- Nunca acesso o navegador. Sem admin da Shopify, sem painel do Yampi, sem extensão do Chrome, sem automação de browser.
- Nunca edito o tema publicado.
- Publicar tema, desativar a senha da loja, instalar/desinstalar app: só com **"pode publicar" explícito**, dito na hora, para aquela ação.

**Confirmação:** comando que só lê roda direto. Ação que escreve (CLI ou admin): digo o que muda e espero o "pode" — uma confirmação vale só para aquela ação. Refactor ou mudança em lote: antes/depois antes do OK.

**Admin e navegador — proibido pra mim.** Nunca abro o admin da Shopify, o painel do Yampi, nem qualquer site. Não uso extensão de navegador, Chrome, automação de browser ou ferramenta equivalente, mesmo que estejam disponíveis na sessão e mesmo que o Gabriel autorize no momento — essa regra não tem exceção de rotina. Tudo que vive no admin (menu, páginas, produtos, variantes, navegação, apps, integrações, temas) é o Gabriel quem faz. Meu papel é dizer **exatamente onde clicar e o que testar**, passo a passo, e anotar o que ficou pendente em `todo.md`. Se eu precisar ver alguma tela, peço print.

**Commits:** fora de `theme/` → prefixo `Non code files - `. Em `theme/` → sem prefixo. Bloco que mexeu nos dois: dois commits separados, nunca um misto.

## 5. Backup

Backup é felito pelo Gabriel ou somente se o Gabriel explicitamente pedir: `shopify theme push --unpublished --theme "Backup AAAA-MM-DD"` + commit do git em `theme/`.

O backup de tema **não cobre** o que vive no banco da Shopify: produtos, páginas, coleções, navegação e clientes — isso só sai por export ou cópia manual no admin. Risco pequeno e aceito: só o Gabriel mexe no admin.

## 6. Tom de voz

Português brasileiro, coloquial e direto. Frase curta — o cliente está no celular, decidindo em segundos.

- CTA em verbo de ação e específico: "Ver tamanhos", "Comprar agora", "Falar no WhatsApp". Nunca "Saiba mais", "Clique aqui", "Confira".
- Preço, frete e prazo são informação de primeira linha, não letra miúda.
- **Evitar:** superlativo vazio · inglês desnecessário · emoji em descrição de produto · parágrafo com mais de 3 linhas no mobile.
- **Nunca inventar** medida, material, prazo, política de troca, avaliação ou número de venda. Se o dado não existe, marco `[PENDENTE]` e pergunto.

## 7. Padrões técnicos — Craft (Online Store 2.0, família Dawn)

- **Nativo quando empata, `custom_liquid` quando ganha.** Escolha por resultado, registrada no commit.
- **`custom_liquid` bem escrito:** variáveis CSS do tema, nunca hex fixo · unidade relativa · CSS reusável em `assets/custom.css` · comentário no topo dizendo o que faz e por que não é nativo.
- **Templates são JSON** — ordem e configuração pelo theme editor. Cor e tipografia em Theme settings, nunca hardcodadas.
- **CSS próprio** só em `assets/custom.css`. Nunca editar `base.css`.
- **Mobile-first.** Se quebra em 390px, não vai ao ar.
- **Imagens:** WebP, dimensionadas para o slot, lazy loading fora da dobra, `alt` em pt-BR em 100% delas.
- **Texto é texto** — nunca imagem. Traduções em `locales/pt-BR.json`. Specs de produto em metafields e variantes.
- **Apps:** nenhum novo. Cada script injetado custa conversão.
- **Densidade:** base limpa como o Craft pede; densidade só nos pontos de decisão — preço e frete visíveis, prova social perto do botão, FAQ acessível.

## 8. Definição de pronto

Copy sem `[PENDENTE]` no ar · `shopify theme check` limpo · preview em 390px e 1280px · `alt` em todas as imagens · nenhum placeholder do tema sobrando · links testados · antes/depois apresentado ao Gabriel. Fechada a entrega, marco a checklist na etapa.

## 9. Comunicação

Respondo em **português**, direto, sem resumir o que acabei de fazer. Em decisão de marca ou de dinheiro, aponto o trade-off em vez de escolher sozinho.
