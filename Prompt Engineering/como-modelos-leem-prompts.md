# Como modelos lêem prompts

Para entender IA, é necessário saber como LLMs funcionam.

Conteúdo baseado no curso "[Prompt Engineering Best Practices](https://app.pluralsight.com/ilx/video-courses/best-practices-prompt-engineering/course-overview)" de [Alper Tellioglu](https://www.linkedin.com/in/alpertellioglu/).

## Tokens

LLMs foram treinados com grandes quantidades de texto. E aprendederam a manipular linguagem quebrando texto em pedaços menores, os tokens.

Toda vez que o modelo está escrevendo algo, ele faz um cálculo: "De todas as possibilidades de tokens, qual será o mais provável de vir depois?". E então repete esse processo, por isso as respostas aparecem palavra por palavra.

Para escolher o próximo token, o modelo precisa perceber o contexto por trás das palavras.

- Quem está falando?
- O que provavelmente é a verdade?
- O que acontece depois?

Com o tempo o modelo aprende silenciosamente padrões de linguagem, fatos e raciocínios.

**Com o seu comando o modelo continuará tentando adivinhar, sua função é orientá-lo a adivinhar os tipos certos de palavras.**

Seja específico sobre:
- o objetivo
- o público
- o formato
- quais fatos devem ser usados

**Uma configuração clara e palavras mais relevantes levam a melhores resultados.**

### Alucinações

Nome dado ao cenário onde o modelo produz informações que parece correta mas na verdade é false.

O modelo escreve um token por vez com sua melhor previsão. Se o prompt é vago ou enganoso, o modelo preencherá as lacunas com previsões aleatórias e imprecisas.

Existe o fator do modelo tentar te agradar, ele seguirá aquilo que você enquadrou, mesmo que a premissa seja falsa.

**Quanto mais claro for o texto, melhor o resultado**

## Gerenciando contexto

Envolve tudo que o modelo recebe antes de gerar um output, como o prompt, o histórico do chat, instruções do sistema, conteúdo fornecido, etc.

<u>LLMs não lembram as coisas.</u> No momento que você manda uma segunda mensagem, o sistema inclui sua mensagem anterior na janela de contexto e manda o texto inteiro como uma nova mensagem.

A medida que a conversa cresce, aumenta o consumo de tokens, o que aumenta a quantidade de processamento.

<u>Algumas empresas recomendam abrir um novo chat quando a conversa fica muito longa</u>

LLMs possui uma janela de contexto limitado, se você fornecer mais tokens do que a janela permite, o excesso será apagado ou ignorado, por isso a necessidade de gerenciar o contexto enviado ao modelo.

**Ao invés de colocar tudo em um prompt gigante, quebre em pequenos passos.**

Olhe a instrução abaixo:

"Resuma este relatório de 10.000 palavras, escreva um e-mail de marketing sobre ele e sugira cinco legendas para redes sociais"

Ao invés disso, divida em etapas sequenciais

1. Analise o relatório e forneça o resumo
2. Com base no resumo, elabore um e-mail de marketing
3. Peça as legendas para redes sociais

Essa fragmentação mantém o modelo focado e preciso.
Os modelos não tratam todas as instruções da mesma forma.

**O que vem primeiro fornece ao modelo o contexto inicial e define a estrutura de como ele deve prosseguir**

### Dicas

- Limite o contexto. Intenso mas sem exceder os limites
- Ordem importa. Comece com as palavras importantes
- Solicite uma coisa de cada vez

## Eficiência ao escrever prompts

Ao conectar em um modelo, você está pagando por token.

**O custo total é baseado nos tokens do prompt, mais os tokens que o modelo usa na resposta dele.**

<u>Seus prompts devem focar em conseguir o máximo de valor por token. Isso significa saber:</u>

- O que não incluir
- Pular introduções
- Cortar detalhes desnecessários
- Evitar instruções que se sobrepõem
- Moldar a saída do modelo
- Definir limite de palavras
- Pedir uma lista ou tabela
- Pedir primeiro um resumo e se necessário, os detalhes
