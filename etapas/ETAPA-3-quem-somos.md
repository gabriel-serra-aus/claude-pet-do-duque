# Etapa 3 — Quem somos

Depende da Etapa 1 (layout global). Independente da Etapa 2.
Arquivo alvo: `theme/templates/page.quem-somos.json` (novo).
Pré-requisito: a página `/pages/quem-somos` já existe no admin (Etapa 0).

## Objetivo
Enquadrar a história que já existe. **Não reescrever o texto.**

---

## 1. Seções

```
1  rich-text                      Título + história
2  collage ou image-with-text     Foto do Duque + foto do Zico
3  image-banner                   Chamada final
```

## 2. Conteúdo

### rich-text
```
Título:    Quem somos
Subtítulo: A história por trás dos Sapatos Duque
```

Usar o texto que já está no site. **Único ajuste: quebrar parágrafos.**
Nenhum bloco pode passar de 3 linhas em viewport de 390px.

Referência do conteúdo existente: Duque, labrador chocolate, displasia aos 4 meses em 2002 → os tapetes pela casa → a reclamação do marido → a busca frustrada por sapatinho para cão com problema articular → o primeiro protótipo costurado à mão → o Zico, labrador amarelo com artrose no cotovelo.

### Fotos
| Arquivo | Alt |
|---|---|
| Duque | `Duque, labrador chocolate deitado na grama` |
| Zico | `Zico, labrador amarelo deitado na grama` |

⚠️ **As duas fotos têm marca d'água de banco de imagem no canto.**
`[PENDENTE: Gabriel confirma se são próprias e substitui pela versão sem marca, ou troca por foto original.]`
**Não publicar com marca d'água.**

### image-banner — chamada final
```
Título:  Feito por quem viveu o problema.
Botão 1: Comprar agora      → produto
Botão 2: Falar no WhatsApp  → https://wa.me/5521993438017
```

---

## 3. Ligação com a home
Confirmar que a chamada final da home (Etapa 1, seção 11) aponta para `/pages/quem-somos`.
A história inteira fica aqui; a home leva só o gancho.

---

## Pronto quando
- [ ] `templates/page.quem-somos.json` existe e a página renderiza
- [ ] Nenhum parágrafo passa de 3 linhas em 390px
- [ ] As 2 fotos com `alt` em pt-BR
- [ ] Questão da marca d'água resolvida
- [ ] Chamada final com os 2 botões, ambos funcionando
- [ ] A home tem caminho visível para esta página
- [ ] Preview em 390px e 1280px
- [ ] `shopify theme check` sem erro
- [ ] Antes/depois apresentado ao Gabriel

## Bloqueia a publicação
crédito/marca d'água das fotos
