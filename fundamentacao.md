2 Uso de boas pr�ticas, n�vel de manutenibilidade e code metrics.

2.1 O que s�o boas pr�ticas

As boas pr�ticas s�o um conjunto de padr�es, princ�pios e conven��es que tem como objetivo estabelecer expressividade e legibilidade aos sistemas, isso permite que qualquer desenvolvedor com conhecimento dessas boas pr�ticas, possa compreender de forma mais r�pida detalhes essenciais sobre o prop�sito e funcionamento do software.

2.2 Qual utilidade das boas pr�ticas para um projeto de pequeno porte?

As mudan�as estrat�gicas de competitividade do mercado corporativo obrigam que o software evolua na mesma velocidade. Isso torna a manutenibilidade um indicador fundamental para ter um software adaptativo e evolutivo, que dure o maior tempo poss�vel ao menor custo de manuten��o. Esses objetivos quando atendidos, elevam � confian�a dos clientes/usu�rios e garante ao software um t�tulo de qualidade.

2.3 Como um projeto pode ficar melhor � partir da aplica��o de boas pr�ticas?

Ao aplicar boas pr�ticas em seu projeto, voc� est� aderindo � solu��es que j� foram testadas para problemas conhecidos. Al�m de reduzir a probabilidade de defeito no c�digo, isso tamb�m facilita a legibilidade e manuten��o. Em alguns casos, tamb�m pode significar aumento de desempenho pelas melhores pr�ticas de utiliza��o de recursos, no entanto o objetivo principal � sobre a qualidade do software.
Apesar da melhoria de legibilidade no c�digo atual, os padr�es podem contribuir para garantia da legibilidade a longo prazo. Ao se ter um c�digo bem aderente � boas pr�ticas provavelmente tamb�m teremos um c�digo mais �ntegro. Isso porque um c�digo que n�o viola os princ�pios SOLID por exemplo ou que aderente � conven��es ao longo de sua arquitetura, tamb�m impede que futuramente um desenvolvedor menos atencioso/experiente possa vir a viol�-los.
Para ter um software de boa qualidade, n�o � preciso garantir ader�ncia de todas as boas pr�ticas, � importante entender qual parte do projeto est� mais fr�gil e concentrar maior aten��o sobre ela. Normalmente em projetos bem estruturados, essas partes s�o facilmente identificadas atrav�s dos recurso do Code Metrics.

2.4 O que � N�vel de Manutenibilidade?

� uma c�lculo baseado na complexidade ciclom�tica do sistema, o acoplamento e a quantidade de linhas de c�digo. Um membro com baixo n�vel de manutenibilidade provavelmente possui uma l�gica confusa, grande depend�ncia externa, muitas linhas de c�digo ou complexidade ciclom�tica alta.

2.5 Code Metrics

� um sistema de avalia��o de indicadores do software. No Visual Studio (IDE padr�o para o C#) ele � uma extens�o que permite mensurar a quantidade de linhas de c�digo, a quantidade de acoplamento, a complexidade ciclom�tica e o n�vel de manutenibilidade.
O Code Metrics ajuda a identificar classes e m�todos que possuem um N�vel de Manutenibilidade baixa. Este indicador ajuda a definir um ponto inicial para an�lise da qualidade do c�digo.
O que impacta diretamente nos N�veis de Manutenibilidade do Code Metrics no geral, � a complexidade ciclom�tica e o n�vel de acoplamento. Quando esses dois s�o tratados, normalmente acarretam uma redu��o de linhas de c�digo, o que tamb�m influencia no N�vel de Manutenibilidade.
Os n�veis de manutenibilidade exibidos pelo Code Metrics s�o confi�veis para avalia��o de m�todos isoladamente, mas quando � feito uma m�dia entre mais de um m�todo ocorre uma incongru�ncia, devido o Code Metrics n�o considerar a quantidade de linhas (um fator fundamental) como um "peso" na hora de realizar a m�dia entre os dois. Ou seja, se um m�todo possui n�vel de 90% de manutenibilidade com 100 linhas e outro possui 70% com 10 linhas, a m�dia simplesmente ser� 80%. O que n�o faz sentido visto que no final o m�todo bem menor ser� bem mais r�pido de ser analisado do que o maior (que j� possui uma qualidade boa de c�digo).

Isso permite que o N�vel de Manutenibilidade do Code Metrics seja burlado, beneficiando a inader�ncia do primeiro princ�pio do SOLID - Responsabilidade �nica.

Veja a explica��o no exemplo abaixo:

Se voc� possui um m�todo sobrecarregado, com 100 linhas e com N�vel de Manutenibilidade de pouco menos de 30%, e voc� refatorar o m�todo extraindo 1 linha para outro m�todo, o projeto inteiro ter� um aumento consider�vel no N�vel de Manutenibilidade, segundo o Code Metrics.

Veja os n�meros que Code Metrics exibir�:

<table>
  <thead>
      <tr>
        <th>M�todo</th>
        <th>% Manut.</th>
        <th>-</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>M�todo 1</td>
        <td>30%</td>
        <td>x</td>
        <td>99</td>
      </tr>
    <tr>
        <td>M�todo 2</td>
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
  
Agora veja o c�lculo correto para o exemplo acima:

<table>
  <thead>
      <tr>
        <th>M�todo</th>
        <th>% Manut.</th>
        <th>-</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>M�todo 1</td>
        <td>30%</td>
        <td>x</td>
        <td>99</td>
      </tr>
    <tr>
        <td>M�todo 2</td>
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

O segundo � bem mais coerente, pois, extrair apenas 1 linha do m�todo melhorou a legibilidade do c�digo, por�m, isso contribuiu pouco para a legibilidade do projeto como todo, menos de 1% na realidade, enquanto o Code Metrics dir� 20%.




2.6 Porqu� a complexidade ciclom�tica influencia tanto na manutenibilidade do sistema?

A complexidade ciclom�tica � a contagem de fluxos poss�veis programados no c�digo, ao mesmo tempo, esse n�mero significa a quantidade m�nima de testes necess�rios para cobrir 100% do sistema.
Quanto mais caminhos o c�digo possuir, maior ser� o esfor�o para compreender e garantir o funcionamento correto.


2.7 Como saber se a qualidade do c�digo j� est� boa?

Isso depende justamente dos objetivos de qualidade desejados para o projeto. Em geral, nos softwares corporativos de pequeno porte que avaliamos neste estudo, as metas de N�vel de Manutenibilidade s�o diferentes para cada camada do sistema, sendo que o estudo identificou nos sistemas de maiores legibilidade ou p�s-refatora��o, os seguintes �ndices m�dios aceit�veis:

 Camada de Acesso � Dados: 60-80%
 Camada de Dom�nio: 80-90%
 Camada de Neg�cios: 75-85%
 Camada de Visualiza��o: 70-75%

Importante mencionar que sistemas Data Centric (popularmente chamados de CRUD) possuem n�vel de manutenibilidade muito superior na parte do software, visto que as regras de neg�cio est�o armazenadas em stored procedures no banco, onde realmente ocorrem manuten��es com maior frequ�ncia. Esse tipo de sistema foi descartado do estudo devido a dificuldade de se mensurar a legibilidade, o n�vel de manutenibilidade ou o impacto das manuten��es.
