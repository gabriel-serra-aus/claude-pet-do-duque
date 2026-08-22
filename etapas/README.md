# Etapas de execução — repaginada Pet do Duque

Instruções para o Claude Code. **Uma etapa por sessão.**
Racional, diagnóstico e wireframes: `Especificacao-Tecnica-Pet-do-Duque.docx` — referência humana, não carregar em sessão.

| Arquivo | Depende de | Bloqueia | Status |
|---|---|---|---|
| `ETAPA-0-preparacao.md` | — | — | **concluída** 22/08 (export adiado) |
| `ETAPA-1-home-e-layout.md` | 0 | — | **concluída** 22/08 |
| `ETAPA-2-pagina-de-produto.md` | 1 | 4 | aberta |
| `ETAPA-3-quem-somos.md` | 1 | 4 | aberta |
| `ETAPA-4-testes-e-aceite.md` | 1, 2, 3 | — | aberta |

As Etapas 2 e 3 são independentes entre si — qualquer ordem.

## O que carregar em cada sessão
`CLAUDE.md` (automático, está na raiz) + **o arquivo da etapa**. Nada mais.

## Regra do projeto
**A Home educa. A página de produto vende.**
Tudo que explica, convence ou tira dúvida vive na Home. O produto guarda só o necessário para escolher e comprar.

## Marcadores
- `[PENDENTE: x]` — dado real que falta. A seção não vai ao ar sem ele.
- `[A DEFINIR]` — seção construída e `disabled`, ligada quando houver conteúdo.
- `[~]` numa checklist — adiado de propósito, com motivo em `skiped.md`.

## Onde cada coisa mora

| Arquivo | O quê |
|---|---|
| `ADMIN.md` | ação que só se resolve no admin da Shopify |
| `skiped.md` | o que a etapa previa e não foi feito, com o motivo |
| `todo.md` | trabalho que sobrou, separado por dono |
| `backups/` | o que o backup de tema não cobre (navegação, exports) |
