# Etapa 0 — Preparação

Rodar antes de qualquer edição. Bloqueia as etapas 1, 2 e 3.

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
- [ ] Export de produtos/páginas/navegação em `backups/` — **adiado por decisão do Gabriel** (22/08). Shopify não exporta página nem menu nativamente; é cópia manual. Refazer depois de decidir quais páginas ficam.
- [x] Git local commitado — `theme/` limpo
- [ ] Menu principal com 3 itens
- [x] Página `/pages/quem-somos` existe — ID `50586583145`, com conteúdo no corpo
- [ ] `shopify theme dev` rodando

## Regras
Ver `CLAUDE.md`. Em resumo: nunca editar tema publicado, nunca publicar sem OK, nunca digitar credencial, uma página por sessão.
