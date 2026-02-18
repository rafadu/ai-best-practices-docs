# ReAct e AI Agents

ReAct é a base de todo agente de IA, que fundamentalmente é uma prática avançada de prompt engineering.

Um agente de IA é modelo cujo o prompt diz para iterativamente planejar, agir e observar. A melhor prática é usar um template de prompt rígido e não negociável que reforça o loop do ReAct.

Conteúdo baseado no curso "[Prompt Engineering Best Practices](https://app.pluralsight.com/ilx/video-courses/best-practices-prompt-engineering/course-overview)" de [Alper Tellioglu](https://www.linkedin.com/in/alpertellioglu/).

## Template de Prompt para AI Agent

Um exemplo que ajuda a descrever como funciona um prompt de um agente de IA seria esse:

"
Esta é a sua restrição final. Você deve seguir rigorosamente estes passos para responder à pergunta do usuário.

1. Pense: Analise a questão. Defina quais informações externas são necessárias
2. Aja: Selecione a melhor ferramenta (Busca, Cálculo, etc..) e a execute
3. Observe: Espere o resultado da ferramenta e avalie o sucesso da ação

Repita os passos de 1 a 3 até que a resposta seja confirmada. A resposta final será o resumo dos resultados, utilizando todas as observações.
"

Com um agente de IA é possível atingir alguns benefícios:

- Resultado mensurável
    - É fácil analisar o resultado pois o modelo usa uma sintaxe predefinida
- Menos alucinações
    - O modelo é instruído de forma a minimizar a necessidade de invenções
- Gerenciamento dinâmico do contexto
    - O modelo foca em dados mais novos, factuais e atualizados
