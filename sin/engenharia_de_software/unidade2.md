# engenharia de software - unidade 2 - modelos de ciclo de vida

- modelos são diferentes de processos
    - um modelo de ciclo de vida é uma versão simplificada da realidade
    - é uma abstração e, tal como todas as boas abstrações, apenas a quantidade de detalhe necessária ao entendimento é incluída
    - qualquer organização que deseje por um modelo de ciclo de vida em prática deverá adicionar detalhes específicos para suas circunstâncias e cultura
    - processo de software não é o mesmo que os modelos de ciclo de vida
    - processo refere-se aos passos específicos usados ​em uma organização específica para construir sistemas
    - indica as atividades específicas que devem ser realizadas e artefatos que devem ser produzidos
    - definições de processos incluem mais detalhes do que os modelos de ciclo de vida

- ciclo de vida do software
    - um conjunto de fases, geralmente em ordem sequencial, cujos nome e quantidades são determinados pelas necessidades de controle da organização ou organizações envolvidas
    - a última fase do ciclo de vida de um produto geralmente é a deterioração e a morte do produto. (pmbok)
    - é o particionamento da vida de um produto ou projeto em fases. (sei, glossário cmmi)
    - o ciclo de vida de um software descreve as fases pelas quais o software passa desde

- modelos
    - modelo cascata
    - prototipação
    - modelo incremental
    - desenvolvimento iterativo
    - modelo espiral

- modelo cascata

    - : vantagens
        - facilidade de gerenciamento, uma vez que identifica um conjunto fixo de documentos produzidos como resultado de cada fase

    - : desvantagens
        - o modelo assume que os requisitos são inalterados ao longo do desenvolvimento
        - o modelo impõe que todos os requisitos sejam completamente especificados antes do prosseguimento das etapas seguintes
        - as primeiras versões operacionais do software são obtidas nas etapas mais tardias do processo

- prototipação

    - caracteristicas
        - descartável
        - evolutiva
    
    - : vantagens
        - modelo interessante para alguns sistemas de grande porte os quais representem um certo grau de dificuldade para exprimir rigorosamente os requisitos
        - através da construção de um protótipo do sistema é possível demonstrar a realizabilidade do mesmo
        - é possível obter uma versão, mesmo simplificada, do que será o sistema com um pequeno investimento inicial
        - a experiência de desenvolver o protótipo pode reduzir o custo das fases posteriores

    - : desvantagens
        - pressão do cliente para adiantar a entrega do produto
        - as concessões de implementação a fim de colocar um protótipo em funcionamento rapidamente podem se tornar parte integrante do sistema

- ciclo de vida incremental

    - : vantagens
        - facilidade em testar o sistema, uma vez que a realização de testes em cada nível de desenvolvimento é mais fácil do que testar o sistema final
        - a obtenção de um sistema, mesmo incompleto num dado nível, pode oferecer ao cliente interessantes informações que sirvam de subsídio para a melhor definição dos requisitos finais do sistema

    - : desvantagens
        - elaboração do contrato - como o custo das características adicionais será determinada e negociada?
        - o projeto inicial deve produzir uma arquitetura robusta, que se mantenha íntegra ao longo dos incrementos

- ciclo de vida iterativo
    
    - : vantagens
        - há um grande envolvimento do usuário e do cliente permitindo um melhor feedback, permitindo que alterações nos requisitos sejam rapidamente incorporadas
        - os resultados mostrados permitirá que os usuários tenham confiança em um bom resultado
        - os riscos podem ser melhor administrados por pequenos pedaços do sistema a serem desenvolvidos em pequenos espaços de tempo

    - : desvantagens
        - pode continuamente surgir muitos requisitos novos, dificultando o término do projeto
        - gerentes que estão acostumados com a forma linear do desenvolvimento de um software podem ter alguns problemas na hora de ir para uma forma mais flexível

- modelo espiral

    - : vantagens
        - é uma abordagem realista para o desenvolvime nto de sistemas e de software em grande escala.
        - usa uma abordagem “evolucionária” à engenharia de software, capacitando o desenvolvedor e o cliente a entender e reagir aos riscos em cada etapa evolutiva.
        - o modelo se adequa a sistemas que representem um alto risco de investimento para o cliente

    - : desvantagens
        - pode ser difícil convencer grandes clientes de que a abordagem evolutiva é controlável
        - exige considerável experiência na avaliação dos riscos e fia-se nessa experiência para o sucesso

- diferentes modelos de ciclo de vida

    - diferentes modelos tem diferentes componentes e não existe um modelo correto

    - qual é o melhor modelo? 
        - responsabilidade do gerente de projeto verificar quais modelos são mais indicados para um um determinado projeto

    - a combinação de modelos é indicada de forma a criar um modelo mais aderente às necessidades do projeto

- seleção de modelos de ciclo de vida
    
    - a escolha de um modelo de ciclo de vida deve considerar as características do contexto de projeto ao qual será aplicado.
    - questões que devem ser respondidas ao selecionar um modelo de ciclo de vida:
        - qual o nível de compreensão do usuário e desenvolvedores em relação aos requisitos no início do projeto? 
        - é provável que a compreensão mude significativamente durante o desenvolvimento do projeto?
        - qual o nível de compreensão dos desenvolvedores em relação a arquitetura do sistema?
        - é provável que mudanças na arquitetura do sistema ocorram no meio do caminho?
        - qual nível de confiança é necessário?
        - o quanto é necessário planejar e projetar durante o projeto prevendo mudanças em versões futuras?
        - qual o nível de riscos implícitos no projeto?
        - pode ser limitado em um cronograma?
        - é necessário habilidade para realizar correções no meio do projeto?
        - é necessário mostrar ao cliente o progresso durante o projeto?
        - é necessário demonstrar ao usuário aspetos gerenciais durante o projeto?