## SOLID

Resumo: Solid veio para dar enfase em boas práticas e principios do desenvolvimento OOB -> 
    - OOB: Orientação a objetos é um paradigma de programação: CONCEITOS :
        - Herança, Polimorfismo e Encapsulamento
    - Obs: OOB não é porque existe uma instancia da classe que significa que esta sendo usada OOB da forma correta.
        - se não existir comportamentos, estados e validações, não é OOB. E sim apenas classes anêmicas.
        - excessos de ifs e trycatch é sinal de programação procedural.
    
### TDD -> Esse projeto tem como base seguir o padrão tdd iniciando a partir do teste de Unitário.

- Single-Responsibility Principle:
    - Tem como primicia separar as responsabilidades e ter apenas um motivo para mudar.
    - Em nosso caso a Order tem o comportamento apenas de pedido,
      e não outros comportamento que envolvem os items e seus calculos e taxas.

- Open-closed Principle:     
    - Aberto para extensão e fechado para modificação.
    - Isso significa que deve ser extensivel sem modificar a própria classe.
    - Em nosso caso foi criado uma abstração TaxItem onde cada classe,
      desse item possa extender e calcular com a sua implementação especifica

- Liskov Substitution Principle:
    - Isso significa que cada subclasse ou classe derivada deve ser substituível por sua classe base ou pai.
    - Em nosso caso, se Cigar/Beer/Water é subclasse de item, os objetos do tipo Item pode ser substituidos
        por instancias de Cigar/Beer/Water sem quebrar o programa, 
        mas nosso exemplo a classe Water não tem implementação, taxa 0, por isso ela quebra, 
        entao é necessario criar uma nova interface de segregação que é o I do solid.

- Interface segregation Principle:
    - Um cliente nunca deve ser forçado a implementar uma interface que não utiliza, 
        ou os clientes não devem ser forçados a depender de métodos que não utilizam.
    - Em nosso caso o Water não precisa implementar nada, pq não existe taxa para agua. Não é obrigatorio.
    - Por isso foi criado TaxItem extendendo de item, extende apenas quem precisa criar uma taxa,
        e nosso caso apenas: Cigar/Beer extendem de TaxItem, 
        e Water extende de Item pq ele não precisa implementar, nada obrigatorio.

- Dependency inversion Principle:
    - As entidades devem depender de abstrações, não de concreções. 
        Afirma que o módulo de alto nível não deve depender do módulo de baixo nível, 
        mas deve depender de abstrações.        
    - Em nosso caso invertemos a dependencia para quem chama o getTaxes(date) passamos a data na chamada,
       e não dentro, porque nosso exemplo o Cigar em janeiro tem uma taxa especial. e os outros não.

 

