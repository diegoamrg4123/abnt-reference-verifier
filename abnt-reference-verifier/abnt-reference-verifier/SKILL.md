---
name: abnt-reference-verifier
description: Verifica se referências ABNT são reais ou alucinadas por IA usando busca na internet para cada uma. Use ao receber listas de referências para checar autenticidade, completude ou erros bibliográficos.
---

# ABNT Reference Verifier

Skill para verificar, uma a uma, se referências bibliográficas no formato ABNT são autênticas e estão completas, usando busca na internet como fonte primária de verificação.

---

## Fluxo de trabalho obrigatório

Para **cada referência** da lista, execute as etapas abaixo em sequência antes de passar para a próxima. Nunca verifique múltiplas referências de uma vez.

### Etapa 1 — Extrair dados da referência
Identifique os campos presentes na referência:
- Autor(es)
- Título da obra
- Subtítulo (se houver)
- Ano de publicação
- Editora / Periódico / Instituição
- Volume, número, páginas (para artigos)
- URL e data de acesso (para sites)
- Cidade de publicação (para livros)
- Tipo de documento (artigo, livro, tese, dissertação, site, legislação, etc.)

### Etapa 2 — Busca na internet (OBRIGATÓRIO)
Execute **ao menos uma busca** para cada referência. Prefira buscas específicas:
- Para artigos: `"[título do artigo]" "[nome do autor]" [ano]`
- Para livros: `"[título do livro]" "[autor]" "[editora]" [ano]`
- Para teses/dissertações: `"[título]" "[autor]" "[universidade]" [ano]`
- Para sites: acesse ou busque a URL diretamente
- Para legislação: busque pelo número e ano da lei/decreto

Se a primeira busca for inconclusiva, tente ao menos mais uma busca com termos alternativos antes de classificar.

### Etapa 3 — Classificar a referência

Com base nos resultados da busca, classifique em uma das quatro categorias:

| Categoria | Critério |
|---|---|
| ✅ **Existe e está correta** | A obra foi encontrada e todos os campos conferem |
| ⚠️ **Existe com divergências** | A obra existe, mas há informações incorretas ou incompletas |
| ❌ **Falsa / Alucinada** | Certeza absoluta de que a obra não existe — título, autor ou dados são inventados |
| 🔍 **Verificação humana necessária** | Não foi possível confirmar nem refutar a existência com as buscas realizadas |

> **Regra de ouro:** Só classifique como ❌ **Falsa** quando tiver certeza absoluta. Em caso de dúvida, sempre classifique como 🔍 **Verificação humana necessária**.

### Etapa 4 — Registrar resultado parcial
Antes de avançar para a próxima referência, anote internamente:
- Número da referência
- Classificação
- Divergências encontradas (se houver)
- Informações corretas a substituir (se houver)
- Fonte(s) usada(s) na verificação

---

## Relatório final

Após verificar **todas** as referências, gere um relatório em Markdown com a estrutura abaixo.

```markdown
# Relatório de Verificação de Referências Bibliográficas

**Total de referências analisadas:** X  
**Data da verificação:** [data]

---

## ✅ Referências confirmadas e corretas
[Liste aqui as referências que existem e estão sem erros]

---

## ⚠️ Referências com divergências
Para cada uma, indique:
- A referência como foi fornecida
- Os campos incorretos ou ausentes
- As informações corretas encontradas na busca

---

## ❌ Referências falsas ou alucinadas
[Liste as referências identificadas como inexistentes, com justificativa da conclusão]

---

## 🔍 Referências que necessitam de verificação humana
[Liste as referências inconclusivas e o motivo da incerteza]

---

## Resumo
| Categoria | Quantidade |
|---|---|
| ✅ Corretas | X |
| ⚠️ Com divergências | X |
| ❌ Falsas/Alucinadas | X |
| 🔍 Verificação humana | X |
| **Total** | **X** |
```

---

## Regras gerais

- **Nunca pule a busca** de uma referência, mesmo que o título pareça familiar.
- **Nunca use apenas o conhecimento interno** do modelo para confirmar ou negar uma referência — a busca na internet é obrigatória.
- Foque em verificar **existência e informações bibliográficas** (autor, título, ano, editora, periódico, etc.). Não avalie formatação tipográfica ABNT (pontuação, itálico, ordem dos elementos).
- A skill deve funcionar com **qualquer tipo de referência**: artigos científicos, livros, teses, dissertações, sites, legislação, normas técnicas, etc.
- Se a lista for longa, informe o usuário quantas referências foram recebidas e vá reportando o progresso conforme verifica cada uma.
