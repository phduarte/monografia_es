2 Uso de boas práticas, nível de manutenibilidade e code metrics.

2.1 O que são boas práticas

As boas práticas são um conjunto de padrões, princípios e convenções que tem como objetivo estabelecer expressividade e legibilidade aos sistemas, isso permite que qualquer desenvolvedor com conhecimento dessas boas práticas, possa compreender de forma mais rápida detalhes essenciais sobre o propósito e funcionamento do software.

2.2 Qual utilidade das boas práticas para um projeto de pequeno porte?

As mudanças estratégicas de competitividade do mercado corporativo obrigam que o software evolua na mesma velocidade. Isso torna a manutenibilidade um indicador fundamental para ter um software adaptativo e evolutivo, que dure o maior tempo possível ao menor custo de manutenção. Esses objetivos quando atendidos, elevam à confiança dos clientes/usuários e garante ao software um título de qualidade.

2.3 Como um projeto pode ficar melhor à partir da aplicação de boas práticas?

Ao aplicar boas práticas em seu projeto, você está aderindo à soluções que já foram testadas para problemas conhecidos. Além de reduzir a probabilidade de defeito no código, isso também facilita a legibilidade e manutenção. Em alguns casos, também pode significar aumento de desempenho pelas melhores práticas de utilização de recursos, no entanto o objetivo principal é sobre a qualidade do software.
Apesar da melhoria de legibilidade no código atual, os padrões podem contribuir para garantia da legibilidade a longo prazo. Ao se ter um código bem aderente à boas práticas provavelmente também teremos um código mais íntegro. Isso porque um código que não viola os princípios SOLID por exemplo ou que aderente à convenções ao longo de sua arquitetura, também impede que futuramente um desenvolvedor menos atencioso/experiente possa vir a violá-los.
Para ter um software de boa qualidade, não é preciso garantir aderência de todas as boas práticas, é importante entender qual parte do projeto está mais frágil e concentrar maior atenção sobre ela. Normalmente em projetos bem estruturados, essas partes são facilmente identificadas através dos recurso do Code Metrics.

2.4 O que é Nível de Manutenibilidade?

É uma cálculo baseado na complexidade ciclomática do sistema, o acoplamento e a quantidade de linhas de código. Um membro com baixo nível de manutenibilidade provavelmente possui uma lógica confusa, grande dependência externa, muitas linhas de código ou complexidade ciclomática alta.

2.5 Code Metrics

É um sistema de avaliação de indicadores do software. No Visual Studio (IDE padrão para o C#) ele é uma extensão que permite mensurar a quantidade de linhas de código, a quantidade de acoplamento, a complexidade ciclomática e o nível de manutenibilidade.
O Code Metrics ajuda a identificar classes e métodos que possuem um Nível de Manutenibilidade baixa. Este indicador ajuda a definir um ponto inicial para análise da qualidade do código.
O que impacta diretamente nos Níveis de Manutenibilidade do Code Metrics no geral, é a complexidade ciclomática e o nível de acoplamento. Quando esses dois são tratados, normalmente acarretam uma redução de linhas de código, o que também influencia no Nível de Manutenibilidade.
Os níveis de manutenibilidade exibidos pelo Code Metrics são confiáveis para avaliação de métodos isoladamente, mas quando é feito uma média entre mais de um método ocorre uma incongruência, devido o Code Metrics não considerar a quantidade de linhas (um fator fundamental) como um "peso" na hora de realizar a média entre os dois. Ou seja, se um método possui nível de 90% de manutenibilidade com 100 linhas e outro possui 70% com 10 linhas, a média simplesmente será 80%. O que não faz sentido visto que no final o método bem menor será bem mais rápido de ser analisado do que o maior (que já possui uma qualidade boa de código).

Isso permite que o Nível de Manutenibilidade do Code Metrics seja burlado, beneficiando a inaderência do primeiro princípio do SOLID - Responsabilidade Única.

Veja a explicação no exemplo abaixo:

Se você possui um método sobrecarregado, com 100 linhas e com Nível de Manutenibilidade de pouco menos de 30%, e você refatorar o método extraindo 1 linha para outro método, o projeto inteiro terá um aumento considerável no Nível de Manutenibilidade, segundo o Code Metrics.

Veja os números que Code Metrics exibirá:

<table>
  <thead>
      <tr>
        <th>Método</th>
        <th>% Manut.</th>
        <th>-</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Método 1</td>
        <td>30%</td>
        <td>x</td>
        <td>99</td>
      </tr>
    <tr>
        <td>Método 2</td>
        <td>90%</td>
        <td>x</td>
        <td>1</td>
      </tr>
  </tbody>
  <tfoot>
    <tr>
        <td>Total</td>
        <td>60%</td>
        <td>-</td>
        <td>100</td>
      </tr>
  </tfoot>
  </table>
  
Agora veja o cálculo correto para o exemplo acima:

<table>
  <thead>
      <tr>
        <th>Método</th>
        <th>% Manut.</th>
        <th>-</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Método 1</td>
        <td>30%</td>
        <td>x</td>
        <td>99</td>
      </tr>
    <tr>
        <td>Método 2</td>
        <td>90%</td>
        <td>x</td>
        <td>1</td>
      </tr>
  </tbody>
  <tfoot>
    <tr>
        <td>Total</td>
        <td>30,6% (*)</td>
        <td>-</td>
        <td>100</td>
      </tr>
  </tfoot>
  </table>

(*) Formula: ((30%*99)+(90%*1))/100 = 30,6%

O segundo é bem mais coerente, pois, extrair apenas 1 linha do método melhorou a legibilidade do código, porém, isso contribuiu pouco para a legibilidade do projeto como todo, menos de 1% na realidade, enquanto o Code Metrics dirá 20%.




2.6 Porquê a complexidade ciclomática influencia tanto na manutenibilidade do sistema?

A complexidade ciclomática é a contagem de fluxos possíveis programados no código, ao mesmo tempo, esse número significa a quantidade mínima de testes necessários para cobrir 100% do sistema.
Quanto mais caminhos o código possuir, maior será o esforço para compreender e garantir o funcionamento correto.


2.7 Como saber se a qualidade do código já está boa?

Isso depende justamente dos objetivos de qualidade desejados para o projeto. Em geral, nos softwares corporativos de pequeno porte que avaliamos neste estudo, as metas de Nível de Manutenibilidade são diferentes para cada camada do sistema, sendo que o estudo identificou nos sistemas de maiores legibilidade ou pós-refatoração, os seguintes índices médios aceitáveis:

 Camada de Acesso à Dados: 60-80%
 Camada de Domínio: 80-90%
 Camada de Negócios: 75-85%
 Camada de Visualização: 70-75%

Importante mencionar que sistemas Data Centric (popularmente chamados de CRUD) possuem nível de manutenibilidade muito superior na parte do software, visto que as regras de negócio estão armazenadas em stored procedures no banco, onde realmente ocorrem manutenções com maior frequência. Esse tipo de sistema foi descartado do estudo devido a dificuldade de se mensurar a legibilidade, o nível de manutenibilidade ou o impacto das manutenções.
