# todo.md — pendências de trabalho

Trabalho que ainda tem que ser feito, com dono claro.

- Ação que só se resolve no admin da Shopify → `ADMIN.md`
- Coisa que a etapa previa e foi pulada, com o motivo → `skiped.md`
- Aqui: o que sobrou de trabalho, meu ou do Gabriel

Status: `[ ]` aberto · `[x]` feito (com data)

---

## Para o Gabriel revisar

### Ícones dos benefícios — revisar o desenho

- [ ] **Olhar os 3 ícones na home** e dizer se servem.

Desenhei em SVG: patinha firme sobre piso liso, sol forte acima da patinha, e
articulação amparada por apoio dos dois lados. Grade de 48px, traço de 2px, sem
cor fixa — quem manda na cor é o esquema do tema, então eles acompanham o
vermelho da marca.

Os arquivos soltos estão em `images/`, se quiser abrir fora do site.

**Três saídas, se não gostar:**

| Saída | Consequência |
|---|---|
| Ajusto o desenho | rápido, continua sem depender de upload |
| Você manda 3 ícones seus | subir em Files, aí eu aponto |
| Foto real no lugar de ícone | mais convincente que ícone, mas precisa de 3 fotos boas |

### Voltar a seção de benefícios para o nativo

- [ ] **Decidir** se quer editar o texto das 3 colunas pelo theme editor.

Hoje o texto vive no snippet `pdd-beneficios.liquid`, não no editor visual.
Foi a troca para ter ícone sem depender de upload.

Para voltar ao nativo: subir os 3 SVG de `images/` em Files, trocar a seção de
volta para `multicolumn` e apontar as imagens. Aí o texto volta a ser editável
por você, sem me chamar.

### Card do produto em destaque ocupando a largura toda

- [ ] **Decidir na Etapa 2** se o card gigante fica.

A seção está com uma coluna no desktop, então o card de um produto só ocupa a
largura inteira — e com `page_width` em 1200 ficou ainda maior. Card enorme de
produto único costuma parecer página inacabada.

Não mexi porque isso conversa com a página de produto, e a regra é uma página
por vez. Alternativas: duas ou três colunas (com um produto fica esquisito de
outro jeito), ou trocar por uma seção que mostre o produto com mais informação
ao lado da foto.

### Chamada final — imagem

- [ ] **Escolher uma foto** para a chamada final da home, se quiser.

Hoje é bloco de texto em fundo escuro, sem imagem. Funciona. Com uma foto boa
vira `image-banner` e ganha peso. Ver `skiped.md`.

---

## Conteúdo que falta (trava a publicação)

Sem estes dados, três seções da home continuam desligadas. Não invento nenhum.

- [ ] **Prazo de entrega** — resposta do FAQ
- [ ] **Custo do frete** — resposta do FAQ. Também destrava a barra de anúncio
- [ ] **Política de troca** — resposta do FAQ
- [ ] **Instruções de lavagem** — resposta do FAQ
- [ ] **Confirmar os 3 passos de medida** contra o vídeo "SapatosDuque Como Medir"
- [ ] **Loox** — ver se há avaliação real acumulada nos 1.979 pedidos. Destrava
      Prova social e Depoimentos

---

## Meu, quando o conteúdo chegar

- [ ] Escrever as 4 respostas do FAQ no `collapsible-content` e ligar a seção
- [ ] Ligar Prova social e Depoimentos com o material do Loox
- [ ] Reescrever e reativar a barra de anúncio com frete ou prazo real
- [ ] Montar as colunas de links do rodapé, depois que o menu existir no admin

---

## Dívida técnica

- [ ] **Locks stale no git** — `.git/index.lock` e `.git/HEAD.lock` aparecem
      sozinhos e travam commit, sem nenhum processo git rodando. Já aconteceu
      três vezes em 22/08. Suspeita: extensão do VS Code ou watcher segurando o
      `.git` no Windows. Contorno: conferir que não há processo git e apagar o
      lock. Causa não investigada.

- [ ] **MCP de navegador** — instalar `@playwright/mcp` e conectar ao Chrome já
      logado, para QA visual e para executar a fila do `ADMIN.md`. Vale montar
      antes da Etapa 4, que é toda conferência de viewport. Ver `CLAUDE.md`,
      seção 4.

- [ ] **Rótulos de tamanho com `=`** — as variantes são `0=`, `PP=`, `P=`, `M=`,
      `G=`, `GG=`, `XG=`, `XXG=`. O `=` é ruído. Se renomear no admin, a tabela
      da home tem que mudar junto: as duas precisam casar, senão o cliente mede
      a patinha e não acha o tamanho. Ver `ADMIN.md`.
