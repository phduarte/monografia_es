**Assunto**:

O que são boas práticas?

**Conclusão**:

As boas práticas são um conjunto de padrões, princípios e convenções que tem como objetivo estabelecer expressividade e legibilidade aos sistemas, isso permite que qualquer desenvolvedor com conhecimento dessas boas práticas, possa compreender de forma mais rápida detalhes essenciais sobre o propósito e funcionamento do software.

---

**Assunto**:

Qual a utilidade das boas práticas para um projeto de pequeno porte?

**Conclusão**:

As mudanças estratégicas de competitividade do mercado corporativo obrigam que o software evolua na mesma velocidade. Isso torna a manutenibilidade um indicador fundamental para ter um software adaptativo e evolutivo, que dure o maior tempo possível ao menor custo de manutenção. Esses objetivos quando atendidos, elevam à confiança dos clientes/usuários e garantem ao software um título de qualidade.

---

**Assunto**:

Como um projeto pode ficar melhor à partir da aplicação de boas práticas?

**Conclusão**:

Ao aplicar boas práticas em seu projeto, você está aderindo à soluções que já foram testadas para problemas conhecidos. Além de reduzir a probabilidade de defeito no código, isso também facilita a legibilidade e manutenção. Em alguns casos, também pode significar aumento de desempenho pelas melhores práticas de utilização de recursos, no entanto o objetivo principal é sobre a qualidade do software.

---

**Assunto**:

Apesar da melhoria de legibilidade no código atual, os padrões podem contribuir para garantia da legibilidade a longo prazo?

**Conclusão**:

Sim. Ao se ter um código bem aderente à boas práticas provavelmente também teremos um código mais íntegro. Isso porque um código que não viola os princípios SOLID por exemplo ou que aderente à convenções ao longo de sua arquitetura, também impede que futuramente um desenvolvedor menos atencioso/experiente possa vir a violá-los.

---

**Assunto**:

Para ter um software de boa qualidade, preciso garantir aderência de todas as boas práticas?

**Conclusão**:

Não. É importante entender qual parte do projeto está mais frágil e concentrar maior atenção sobre ela. Normalmente em projetos bem estruturados, essas partes são fácilmente identificadas através dos recursos do Code Metrics.

---

**Assunto**:

O que é Code Metrics?

**Conclusão**:

