# abnt-reference-verifier

Skill para Claude que verifica, uma a uma, se referências bibliográficas no formato ABNT são reais ou foram geradas por alucinação de modelos de IA.

Para cada referência recebida, o agente faz uma busca na internet, tenta localizar a obra e classifica o resultado em quatro categorias: referência confirmada e correta, referência com informações divergentes, referência falsa ou inexistente, e referência que precisa de verificação humana.

O agente só marca uma referência como falsa quando tem certeza absoluta. Nos casos em que a busca não é suficiente para confirmar nem refutar, a referência vai para a fila de verificação humana.

## Como usar

Cole a lista de referências em uma mensagem e peça ao Claude para verificar. O agente vai processar cada referência em sequência, buscar na internet e montar um relatório em Markdown ao final com os resultados organizados por categoria e uma tabela de resumo.

A skill funciona com artigos científicos, livros, teses, dissertações, sites, legislação e outros tipos de documento.

## Sem a skill instalada

O conteúdo do `SKILL.md` também pode ser usado diretamente como prompt em qualquer conversa com Claude que tenha acesso à busca na internet. Basta copiar as instruções e colar antes da lista de referências. O comportamento provavelmente será o mesmo, ou bparecido, sem necessidade de instalar a skill.

**Requisito:** o agente precisa ter acesso à ferramenta de busca na internet.
