# Prova-2-P3
Prova 2 P3

Funcionalidades: 
     
     - Adição de novos empregados: implementada na main, cria um novo funcionário e o adiciona em um ArrayList, como esse ArrayList se localiza se main, então a implementação dessa funcionalidade deveria ter sido feita nela; 
      
      - Remoção de empregados: implementada na main, apenas remove o funcionário desejado do ArrayList de funcionários que, por se localizar na main, era a única opção onde deveria ter sido implementado; 
      
      - Lançar cartão de ponto: utiliza o método CartaoDePonto que conta as horas que um funcionario trabalhou num dia e guarda essa quantidade de horas para que sejam utilizadas no cálculo do salário, esse método se localiza na classe Horista, pois apenas esse tipo de funcionário deve ser capaz de bater um cartão de ponto, portanto era a melhor localização para este método;
      
      - Lançar um resultado de venda: utiliza o método ResultadoDeVenda que acumula o valor de cada resultado de venda em atributos próprios da classe Comissionado para que esse valor seja utilizado no cálculo do salário deste tipo de funcionário, por ser uma funcionalidade que apenas seria útil aos empregados comissionados foi necessário que este método se localizasse na classe Comissionado;

      - Alterar detalhes sobre um empregado: utiliza o método AlterarInformações, que edita quaisquer informações sobre um usuário, exceto o tipo dele, esse método se localiza na classe Funcionarios por se tratar de uma funcionalidade necessária a todos os empregados sem distinção de tipo. Para se alterar o tipo de empregado, foi necessário que a implemetação fosse feita direto na main, pois era necessário fazer um cast e alterar a classe dele, isso somado ao fato de que o ArrayList de funcionários se localizava na main e era preciso alterá-lo fez com que fosse preciso que essa parte específica dessa funcionalidade fosse implementada na main;
      
      - Rodar a folha de pagamento: implementação na main, o sistema inicia no dia atual e a cada rodagem da folha de pagamento, um dia é incrementado, mostra os funcionários que devem ser pagos naquele dia, foi necessária a implementação na main tendo em vista que para acessar todos os funcionários era preciso percorrer o ArrayList que contém todos os empregados que se localiza na main; 
      
      - Desfazer/refazer operações: implementação na main. Foram necessárias duas pilhas, uma de undo e outra de redo, a cada vez que uma das sete primeiras operações é requerida, é guardado na pilha undo o estado atual dos empregados antes que haja uma alteração, daí quando se deseja fazer undo há uma troca do estado atual para o estado anterior através de um pop na pilha, enquanto a pilha de redo recebe um push desse estado antes da troca, por conta da necessidade dessa troca de estados dos empregados era necessário que a implementação fosse na main em razão do ArrayList de empregados que nela está contido;
      
      - Mostrar a agenda de pagamento: implementação na main. Divide os funcionários entre quem recebe mensalmente, bi-semanalmente ou semanalmente e os exibe de acordo com isto, por também necessitar o acesso a todos os empregados, foi preciso que fosse implementada na main; 
      
      - Criar nova agenda de pagamento: implemetação na main, pode-se alterar a frequência de pagamento entre mensal e semanal e escolher o dia que deseja ser pago com base nessa nova agenda, para isso foi criada uma classe auxiliar NovaAgenda que guarda o dia do mês ou da semana, e a frequencia, mensal ou semanal, que o funcionário deseja ser pago, com a mudança de tipo, o salário também é alterado, tal qual na funcionalidade de alterar informações, e se localiza na main pelo mesmo motivo, para facilitar o acesso ao ArrayList que contém os empregados e pela necessidade de fazer um recast.
      
 Classes:
 
      1) Funcionários:
            
            * Motivação: A necessidade de uma classe que contivesse as informações gerais a qualquer funcionário.
            
            * Solução: Uma superclasse abstrata, que tem como atributos informaçes gerais como nome, endereço, identificação no sistema, salário, método de pagamento, a pertinência ao sindicato, taxa sindical, identificação no sindicato e taxa de serviço. Possui como métodos um construtor, o método alterarInformações que edita informações sobre um usuário, e ainda um método abstrato getSalario para que suas subclasses  retornassem o salário da forma específica a cada uma.
            
            * Vantagens: Evita repetição de código e promove organização ao sistema. Sem uma superclasse seria necessário que cada tipo de empregado fosse implementado em classes separadas, e todos possuem informações gerais iguais, logo haveria a repetição de código na captação dessas informações, além de funcionalidades que são gerais a todos os tipos, como alterar informações, daí com essa superclasse e o conceito de herança foi possível evitar isso.
            
            * Desvantagens: A necessidade de fazer casts para tratar cada tipo específico de suas subclasses num ArrayList de Funcionários.
                          
                         
      2) Horista:
            
            * Motivação: A necessidade de uma classe que trabalhasse com o tipo de empregado Horista e suas especifidades.
            
            * Solução: Uma subclasse da superclasse Funcionários, com os atributos horas e horaExtra, que seriam necessários para acumular as horas do horista quando ele batesse o cartão de ponto para que fossem utilizadas no cálculo de seu salário, possui os métodos getSalário, que calcula o salário específico do horista e o método CartãoDePonto, que tem a funcionalidade de acumular as horas de trabalho diárias de um horista.
            
            * Vantagens: Poder tratar apenas as especificidades desse tipo de funcionário em uma única classe exclusiva dele e por se tratar de uma subclasse, poder tratar suas informções gerais através da superclasse por conta do uso de herança.
            
            * Desvantagens: A dificuldade de se alterar o tipo de funcionário, fazendo que esse tipo de alteração tivesse que ser implementado na main através de recasts, ao invés de ser implementado no junto às outras alterações de informações no método alterarInformacoes.
            
       
       3) Assalariado:
            
            * Motivação: A necessidade de uma classe que trabalhasse com o tipo de empregado Assalariado e suas especifidades.
            
            * Solução: A classe mais simples do sistema, uma subclasse de Funcionários, sem nenhum atributo a mais, com o
                      método getSalario que retorna o cálculo do salário específico de um assalariado.
            
            * Vantagens: Poder tratar apenas as especificidades desse tipo de funcionário em uma única classe exclusiva dele e por se tratar de uma subclasse, poder tratar suas informções gerais através da superclasse por conta da herança.
            
            * Desvantagens: A dificuldade de se alterar o tipo de funcionário, fazendo que esse tipo de alteração tivesse que ser implementado na main através de recasts, ao invés de ser implementado no junto às outras alterações de informações no método alterarInformacoes.
            
        
        4) Comissionado: 
            
            * Motivação: A necessidade de uma classe que trabalhasse com o tipo de empregado Comissionado e suas especifidades.
            
            * Solução: Uma subclasse de Funcionários, com os atributos comissao, que contém a porcentagem da comissão que o comissionado receberá por cada venda, e vendas, que acumulará cada resultado de venda do funcionário. Possui os métodos getSalário, que retorna seu salário específico e o método ResultadoDeVenda que lança um resultado de venda e o guarda no atributo vendas.
             
             * Vantagens: Poder tratar apenas as especificidades desse tipo de funcionário em uma única classe exclusiva dele e por se tratar de uma subclasse, e poder tratar suas informções gerais através da superclasse por conta do uso de herança.
             
             * Desvantagens: A dificuldade de se alterar o tipo de funcionário, fazendo que esse tipo de alteração tivesse que ser implementado na main através de recasts, ao invés de ser implementado no junto às outras alterações de informações no método alterarInformacoes.
             
        
        5) AgendaNova:
             
             * Motivação: A necessidade de uma subclasse auxiliar de Funcionários para tratar a funcionalidade do programa de criar uma nova agenda de pagamento.
             
             * Solução: Uma subclasse de Funcionários, com os atributos frequencia, que guarda a nova frequencia na qual o funcionário deseja ser pago, e dia, que guarda o dia, do mês ou da semana a depender da frequencia, no qual o funcionário deseja ser pago. Tem como métodos o getSalario que retorna o salário com base nessa nova agenda e um construtor que além de utilizar o da suplerclasse, adiciona também o dia de pagamento e a frequencia.
              
              * Vantagens: Poder criar uma nova agenda de pagamento, diferente das agendas dos horistas, comissionados e assalariados sem que se altere essas, além de herdar informações da superclasse.
              
        
        6) FolhaDePagamento:
              
              * Motivação: Uma classe que contivesse a main.
              
              * Solução: Uma classe com a main, onde se dá todo o funcionamento do sistema. 
             
            
 Padrões de Projeto:
 
         1) Iterator:
         
               * Seria utilizado no método main na classe FolhaDePagamento sempre que necessário iterar o ArrayList de Funcionarios, ou seja, seria aplicado sempre que necessário buscar um funcionário, ou mostrar uma lista de funcionários.
               * Sua implementação é feita através da interface Iterator que possui os métodos hasNext e Next, a classe IteratorFuncionario possui esses dois métodos herdados da interface, o primeiro é um booleno que informa se no ArrayList de funcionários há um próximo elemento, e o segundo passa do funcionário atual para o próximo.
         
         2) Command:
         
                * Também teria aplicação na main, eliminaria a necessidade de um menu, ou seja, evitaria que a main fosse poluídas por vários ifs ou um longo switch.
                * É implementado através de uma interface Command que possui o método execute. Então para cada uma das nove funcionalidades é criada uma classe que implementa a interface Command e que realizam cada opção desejada. Daí é criada uma classe invoker, onde existe uma HashMap que para cada valor inserido pelo usuário, vai executar um método de uma dessas classes criadas a partir do command. Daí, na main, a depender da String que o usuário digitar, uma funcionalidade será escolhida na HashMap e será executada.
          
          
          
          