É um sistema de avaliação de indicadores do software. No Visual Studio (IDE padrão para o C#) ele é uma extensão que permite mensurar a quantidade de linhas de código, a quantidade de acoplamento, a complexidade ciclomática e o nível de manutenibilidade. No momento a extensão só calcula métricas para projetos em C#, Visual Basic e C++/CLI que não são projetos de Site.

---

**Assunto**:

Como o Code Metrics pode ajudar na identificação de códigos de baixa qualidade?

**Conclusão**:

O Code Metrics vai ajudar identificar classes e métodos que possuem um Nível de Manutenibilidade baixa. Este indicador ajuda a definir um ponto inicial para análise da qualidade do código.

---

**Assunto**:

O que é Nível de Manutenibilidade?

**Conclusão**:

É um cálculo baseado na complexidade ciclomática do sistema, o acoplamento e a quantidade de linhas de código. Um membro com baixo nível de manutenibilidade provavelmente possui uma lógica confusa, grande dependência externa, muitas linhas de código ou complexidade ciclomática alta.

---

**Assunto**:

O que impacta diretamente nos Níveis de Manutenibilidade do Code Metrics?

**Conclusão**:

No geral, a complexidade ciclomática e o nível de acoplamento são os principais influenciadores no Nível de Manutenibilidade. Quando esses dois são tratados, normalmente acarretam uma redução de linhas de código, o que também influencia no Nível de Manutenibilidade.

---

**Assunto**:

Porquê a complexidade ciclomática influencia tanto na manutenibilidade do sistema?

**Conclusão**:

A complexidade ciclomática é a contagem de fluxos possíveis programados no código, ao mesmo tempo, esse número significa a quantidade mínima de testes necessários para cobrir 100% do sistema.

Quanto mais caminhos o código possuir, maior será o esforço para compreender e garantir o funcionamento correto.

---

**Assunto**:

Como saber se a qualidade do código já está boa?

**Conclusão**:

Isso depende justamente dos objetivos de qualidade desejados para o projeto. Em geral, nos softwares corporativos de pequeno porte que avaliamos neste estudo, as metas de Nível de Manutenibilidade são diferentes para cada camada do sistema, sendo que o estudo identificou nos sistemas de maiores legibilidade ou pós-refatoração, os seguintes índices médios aceitáveis:

+ Camada de Acesso à Dados: 60-80%
+ Camada de Domínio: 80-90%
+ Camada de Negócios: 70-85%
+ Camada de Visualização: 70-75%

Importante mencionar que sistemas Data Centric (popularmente chamados de CRUD) possuem nível de manutenibilidade muito superior na parte do software, visto que as regras de negócio estão armazenadas em stored procedures no banco, onde realmente ocorrem manutenções com maior frequência. Esse tipo de sistema foi descartado do estudo devido a dificuldade de se mensurar a legibilidade, o nível de manutenibilidade ou o impacto das manutenções.

---

**Assunto**:

Os niveis de manutenibilidade exibidos pelo Code Metrics são confiáveis?

**Conclusão**:

Para avaliação de um método apenas, sim. Quando é feito uma média entre mais de um método ocorre uma incongruência, devido o Code Metrics não considerar a quantidade de linhas (um fator fundamental) como um "peso" na hora de realizar a média entre os dois. Ou seja, se um método possui nível de 90% de manutenibilidade com 100 linhas e outro possui 70% com 10 linhas, a média simplesmente será 80%. O que não faz sentido visto que no final o método bem menor será bem mais rápido de ser analisado do que o maior (que já possui uma qualidade boa de código).

Isso permite que o Nível de Manutenibilidade do Code Metrics seja burlado, beneficiando a inaderência do primeiro princípio do SOLID - Responsabilidade Única.

Veja a explicação no exemplo abaixo:

Se você possui um método sobrecarregado, com 100 linhas e com Nível de Manutenibilidade de pouco menos de 30%, e você refatora o método extraindo 1 linha para outro método, o projeto inteiro terá um aumento considerável no Nível de Manutenibilidade, segundo o Code Metrics.

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

---

**Assunto**:

Uma demonstração de antes e depois de um sistema com melhoria do indice de manutenibilidade usando boas práticas:
Análise do sistema de estoque [https://github.com/jrrnet/ControleDeEstoque]

**Conclusão**:

O índice de facilidade de manutenção da versão original do software era *77%*.

Após realizar mudanças utilizando o conceito de responsabilidade única do SOLID, no qual uma classe deve realizar apenas uma tarefa,
as classes de modelo deixaram de implementar consultas ao banco de dados, sendo esta tarefa transferida para ser responsabilidade de outras classes, o que consequentemente gerou aumento do indice de facilidade de manutenção para *80%*.

---

**Assunto**:

Demonstração do efeito da refatoração do código no índice de manutenibilidade. (Resultados do Code Metrics do Visual Studio)

**Conclusão**:

*(Projeto Original)* O método **Carregar** chamado na camada de Apresentação, passa como argumento o texto de um componente da tela (Windows Forms) que é inserido diretamente no texto da Consulta que será executada para acessar os dados da base. 

A rotina que faz a conversão dos valores dentro do DataTable para as propriedades dentro do objeto da classe Tecnico também está implementada dentro do método.

*(Trecho de código igual para ambos projetos)* Chamada do método **Carregar** na camada de Apresentação

```c#
private void Btm_Pesquisar_Click(object sender, EventArgs e)
{
    tecnico UsuarioBase = new tecnico();
    UsuarioBase = ControllerUsuario.Carregar(Txt_Tecnicos.Text);

    IDtec = UsuarioBase.Id;
    Txt_Login.Text = UsuarioBase.Nome;
    Txt_Senha.Text = UsuarioBase.Senha;
    Txt_Tipo.Text = RetornarTipo(UsuarioBase);
}
```

**Projeto Original:** (https://github.com/CristianoRC/SoftwareOrdemDeServico)
<table>
  <thead>
      <tr>
        <th>Método</th>
        <th>% Manut.</th>
        <th>Comp. Ciclomática</th>
        <th>Acop. de Classes</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Carregar</td>
        <td>51%</td>
        <td>10</td>
        <td>13</td>
        <td>20</td>
      </tr>   
  </tbody>
  </table>

```c#
public static tecnico Carregar(string Login)
{
    tecnico UsuarioBase = new tecnico();

    Spartacus.Database.Generic dataBase;
    System.Data.DataTable Tabela;

    try
    {
       dataBase = new Spartacus.Database.Sqlite(DB.GetStrConection());

       Tabela = dataBase.Query(String.Format("Select * from tecnicos WHERE Login = '{0}'", Login.ToLower()), "Tecnicos");
       [...]
    }
    catch (Exception exc)
    {
       ControllerArquivoLog.GeraraLog(exc);
    }

    return UsuarioBase;
}
```

*(Projeto Refatorado)* Separando a criação do texto da Consulta e componentes de Acesso a Dados do método original, além de outras mudanças como a criação de um método para conversão do resultado da consulta para as propriedades dentro do objeto da classe Tecnico, foi possível aumentar o índice de Facilidade de Manutenção em geral dos métodos com a mesma responsabilidade do método no *Projeto Original*.

**Projeto Refatorado:** (https://github.com/satoLG/refactor_SoftwareOrdemDeServico)
<table>
  <thead>
      <tr>
        <th>Método</th>
        <th>% Manut.</th>
        <th>Comp. Ciclomática</th>
        <th>Acop. de Classes</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>CarregarPorLogin</td>
        <td>73%</td>
        <td>1</td>
        <td>2</td>
        <td>4</td>
      </tr>
      <tr>
        <td>Carregar</td>
        <td>70%</td>
        <td>2</td>
        <td>5</td>
        <td>6</td>
      </tr>    
  </tbody>
  </table>

```c#
public static DataTable CarregarPorLogin(String Login)
{
    ComandoDB Comando = new ComandoDB("Select * from tecnicos WHERE Login = #login#");

    Comando.AdicionarParametro("login", Login.ToLower(), Spartacus.Database.Type.STRING);

    return Comando.ListarTabela("Tecnicos");
}
```

```c#
public static Tecnico Carregar(string Login)
{
    DataTable tabela = new DataTable("Tecnico");

    try
    {
        tabela = AcessoUsuario.CarregarPorLogin(Login);
    }
    catch (Exception ex)
    {
        ArquivoLog.Gerar(ex);
    }

    return PreencheTecnico(tabela);
}
```
Refatorando o código da mesma forma em todos os métodos de todas as classes que controlam o acesso aos Dados no *Projeto Original* houve um aumento considerável do índice de Facilidade de Manutenção desta camada.

**Projeto Original:**
<table>
  <thead>
      <tr>
        <th>Camada</th>
        <th>% Manut.</th>
        <th>Comp. Ciclomática</th>
        <th>Acop. de Classes</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Controller</td>
        <td>63%</td>
        <td>170</td>
        <td>46</td>
        <td>909</td>
      </tr>
  </tbody>
  </table>
  

**Projeto Refatorado:**
<table>
  <thead>
      <tr>
        <th>Camada</th>
        <th>% Manut.</th>
        <th>Comp. Ciclomática</th>
        <th>Acop. de Classes</th>
        <th>Linhas</th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Acesso a Dados</td>
        <td>72%</td>
        <td>49</td>
        <td>12</td>
        <td>217</td>
      </tr>
          <tr>
        <td>Regras de Negócio</td>
        <td>70%</td>
        <td>120</td>
        <td>37</td>
        <td>358</td>
      </tr>
          <tr>
        <td>Utilitários (Cross-Cutting)</td>
        <td>77%</td>
        <td>28</td>
        <td>11</td>
        <td>51</td>
      </tr>
  </tbody>
  </table>
  
  As 3 camadas do *Projeto Refatorado* são resultado da refatoração da camada Controller do *Projeto Original*, observando as funcionalidades e responsabilidades que estavam concentradas na mesma.

---
