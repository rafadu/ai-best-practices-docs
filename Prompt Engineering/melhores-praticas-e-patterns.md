# Melhores práticas e padrões de prompt

Existem algumas técnicas que podem ser usadas sempre que surgir dúvidas sobre como formular uma pergunta.

Conteúdo baseado no curso "[Prompt Engineering Best Practices](https://app.pluralsight.com/ilx/video-courses/best-practices-prompt-engineering/course-overview)" de [Alper Tellioglu](https://www.linkedin.com/in/alpertellioglu/).

## Act as Hack

Pedir para o modelo adotar uma persona, onde o tom, os detalhes e a perspectiva do modelo mudam. O modelo age como se estivesse em uma profissão e seu retorno fica mais próximo do que é esperado.

Existem vários repositórios open-source onde pessoas forneceram vários prompts que usam essa técnica. Eles podem ajudar a enquadrar seus próprios prompts.

## Fórmula de prompt

Uma estrutura de prompt que pode ser reusada. Exemplo:

"Do ponto de vista desta [FUNÇÃO/PAPEL], execute esta [TAREFA] neste [ESTILO] com estas [RESTRIÇÕES]"

- FUNÇÃO/PAPEL &rarr; Qual perspectiva o modelo deve adotar
- TAREFA &rarr; O que você quer que o modelo faça
- ESTILO &rarr; Como você quer que a tarefa seja entregue
- RESTRIÇÕES &rarr; Delimita duração, tempo, orçamento, formato, etc.

## Refinamento

É o processo que naturalmente todos fazem ao interagir com a IA. 

1. Você pede algo para IA
2. A resposta não está tão correta
3. Você faz um ajuste e tenta de novo

Isso molda a saída passo a passo ao invés de esperar a resposta perfeita na primeira tentativa.

Alguns truques que podem tornar o refinamento mais fácil

- Um ajuste por vez
- Seja específico sobre duração, tom, formato ou nível de detalhe
- Reuse respostas anteriores

## Gerenciamento de histórico

Usar históricos de chat longos consomem mais tokens. Então é necessário saber o momento de abrir um novo chat e continuar.

Se as mensagens anteriores são relevantes, continue. Se estão seguindo por uma direção errada ou você está procurando por outra coisa, deve ser o sinal de abrir um novo chat.

## Prompt Chaining

Você pede para uma IA gerar prompts, então pega esses prompts e fornece para a mesma IA em um chat diferente ou para outras IAs e ferramentas.

Por exemplo: Pedir para o ChatGPT escrever um prompt de criação de uma imagem artística e detalhada, coletar a resposta e mandar para o Gemini gerar a imagem.

## Evitar alucinações

Alguns truques para evitar alucinações

- Peça honestidade. 
  - Exemplo: "Se você não tiver certeza, diga".
- Forneça referências. 
  - Colar um documento ou conjunto de dados e pedir explicitamente para usar somente este material
- Peça citações
  - Pedir fontes força o modelo a depender menos de invenções
- Mantenha o escopo definido
  - Quanto mais ampla a questão mais fácil o modelo se desvia

## Debug de prompt

Quando a resposta do modelo for ruim, comece a fazer o debug. Fique no mesmo chat e iterativamente corrija ele. É um processo de 3 etapas:

- Isolamento do problema
- Ajustar as camadas ocultas do modelo
- Autocorreção

Se seu prompt ter 5 instruções separadas, remova 4. O modelo executa corretamente a tarefa mais importante?

- Se sim, o problema é sobrecarga ou conflito de instruções. 
  - Faça refinamento iterativo ou simplifique suas restrições
- Se não, o problema é má interpretação do modelo ou problema de contexto
  - Cheque a janela de contexto. Volte ao material de entrada que você forneceu.
    - Você usou tokens em excesso, passando do limite da janela de contexto?
    - Se sim, o modelo perdeu informações cruciais
      - Resuma ou divida o contexto em blocos

### Temperatura

Parâmetro de comportamento do modelo que controla a criatividade e aleatoriedade do modelo, geralmente é um número entre 0 e 1.

Em baixa temperatura (0.0 a 0.4), o modelo é mais seguro, previsível e factual.

Em alta temperatura (0.7 a 1.0), o modelo é mais criativo, usa mais variedade e imaginação.

Nos cenários onde a aplicação não permite ajustar este parâmetro de forma direta, é necessário compensar usando metaprompting

### Metaprompting

É o ato de guiar o LLM a governar ou avaliar seu próprio processo de pensamento ou sua forma de responder.

Se a saída do modelo estiver imprecisa ou ser uma alucinação, escreva textos próximos a: 

- "Sua resposta deve ser inteiramente factual e não conter qualquer especulação.". 

Isso baixa a temperatura do modelo.

Do contrário, se precisar de algo mais criativo, suba a temperatura com frases como:

- "Seja criativo, arrisque-se e gere três opções variadas e distintas."

### Metaprompting avançado

Você força o LLM a fazer o debug do próprio processo de raciocínio, demandando autorreflexão.

- Ao invés de pedir somente a resposta final, peça primeiro para o modelo explicar seu raciocínio.
- Questione a resposta. Informe ao modelo que houve uma falha e pergunte o motivo.

## Chain of Thought vs ReAct

São formas de guiar como o modelo deve pensar sobre um problema e resolvê-lo.

### Chain of Thought

O modelo raciocina e quebra o problema em pequenos passos e explica cada um deles.
Você direciona o modelo com frases como "Pense passo a passo". 

Deve ser usado em cenários onde o processo é tão importante quanto o resultado ou o problema precisa de raciocínio cuidadoso.

### ReAct

Combina o raciocínio do modelo com ações externas como pesquisas.

Você passa uma tarefa que requer informação externa ou precisa de vários passos. O modelo alterna entre racionar, escrevendo seu processo de raciocínio, e fazer ações como pesquisar na internet ou ler um documento. Depois de fazer uma ação o modelo volta a racionar, e se precisar, faz outra ação. Esse looping continua até a tarefa ser concluída.
