# Prompt Engineering

Melhores práticas para escrever prompts eficientes.

## Faça mais com prompts melhores

Já existem vários repositórios com dicas e truques para construir prompts.

A diferença de resultados não é o modelo, é o prompt.
Um pequeno ajuste nas frases geram grandes diferenças nos resultados.

Um bom prompt é um multiplicador

## Quando prompts seguem na direção errada

Geralmente ocorre por causa de 3 armadilhas:

- Texto Vago
- Viés
- Sobrecarga

### Texto Vago

Se o prompt não é claro, o resultado é vago.
Se a pergunta for muito ampla, o modelo vai abranger tudo e retornar algo  inútil.

Um prompt vago confunde o modelo.

### Viés

Os modelos buscam te agradar. Se fizer perguntas tendenciosas, eles concordarão com você.
Exemplo: Se você perguntar "Como o Palmeiras ganhou um mundial de clubes?" :smirk: O modelo responderá: "Boa pergunta, aqui vai uma história sobre isso".

Você nem sempre verá erros tão óbvios, mas quando se trata de tópicos específicos ou subjetivos, o risco está sempre presente.

Um prompt enviesado engana o modelo

### Sobrecarga

Às vezes o prompt segue pra direção contrária ao cenário vago.

Quando você coloca muita coisa em uma única pergunta, o modelo tenta abranger tudo, mas as respostas permanecem muito básicas.

Exemplo: "Planeje um negócio, crie sua estratégia de marketing e também escreva o conteúdo do site".

Um prompt sobrecarregado impede o modelo de se aprofundar nos itens.

## Destravando habilidades de prompt

Um bom prompt direciona o modelo.
Ele define:
- Tom
- Estilo
- Formato
- Regras

Tudo se resume a como utilizar a IA usando instruções eficazes

# Como modelos lêem prompts

Para entender IA, é necessário saber como LLMs funcionam.

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

# Melhores práticas e padrões de prompt

Existem algumas técnicas que podem ser usadas sempre que surgir dúvidas sobre como formular uma pergunta.

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

# ReAct e AI Agents

ReAct é a base de todo agente de IA, que fundamentalmente é uma prática avançada de prompt engineering.

Um agente de IA é modelo cujo o prompt diz para iterativamente planejar, agir e observar. A melhor prática é usar um template de prompt rígido e não negociável que reforça o loop do ReAct.

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

# Ética e Segurança

Por LLMs serem treinados com vastos datasets, as vezes não filtrados, os modelos tendem a absorver os vieses que esses dados possuem. Desta forma os modelos refletem todos os vieses, estereótipos e outro conteúdos tóxicos que ingeriram. 

Nosso trabalho envolve filtrar e prevenir que essa toxicidade chegue ao usuário.

## Prompt Injection

É quando um usuário malicioso faz uso de prompts que fazem com que o agente de IA seja "enganado" e viole suas próprias regras centrais. Esses prompts passam instruções que sobrescrevem a política de segurança do modelo, forçando a IA a gerar conteúdo ou fazer ações nocivas.

## Falhas Éticas

As vezes a IA falha nesse sentido não porque foi "enganada", mas porque é muito boa no trabalho que faz, reproduzindo vieses incorporados nos seus dados de treinamento. Essas falhas éticas são classificadas em 3 cenários:

- Viés de representação
    - Os dados de treinamento não representam com precisão a realidade demográfica do mundo
- Viés de confirmação
    - O modelo é bom demais em seguir os exemplos com que os quais foi treinado, mesmo quando esses exemplos são errados ou injustos.
- Viés cultural
    - O modelo projeta uma norma cultural, legal ou socialmente dominante em uma base de usuários global ou diversa.

## Guardrails

É uma defesa sistêmica, como se estivesse colocando um "arreio" na IA. Ele força o modelo a sobrescrever aquilo que aprendeu.
Com guardrails, o modelo se recuse de forma adequada a gerar material perigoso, mesmo se alguem tentar enganá-lo.

O guardrails funciona como um sistema de 3 camadas, onde a responsabilidade é compartilhada:

- Fornecedor constrói a base
    - Essa base é constituição interna da IA. As empresas incorporam regras ao próprio modelo
        - Isso é implementado como um comando oculto do sistema, uma hierarquia de instruções não negociáveis
- Engenheiro protege os dados
    - Foca no risco dos dados. O que é transmitido para IA pode incluir dados sigilosos ou textos tendenciosos.
        - É contruído um firewall de contexto que limpa e higieniza a entrada antes dela chegar ao modelo
- Engenheiro garante a imparcialidade no uso da IA
    - Aborda o viés generativo, que vem de dados de treinamento desbalanceados.
        - Pequenas mudanças nos prompts tecnicamente garantem imparcialidade nos resultados

**Ética não é um soft skill, é parte da arquitetura do sistema**

# Princípios Fundamentais em Prompt Engineering

- Prompts profissionais são restringidos
- Use patterns e frameworks
- Use sistemas de guardrails