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

- 22/08/2026 — **Etapas 0 e 1 concluídas.** Home reescrita no Craft #164972953635, ainda unpublished. Booster Premium 2.0 continua no ar.
- 22/08/2026 — Loja **ainda em modo senha** ("Estamos passando por uma manutenção no site"), vendas por WhatsApp. Confirmado buscando `petdoduque.com`.
- 22/08/2026 — **Sem ferramenta de navegador na sessão.** O Gabriel autorizou o acesso ao admin, mas autorização não instala ferramenta: não há MCP de browser configurado. Enquanto isso, ação de admin fica em `ADMIN.md` e é ele quem executa. A CLI, essa sim, roda por Bash e já está autenticada.
- 22/08/2026 — Loja tem **1.979 pedidos**. Não é loja nova: pode haver avaliação real acumulada no Loox, o que destravaria as seções de prova social.

## Dados da loja verificados (22/08, pelo servidor de dev)

- **Produto:** `sapatos-duque-c2-original` — "Sapatos Duque", R$ 109,90 a R$ 344,90, 96 variantes (92 em estoque), 19 imagens.
- **Opções:** 4 cores (Preto, Branco, Roxo, Vermelho) · 8 tamanhos · 3 kits (One 4 patas, Double Duque 8, Duque Economy 16).
- **Tamanhos, nomes reais:** `0=` `PP=` `P=` `M=` `G=` `GG=` `XG=` `XXG=`. O `=` é ruído a renomear; se mudar, a tabela da home muda junto.
- **Páginas conhecidas:** `/pages/quem-somos` (ID 50586583145, com a história do Duque no corpo) e `/pages/rastreamento-1`.
- **Menu principal:** `Início` · `Sapatos Duque` · `Quem somos`.

## Backups

- 16/08/2026 — **Full backup de tema feito.** Camada 1: tema `Backup 2026-08-16 (Craft base)` #165221826595, unpublished na loja. Camada 2: git local + GitHub `gabriel-serra-aus/claude-pet-do-duque` (branches `main` = Craft, `booster-live` = Booster). Camada 3: zips em `backups/craft-2026-08-16.zip` e `backups/booster-live-2026-08-16.zip`.
- 22/08/2026 — Segundo tema de backup: `Backup 2026-08-22` **#165276221475**, unpublished. É retrato da pasta local, não do tema remoto.
- **Adiado por decisão do Gabriel (22/08):** export de conteúdo da loja. Ver `skiped.md`. Descoberta relevante: a Shopify **não** exporta página, coleção, blog nem menu nativamente — só produto, cliente, pedido, desconto e estoque. O resto é cópia manual.
- **Risco aceito:** o corpo da página `quem-somos` existe só no banco da Shopify. Não está em `theme/`, nem no git, nem em nenhum tema de backup.

## Decisões

- 16/08/2026 — Escopo acordado: repaginada completa (conteúdo + layout + visual) dentro do tema Craft.
- 16/08/2026 — **Base de trabalho = Craft #164972953635** (criado recentemente pelo Gabriel, unpublished). O Booster Premium fica no ar até o Craft ficar pronto; então o Gabriel publica o Craft. Snapshot do Booster guardado no branch git `booster-live`.
- 16/08/2026 — Contadores falsos do Booster (`product_count_random`, timers de escassez): **manter por enquanto**, revisitar depois. Não vão para o Craft.
- 16/08/2026 — **Método de trabalho definido: Shopify CLI.** Tema em `C:\Users\gabri\Documents\Claude Code\Code\pet-do-duque\theme` (pull do live feito, git local iniciado, commit `01303cf`); Gabriel roda `shopify theme dev` e Claude edita os arquivos na pasta. Chrome fica só para QA visual.
- 16/08/2026 — Integração GitHub da Shopify **descartada** por ora: sem hot reload e com conflito de escrita (theme editor commita de volta em `settings_data.json` e `templates/*.json`), o que pesa muito num projeto com edição intensa de conteúdo. Custo aceito: sem trabalho assíncrono, exige a máquina do Gabriel ligada.
- 16/08/2026 — Backup em três camadas: tema `Backup AAAA-MM-DD` unpublished na loja, git local na pasta do tema, e snapshot .zip datado. Publicação sempre manual.

- 22/08/2026 — **Convenção de commit:** commit que não toca `theme/` leva o prefixo `Non code files - `. Commit de tema não leva prefixo. Se um bloco mexeu nos dois, são dois commits.
- 22/08/2026 — **Acesso ampliado:** o Claude pode abrir o admin e rodar comando da CLI, perguntando antes de cada ação que escreve. Comando somente-leitura roda direto. Publicar tema, desativar a senha da loja e instalar app continuam exigindo "pode publicar" na hora.
- 22/08/2026 — **Vermelho da marca `#B3342B`**, provisório, só no botão primário do esquema claro. 6,10:1 com label branco. No esquema escuro o botão segue claro, por contraste.
- 22/08/2026 — **`page_width` 1200** (era 1000, o mínimo do schema; 1200 é o padrão do Craft).
