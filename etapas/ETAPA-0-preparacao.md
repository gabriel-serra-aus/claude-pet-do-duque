# Etapa 0 — Preparação

**CONCLUÍDA em 22/08/2026**, com um item adiado por decisão do Gabriel
(export de conteúdo — ver `skiped.md`). Não bloqueia mais as etapas 1, 2 e 3.

## Contexto
- Loja: `sapatos-duque.myshopify.com`
- Tema alvo: Craft **#164972953635** (unpublished)
- Tema no ar: Booster Premium 2.0 — não tocar
- Pasta do tema: `theme/`

## Tarefas

1. Confirmar que o git local em `theme/` está limpo. Se não, commitar antes de seguir.
2. **Gabriel roda**, na máquina dele:
   ```
   shopify theme push --unpublished --theme "Backup 2026-08-22"
   shopify theme dev --store sapatos-duque.myshopify.com
   ```
3. **Gabriel exporta pelo admin** (o CLI não faz): produtos CSV, páginas, navegação. Guardar em `backups/`.
4. Confirmar no admin que o menu principal tem exatamente 3 itens:
   `Início` · `Sapatos Duque` · `Quem somos`
   Rastreio **sai** do menu principal.
5. Confirmar no admin que existe a página `/pages/quem-somos`.

## Pronto quando
- [x] Tema de backup `Backup 2026-08-22` existe na loja, unpublished — #165276221475
- [~] Export de produtos/páginas/navegação — **adiado por decisão do Gabriel** (22/08), rastreado em `skiped.md`. A Shopify não exporta página, coleção nem menu nativamente: é cópia manual. A navegação já ficou salva em `backups/navegacao-2026-08-22.md`.
- [x] Git local commitado — `theme/` limpo
- [x] Menu principal com 3 itens — `Início` · `Sapatos Duque` · `Quem somos`, verificado no servidor de dev. Rastreio saiu
- [x] Página `/pages/quem-somos` existe — ID `50586583145`, com conteúdo no corpo
- [x] `shopify theme dev` rodando — usado o tempo todo na Etapa 1 para verificar renderização

## Regras
Ver `CLAUDE.md`. Em resumo: nunca editar tema publicado, nunca publicar sem OK, nunca digitar credencial, uma página por sessão.
