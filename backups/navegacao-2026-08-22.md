# Navegação — estado em 2026-08-22

Capturado do servidor de dev (`shopify theme dev`) antes da reorganização da Etapa 1.
Menu não vive no tema: não está em `theme/` nem no tema `Backup 2026-08-22` (#165276221475).
Este arquivo é a única cópia do estado anterior.

## Menu principal (`main-menu`)

| # | Rótulo (como digitado) | Destino |
|---|---|---|
| 1 | `INÍCIO` | `/` |
| 2 | `QUEM SOMOS?` | `/pages/quem-somos` |
| 3 | `PRODUTOS` | `/collections/all` |
| 4 | `RASTREIO` | `/pages/rastreamento-1` |

## Estado alvo da Etapa 1

| # | Rótulo | Destino |
|---|---|---|
| 1 | `Início` | `/` |
| 2 | `Sapatos Duque` | `/products/sapatos-duque-c2-original` |
| 3 | `Quem somos` | `/pages/quem-somos` |

`RASTREIO` sai do menu principal e vira link de rodapé. A página `/pages/rastreamento-1`
continua existindo — só deixa de ser item de menu.

## Páginas conhecidas até agora

- `/pages/quem-somos` — ID 50586583145, visível, com conteúdo no corpo
- `/pages/rastreamento-1` — existe, conteúdo não inspecionado

Levantamento completo de páginas ainda não foi feito (export adiado por decisão do Gabriel).
