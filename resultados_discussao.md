**Assunto**:

O que são boas práticas?

**Conclusão**:

As boas práticas são um conjunto de padrões, princípios e convenções que tem como objetivo estabelecer expressividade e legibilidade aos sistemas, permitindo que qualquer desenvolvedor que às conheça, possa compreender de forma mais rápida detalhes essenciais sobre o propósito e funcionamento do sistema.

---

**Assunto**:

Qual utilidade de boas práticas para um projeto de pequeno porte?

**Conclusão**:

As mudanças de estratégias de competitividade do mercado corporativo obrigam que o software evolua na mesma velocidade. Com isso, a manutenibilidade se torna o indicador fundamental para ter um software evolutivo e adaptativo, que dure o maior tempo possível e ao menor custo de manutenção. Esses objetivos quando atendidos, elevam à confiança do cliente/usuário e garante ao software um título de qualidade.

---

**Assunto**:

Como um projeto pode ficar melhor à partir de aplicação de boas práticas?

**Conclusão**:

Ao aplicar boas práticas em seu projeto, você está aderindo à soluções que já foram testadas para problemas conhecidos. Além de reduzir a probabilidade de defeito no código, isso também facilita a legibilidade e manutenção.

---

**Assunto**:

Para ter um software de boa qualidade, preciso garantir aderência de todas as boas práticas?

**Conclusão**:

Nem todos os padrões, princípios ou convenções são necessárias, é importante entender qual parte do projeto está mais fragilizada, sendo necessário maior atenção. Normalmente em projetos bem estruturados, os focos de problema são bem específicos e fácilmente identificados através de Code Metrics.

---

**Assunto**:

O que é Code Metric?

**Conclusão**:

É um sistema de avaliação de indicadores do software. No visual studio (IDE padrão de C#) ele é uma extensão que permite mensurar a quantidade de linhas de código, a quantidade de acoplamento, a complexidade ciclomática e o nível de manutenibilidade.

---

**Assunto**:

Como o Code Metric pode ajudar na identificação de códigos de baixa qualidade?

**Conclusão**:

O Code Metric vai ajudar a identificar classes e métodos que possuem um nível de manutenibilidade baixa. Estes são pontos iniciais de análise da qualidade do código.

---

**Assunto**:

O que é Nível de Manutenibilidade?

**Conclusão**:

É uma cálculo baseado na complexidade ciclomática do sistema, o acoplamento e a quantidade de linhas de código. Um membro com baixo nível de manutenibilidade provavelmente possue lógica confusa, muita dependência externa, muitas linhas de código ou complexidade ciclomática alta. 

---

**Assunto**:

O que impacta diretamente nos níveis de manutenibilidade do Code Metrics?

**Conclusão**:

São vários fatores, mas basicamente, a complexidade ciclomática e o nível de acoplamento são os principais, eles indiretamente afetam na quantidade de linhas de código.

---

**Assunto**:

Como saber se a qualidade do código já está boa?

**Conclusão**:

Essa é uma questão subjetiva, que depende justamente dos objetivos de qualidade do projeto. Nos softwares corporativos de pequeno porte que avaliamos neste estudo, os valores precisam ser separados por camada, sendo identificado nos sistemas de maiores legibilidade os seguintes índices médios aceitáveis:

+ Camada de Acesso à Dados: 60-70%
+ Camada de Domínio: 80-90%
+ Camada de Negócios: 75-85%
+ Camada de Visualização: 70-75%

Importante mencionar que sistemas Data Centric (popularmente chamados de CRUD) possuem nível de manutenibilidade muito superior na parte do software, visto que as regras de negócio estão armazenadas em store procedures no banco, onde realmente ocorrem manutenções com maior frequência. Esse tipo de sistema foi descartado do estudo devido a dificuldade de se mensurar a legibilidade, o nível de manutenibilidade ou o impacto das manutenções.

---

**Assunto**:

Porquê a complexidade ciclomática influencia tanto na manutenibilidade do sistema?

**Conclusão**:

A complexidade ciclimática conta a quantidade fluxos possíveis do código, ao mesmo tempo, esse número significa a quantidade mínima de testes necessários para cobrir 100% do sistema.

Quanto mais caminhos o código possuir, maior será o esforço de garantia de funcionamento.

---

**Assunto**:

As boas práticas são apenas para melhorar a legibilidade do código?

**Conclusão**:

Apesar de isso ser o principal. Ao se ter um código bem aderente com padrões, princípios e convenções, bem provavelmente você terá também um código mais íntegro, ou seja, que não apenas não faz usos que violem princípios, mas que impedem que futuramente um desenvolvedor menos atencioso possa vir a violá-lo.

Um exemplo, é o desacoplamento da camada de visualização e a camada de dados. Não basta simplesmente garantir que elas não se falem, deve se usar de recursos de acessibilidade da OOP (internal, private) para garantir que ambas nem saibam da existência alheia!
