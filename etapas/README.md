# Etapas de execução — repaginada Pet do Duque

Instruções para o Claude Code. **Uma etapa por sessão.**
Racional, diagnóstico e wireframes: `Especificacao-Tecnica-Pet-do-Duque.docx` — referência humana, não carregar em sessão.

| Arquivo | Depende de | Bloqueia |
|---|---|---|
| `ETAPA-0-preparacao.md` | — | 1, 2, 3 |
| `ETAPA-1-home-e-layout.md` | 0 | 2, 3 |
| `ETAPA-2-pagina-de-produto.md` | 1 | 4 |
| `ETAPA-3-quem-somos.md` | 1 | 4 |
| `ETAPA-4-testes-e-aceite.md` | 1, 2, 3 | — |

As Etapas 2 e 3 são independentes entre si — qualquer ordem.

## O que carregar em cada sessão
`CLAUDE.md` (automático, está na raiz) + **o arquivo da etapa**. Nada mais.

## Regra do projeto
**A Home educa. A página de produto vende.**
Tudo que explica, convence ou tira dúvida vive na Home. O produto guarda só o necessário para escolher e comprar.

## Marcadores
- `[PENDENTE: x]` — dado real que falta. A seção não vai ao ar sem ele.
- `[A DEFINIR]` — seção construída e `disabled`, ligada quando houver conteúdo.

Ação que só o Gabriel faz no admin não entra aqui — vai para `ADMIN.md`.
