# engenharia de software - unidade 3 - processos de software

- problemas comuns
    
    - incapacidade de desenvolver ou manter software de alta qualidade com um custo razoável e dentro de um cronograma e orçamento estabelecido
    - desenvolvimento do produto errado
    - baixa produtividade
    - má qualidade
    - alto custo e duração longa de projetos de software
    - constante manutenção
    - insatisfação dos clientes
    - insatisfação dos funcionários

- melhoria de processo de software
    
    - melhorar a qualidade do produto - melhorar a qualidade do processo

- modelos são diferentes de processos
    
    - processo de software não é o mesmo que os modelos de ciclo de vida
    - processo refere-se aos passos específicos usados ​em uma organização específica para construir sistemas
    - atividades específicas que devem ser realizadas e artefatos que devem ser produzidos
    - mais detalhes do que os modelos de ciclo de vida

- processo de desenvolvimento de software
    - um processo é um conjunto de atividades para transformar entradas em saídas
    - um processo é uma sequência de passos realizados para um determinado propósito
    - um processo de desenvolvimento de software é um conjunto de atividades, parcialmente ordenadas, com a finalidade de obter um produto de software
    - define quem faz o que, quando e como, para atingir um certo objetivo

- elementos de processo
    - papéis (role): who
    - atividades (activities): how
    - artefatos (artifacts): what
    - fluxo de trabalho (workflows): when

- papéis
    - um papel é uma definição abstrata de um conjunto de atividades executadas e dos respectivos artefatos
    - normalmente os papéis são desempenhados por uma pessoa ou um grupo de pessoas que trabalham juntas em equipe
    - um membro da equipe do projeto geralmente desempenha muitos papéis distintos
    - os papéis não são pessoas; pelo contrário, eles descrevem como as pessoas se comportam no negócio e quais são as responsabilidades que elas têm
    - exemplos: analista de sistema, programador

- atividades
    - uma unidade de trabalho que um papel pode ser solicitado a executar
    - ação executada dentro do processo que resulta em um ou mais artefatos; pode envolver a utilização de ferramentas e templates
    - exemplos: identificar solicitações dos stakeholders, executar um conjunto de testes

- artefatos
    - uma informação que é usada ou produzida por um processo de desenvolvimento de software
    - um artefato pode ser um dos seguintes elementos:
        - um documento, como caso de negócio ou documento de arquitetura de software
        - um modelo, como o modelo de casos de uso ou o modelo de design
        - um elemento do modelo, ou seja, um elemento existente em um modelo, como uma classe ou um subsistema

- fluxo de trabalho
    - uma sequência típica de eventos ocorridos na condução do fluxo de trabalho, expressa em termos de detalhamentos do fluxo de trabalho. um detalhamento do fluxo de trabalho é um agrupamento de atividades que são realizadas "em conjunto" e apresentadas com artefatos informados e resultantes
    - sequência de atividades que deve ser executada em certa ordem para atingir um determinado objetivo

- méritos do processo
    - definição das atividades
    - clareza para e entre pessoas
    - transferência de workers entre projetos
    - treinamento padronizado
    - mensurável
    - resumindo: aprimora trabalho coletivo

- abordagens

    - metodologias ágeis
        - indivíduos e interação entre eles mais que processos e ferramentas;
        - software em funcionamento mais que documentação abrangente;
        - colaboração com o cliente mais que negociação de contratos;
        - responder a mudanças mais que seguir um plano
        - exemplo: scrum

    - processos tradicionais/formais
        - processos detalhados
        - análise de risco
        - adequado a grandes equipes
        - sistemas críticos
        - exemplo: rational unified process (rup)

- modelagem de processos

    - : conceito 
        - modelagem de processos permite criar uma abstração de como funciona um negócio
        - fornece o entendimento de como são realizadas as diversas atividades contidas em cada processo
        - informações e documentos são considerados, gerando um fluxo de como as atividades são realizadas
        - desde seu início até alcançar o objetivo do processo

    - : itens necessários
        - método: sequência de passos para levantamento e modelagem de informações
        - meta-modelo: informações a serem modeladas
        - notação: símbolos e regras para representar as informações
        - ferramenta: apoio computacional para documentação das informações

    - : vantagens 
        - compreender melhor o processo
        - disseminar o processo a todos os envolvidos
        - auxiliar no seu gerenciamento
        - melhorar a compreensão dos papéis dentro do processo
        - auxiliar na documentação
        - avaliação do processo
        - melhoria contínua  

    - notações 

        - spem (software process engineering metamodel)
            - adota uma abordagem oo com base na uml para modelar processos de software 

        - bpmn (business process modeling notation)
            -  é uma linguagem unificada para notação de processos
            -  permite um entendimento comum para a representação de processos
            -  vem se consolidando como uma linguagem padrão internacional de mapeamento de processos
            -  é clara
            -  é padronizada
            -  é completa

            - : elementos
                
                - : objetos de fluxo
                    
                    - principais elementos gráficos para definir comportamente do processo de trabalho
                        
                    - atividades
                        - trabalho realizado dentro de uma organização e consome recursos, com tempo e custos
                    
                    - gateways
                        - utilizar para controlar pontos de divergência e convergência de fluxo
                        - decisões
                        - ações em paralelo
                        - pontos de sincronização do fluxo
                    
                    - eventos
                        - algo que ocorre ou pode ocorrer durante o decorrer do processo
                        - afetam o fluxo de processo e usualmente tem uma causa ou um resultado
                        - podem iniciar / interromper um processo ou uma tarefa, parar / finalizar o processo
                        - eventos de início
                        - eventos intermediários
                        - eventos de fim

                - swimlanes

                    - utilizados para organizar as atividades do fluxo em diferentes categorias visuais que representam áreas funcionais, papéis, responsabilidades, entidades ou processos

                    - : pool
                        - contâiner de um único processo
                        - nome do pool deve ser o nome do processo
                        - processo abstrato (externo) pode ser diagramado como um pool vazio
                        - com os pontos de contato nos limites do pool

                    - : lane
                        - subdivisão de um pool
                        - representando um papel ou área organizacional

                - objetos conexão

                    - os objetos do fluxo se conectam entre si por meio dos conectores
                        
                    - linhas de sequência
                        - uma atividade só inicia quando a anterior finaliza
                        - usados pra representar sequência dos objetos do fluxo

                    - linhas de mensagem
                        - possíveis sinais/mensagens trocadas entre processos
                        - não podem haver linhas de mensagem entre elementos de um mesmo pool
                    
                    - associações
                
                - artefatos 

                    - objetos de dados
                        - proveem informações sobre as entradas e saídas de uma tarefa

                    - anotações
                        - permitem agregar informações adicionais sobre o processo

                    - grupos
                        - mecanismos visuais que permitem agrupar as tarefas com fins de documentação e análise