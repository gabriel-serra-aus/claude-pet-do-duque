# MEMORY — Pet do Duque

- **CLI:** usar o handle `sapatos-duque.myshopify.com` — `petdoduque.com` é só vitrine e faz o CLI falhar.
- **Estado (22/08/2026):** Etapas 0 e 1 concluídas no Craft (unpublished). Booster no ar, loja em modo senha.
- **Sem MCP de navegador na sessão:** admin é o Gabriel quem executa. A CLI roda por Bash, já autenticada.
- **Produto:** handle `sapatos-duque-c2-original`, 96 variantes. Cores: Preto, Branco, Roxo, Vermelho · kits: One 4 patas, Double Duque 8, Duque Economy 16 · tamanhos reais: `0=` `PP=` `P=` `M=` `G=` `GG=` `XG=` `XXG=`.
- **Rótulos de tamanho são dependência frágil:** o tema casa com eles em 3 lugares — tabela da home (`index.json`), tabela do produto (`product.json`) e mapa de faixas em cm (`product-variant-options.liquid`). Renomeou no admin, muda tudo junto.
- **Páginas:** `/pages/quem-somos` (ID `50586583145`) e `/pages/rastreamento-1`. O corpo de `quem-somos` — a história do Duque — existe **só** no banco da Shopify: sem export, não há de onde restaurar.
- **Backups:** 3 camadas — tema unpublished (`Backup 2026-08-22` #165276221475), git + GitHub `gabriel-serra-aus/claude-pet-do-duque` (`main` = Craft, `booster-live` = Booster), zips em `backups/`.
- **Integração GitHub da Shopify descartada:** sem hot reload e conflita com o theme editor.
- **Contadores falsos do Booster** (escassez, `product_count_random`): não vão para o Craft.
- **Vermelho da marca `#B3342B`**, provisório, só no botão primário do esquema claro.
