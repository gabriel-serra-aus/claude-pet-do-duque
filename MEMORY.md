# MEMORY — Pet do Duque

## Fatos do projeto

- **Loja:** Pet do Duque — `https://petdoduque.com` (Shopify)
- **Handle da loja (para o CLI):** `sapatos-duque.myshopify.com` — admin em `admin.shopify.com/store/sapatos-duque`. `petdoduque.com` é só vitrine e faz o CLI falhar.
- **Tema live:** **Booster Premium 2.0** (vintage, Online Store 1.0 — templates `.liquid`, `content_for_index`, jQuery, Loox + Yampi). O **Craft existe na loja mas está unpublished** (#164972953635). O CLAUDE.md descrevia Craft por engano.
- **Produto principal:** sapatinhos para pets
- **WhatsApp de vendas:** +55 21 99343-8017
- **Mercado:** Brasil / Rio de Janeiro — pt-BR, BRL, tráfego mobile
- **Posicionamento definido:** acessível e prático (preço, variedade, entrega rápida)

## Estado

- 16/08/2026 — Loja em modo senha ("Abertura em breve"), vendas rodando por WhatsApp.
- 16/08/2026 — Extensão do Chrome ainda **sem permissão** para `admin.shopify.com`. Precisa ser liberada antes de qualquer edição.

## Backups

- 16/08/2026 — **Full backup de tema feito.** Camada 1: tema `Backup 2026-08-16 (Craft base)` #165221826595, unpublished na loja. Camada 2: git local + GitHub `gabriel-serra-aus/claude-pet-do-duque` (branches `main` = Craft, `booster-live` = Booster). Camada 3: zips em `backups/craft-2026-08-16.zip` e `backups/booster-live-2026-08-16.zip`.
- **Pendente:** export de conteúdo da loja (produtos, coleções, páginas, navegação) — só pelo admin, Claude não consegue pelo CLI.

## Decisões

- 16/08/2026 — Escopo acordado: repaginada completa (conteúdo + layout + visual) dentro do tema Craft.
- 16/08/2026 — **Base de trabalho = Craft #164972953635** (criado recentemente pelo Gabriel, unpublished). O Booster Premium fica no ar até o Craft ficar pronto; então o Gabriel publica o Craft. Snapshot do Booster guardado no branch git `booster-live`.
- 16/08/2026 — Contadores falsos do Booster (`product_count_random`, timers de escassez): **manter por enquanto**, revisitar depois. Não vão para o Craft.
- 16/08/2026 — **Método de trabalho definido: Shopify CLI.** Tema em `C:\Users\gabri\Documents\Claude Code\Code\pet-do-duque\theme` (pull do live feito, git local iniciado, commit `01303cf`); Gabriel roda `shopify theme dev` e Claude edita os arquivos na pasta. Chrome fica só para QA visual.
- 16/08/2026 — Integração GitHub da Shopify **descartada** por ora: sem hot reload e com conflito de escrita (theme editor commita de volta em `settings_data.json` e `templates/*.json`), o que pesa muito num projeto com edição intensa de conteúdo. Custo aceito: sem trabalho assíncrono, exige a máquina do Gabriel ligada.
- 16/08/2026 — Backup em três camadas: tema `Backup AAAA-MM-DD` unpublished na loja, git local na pasta do tema, e snapshot .zip datado. Publicação sempre manual.
