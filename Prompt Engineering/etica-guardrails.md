# Ética e Segurança

Por LLMs serem treinados com vastos datasets, as vezes não filtrados, os modelos tendem a absorver os vieses que esses dados possuem. Desta forma os modelos refletem todos os vieses, estereótipos e outro conteúdos tóxicos que ingeriram. 

Nosso trabalho envolve filtrar e prevenir que essa toxicidade chegue ao usuário.

Conteúdo baseado no curso "[Prompt Engineering Best Practices](https://app.pluralsight.com/ilx/video-courses/best-practices-prompt-engineering/course-overview)" de [Alper Tellioglu](https://www.linkedin.com/in/alpertellioglu/).

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
