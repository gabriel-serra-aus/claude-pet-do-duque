# Etapa 4 — Testes e aceite

Depende das Etapas 1, 2 e 3 aprovadas.
Termina com a publicação manual do Craft pelo Gabriel.

---

## 1. Matriz de testes

Cada linha ou passa ou não passa. Sem "está bom".

| # | Frente | Teste | Esperado |
|---|---|---|---|
| 1 | Responsivo | 3 páginas em 390px | zero rolagem horizontal |
| 2 | Responsivo | 3 páginas em 768px e 1280px | colunas onde previsto, sem sobreposição |
| 3 | Responsivo | produto em paisagem no celular | caixa de compra alcançável |
| 4 | Conteúdo | buscar `placeholder`, `Lorem`, `Várias colunas`, `Vídeo` | zero ocorrências |
| 5 | Conteúdo | buscar strings em inglês no site renderizado | zero ocorrências |
| 6 | Conteúdo | conferir cada `[PENDENTE]` | resolvido ou seção desativada |
| 7 | Acessibilidade | inspecionar todas as imagens | 100% com `alt` em pt-BR |
| 8 | Acessibilidade | selecionar a tabela de tamanhos com o cursor | texto selecionável, não imagem |
| 9 | Acessibilidade | navegar a caixa de compra só pelo teclado | todos os seletores e botões alcançáveis |
| 10 | Links | todos os links de menu, rodapé e CTA | zero 404, zero link vazio |
| 11 | Links | link do WhatsApp no celular | abre o app com +55 21 99343-8017 |
| 12 | Compra | escolher cada uma das 4 cores | a foto principal troca a cada escolha |
| 13 | Compra | tamanho + kit → adicionar ao carrinho | variante correta no carrinho |
| 14 | Compra | carrinho → checkout | abre com preço e frete corretos |
| 15 | Compra | combinação sem estoque | mensagem clara, botão desabilitado |
| 16 | Vídeo | abrir a home sem clicar em nada | zero script do YouTube carregado |
| 17 | Performance | Lighthouse mobile na home e no produto | registrar nota; comparar com o Booster |
| 18 | Performance | conferir formato das imagens | WebP, dimensionadas, lazy fora da dobra |
| 19 | Código | `shopify theme check` | zero erro; avisos revisados um a um |
| 20 | Navegadores | Chrome e Safari mobile; Chrome desktop | renderização equivalente |

---

## 2. Regressão de conteúdo

Conferir contra a especificação: cada seção existe, na ordem, com a copy definida.
Rodar a checagem sobre as listas de "remover" das Etapas 1 e 2 — cada item marcado para sair precisa realmente ter saído.

---

## 3. Aceite

- [ ] Os 20 testes passaram
- [ ] Critérios de pronto das Etapas 1, 2 e 3 satisfeitos
- [ ] Zero `[PENDENTE]` visível ao cliente
- [ ] `shopify theme check` limpo
- [ ] Antes/depois das 3 páginas aprovado pelo Gabriel
- [ ] Backup do Booster confirmado: branch `booster-live` + tema de backup na loja
- [ ] Export de produtos/páginas/navegação guardado

---

## 4. Publicação

⚠️ **Claude não publica.** Gabriel publica, no admin, com "pode publicar" explícito.

- O Booster permanece publicado até esse momento.
- Depois de publicar, o Booster continua na loja como tema **unpublished** — é o rollback.
- **Desativar a senha da loja é decisão separada** e precisa de autorização própria.

Rollback, se necessário: publicar o Booster de volta pelo admin.

---

## 5. Depois de publicar

Não bloqueia o aceite:

1. **Prova social.** Pedir avaliação por WhatsApp aos primeiros pedidos do site. Com 3 depoimentos reais com nome, ativar as duas seções que ficaram `disabled` na home e o bloco no produto.
2. **Botão de compra fixo no rodapé do mobile.** Decidir com dado de comportamento real, não com palpite. Custa CSS próprio.
