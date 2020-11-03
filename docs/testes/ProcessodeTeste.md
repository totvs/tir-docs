#TESTE DE SOFTWARE

Teste de software é uma etapa de controle de qualidade, utilizada para assegurar que o software está contemplando todas as funcionalidades esperadas e que estas estão funcionando corretamente.

O processo de teste não irá garantir que o software estará isento de bugs, mas os esforços empenhados ampliarão a qualidade do produto final.


![testes-tipos1]

Usa-se tipos, níveis e técnicas de teste para verificar os objetivos dos testes em diversos momentos do desenvolvimento de software (ciclo de vida), de acordo com as necessidades de validação.
É corriqueira a implementação de mais de um tipo, nível e técnica de teste empregada em um software para ampliar a garantia da qualidade do mesmo.

Abaixo temos mais informações sobre estes itens:

**Testes Funcionais (Caixa Preta):** É feito para validar se as implementações atendem à função designada, ou seja, o resultado esperado. Bem como se não fere regras de negócio associadas às funcionalidades do software, que podem estar divergentes das determinações existentes em sua documentação.
De modo geral, são utilizados para avaliar as funções do sistema, simulando a ação do usuário.


**Teste de Sistema:** Nestes testes são colocador parâmetros pré estabelecidos na aplicação, a fim de se obter um resultado esperado, podem ser executados manualmente ou de modo automatizado.

**Teste de Regressão:** Uma alteração feita em uma ou mais partes do sistema, seja correção ou implementação, pode afetar acidentalmente o comportamento de outras partes do mesmo código. O teste de regressão envolve a execução de testes para detectar esses efeitos colaterais indesejados.

**Teste de Integração** (contexto direcionado a automação de teste): O teste de integração tem por objetivo validar diferentes módulos em um sistema, onde a criação de novas funcionalidades ou alterações em antigas, podem modificar o comportamento de outras partes do sistema, que podem ter conexões entre si.

A execução de testes funcionais, em todas suas variações, tem por objetivo garantir a funcionalidade do sistema levando em consideração os resultados esperados, garantindo que o produto atenda as especificações e necessidades.



##Testes Manuais
Os testes manuais, são realizados por seres humanos através de casos de testes que possuem o passo a passo para validar se a execução dos testes estão de acordo com o resultado esperado. No teste manual não há auxílio de nenhuma ferramenta para execução dos testes.

##Testes Automatizados
No teste automatizado, os testes são executados através de ferramentas e frameworks que geram um script com elementos de entrada e saída, de acordo com o escopo definido e resultado esperado,valida se o mesmo passou ou falhou.

##Benefícios Teste Manuais e Automatizados
Para automatizar um cenário de teste é necessário ter conhecimento do resultado esperado, este pode ser adquirido através de um execução prévia, manual. Além deste ponto, para execução dos testes manuais leva-se em consideração o conhecimento do analista que está criando e testando os casos de teste.

Em contra partida, execução manual onera tempo, aumentando custos, pode ser interrompida por fatores humanos, alheios a qualquer planejamento de projeto, tempo, alterando um possível fluxo predefinido.

 imagem tabela 1

Em oposição ao teste manual, os testes automatizados contam com pouca interação humana, que é essencial para elaboração dos scripts, após este ponto, geralmente todos os demais processos são automatizados.

Testes automatizados são explícitos, pois permitem saber por quais pontos o robô passou para chegar em determinado erro ou acerto.

Outro benefício é a velocidade em comparação aos testes manuais, já que não há atraso entre o tempo de entrada e a verificação.
Podemos usar como exemplo a execução de testes em mais ambientes diversos da mesma aplicação, automatizados, consegue-se obter um retorno rápido e preciso da execução em todos, visto que as mesmas ações realizadas manualmente gastariam mais tempo se executados por um usuário.

Os contras da automação de testes, de início, será necessário demandar tempo para elaboração dos scripts, que além da parte técnica precisam ser consistente com o resultado esperado do sistema, em alguns casos, será necessário conhecer ou obter apoio de terceiros quanto a regra de negócio para criar os scripts.

Importante garantir que todos os ambientes, bases e outros itens que serão utilizados na automação estejam preparados.

A longo prazo ter automatização dos testes, é vantajosa pois reduz o tempo de utilização de recursos humanos nas equipes, permitindo que estes recursos possam utilizar este tempo para validar outras partes do sistema que em alguns casos, não será possível automatizar por exemplo, bem como outras validações importantes para garantir a qualidade do produto.

![autXman]


##Custo Manual X Automatizado

De acordo com os itens mencionados acima, o custo tanto do teste manual quanto ao automatizado depende do contexto no qual serão aplicados.

Para funcionalidades de teste rápido, que não demandam repetição, serão executadas em ambiente único, ou que demandariam mais tempos na criação do script de teste do que efetivamente validando o sistema, o teste manual é indicado , pois terá menor custo que o automatizado.

Em contraponto, rotinas repetitivas, que demandam execução contínua, diversidade de ambientes e poderiam onerar muito tempo para ser executada, automação, a longo prazo, tem o custo reduzido. Pode-se utilizar ambos os métodos de acordo com a necessidade e disponibilidade, a fim de garantir a qualidade do sistema a ser testado.


##PLANEJAMENTO DE TESTES

A primeira etapa do processo de teste é o planejamento. Esta etapa envolve as atividades que determinam quais serão as abordagens para atender os propósitos dos testes. O planejamento de testes irá resultar num documento chamado Plano de Teste. Neste documento estarão os objetivos e as abordagens dos testes.

Os itens a serem testados devem ser definidos visando garantir a qualidade do produto entregue, abaixo temos a pirâmide de testes, que demonstra o melhor cenário para otimizar os testes e ampliar a garantia da qualidade.

![piramidedetestes]

Após a definição do que será testado, é necessário definir os meios a serem utilizados nas validações: tipos de teste, ferramentas, base de dados, ambiente e todas as informações necessárias ao andamento dos testes.

MODELAGEM DE TESTE

Neste item vamos citar alguns conceitos sobre modelagem de testes, ampliando as opções para iniciar a construção de casos de teste que visem garantir a qualidade do produto. Alguns exemplos que podem ser utilizados:


  - Análise de valor limite
  - Particionamento por equivalência
  - Teste Randômico (Pareto)
O detalhamento destes conceitos pode ser acessado através deste link: https://qualidadebr.wordpress.com/2009/03/07/tecnicas-de-modelagem-de-teste-parte-1/

#---inserir gif com as imagens sobre tec.modelagem

Temos ainda, métodos simples como o modo de criação dos casos de teste, que podem utilizados para elaborar os mesmos em momentos distintos de acordo com a necessidade de quem irá manuseá-lo:


**Identificado**

Um caso de teste identificado, surge a partir do momento que o desenvolvedor, analista de testes ou integrantes de equipes que, geralmente, atuam com desenvolvimento , encontram um pontoitem do sistema que pode ou deve ser testado mas não será detalhado no primeiro momento.
Sendo assim é criado um caso de teste que contenha somente a descrição do que deve ser testado. Não são inseridas pré-condições, parâmetros, passo-a-passo. Posteriormente, este caso de teste será devidamente detalhado para execução.
Este caso de teste é indicado para momentos em que se tenha pouca disponibilidade de tempo para criar um caso completo, ou é necessário somente indicar um ponto a ser testado, para posteriormente, criar o caso de teste completo com todas as informações necessárias à execução.

Ao final da criação deste tipo de caso de teste, não é possível testá-lo, pois ainda não contém todos os dados necessários para tal ação.

--- Ver com Edmar o que acha de colocar um exemplo deste CT que conste no Kanoah

**Detalhado**

Nos casos de teste detalhados temos a construção de início a fim do caso de teste, incluindo dados como Objetivo, Parâmetros, Pré-condiçoes, Passo-a-passo e principalmente o Resultado esperado.
Neste tipo de caso de teste, leva-se mais tempo para criação pois é necessário informar todos os dados pertinentes à execução do caso de teste, que ao final já deve estar pronto para ser executado.

---Ver com o Edmar o que ele acha de colocar a situação de aprovação do CT por uma par.

####Prós e contras de cada caso de teste

Nos casos de teste **Identificados**, temos como pontos positivos: praticidade na criação, possibilidade de criar diversos futuros casos de teste de forma rápida, não depende necessáriamente de conhecimento técnico ou do sistema.
Em contraponto, demanda tempo posteriormente para detalhamento do vai ser testado. Se a descrição não permitir fácil interpretação,pode dificultar ou até mesmo impossibilitar a criação do caso de teste, pois se o recurso responsável por descrever não compreender do que se trata, pode não criar corretamente. 

Para casos de teste **Detalhados** podemos demonstrar como pontos positivos: pronto para ser utilizado ao final da criação, informações completas, pronto para execução.

As opções de elaboração de casos de teste citadas acima, são úteis e válidas quando utilizadas em momentos adequados a necessidade.

##Características do Caso de Teste

Independente do método utilizado para elaboração, é necessário atentar-se a características importantes para construção de casos de teste:

_**Possuir um título:** claro, objetivo, rastreável e autoexplicativo: o título do Caso de Teste deve permitir que ele seja facilmente encontrado e reconhecido, deve deixar claro qual o seu objetivo._

_**Seguir um padrão:** seguir um padrão de escrita é ideal, principalmente para facilitar a manutenibilidade dos casos de teste._
 
 _Seguir um padrão permite compreender o que está descrito e alterar com mais facilidade, um exemplo simples, sempre colocar o módulo ou rotina entre colchetes no título do caso de teste; colocar campos e mensagens entre aspas, entre outros padrões que podem ser criados e seguidos pela equipe que atua com elaboração e manutenção dos casos de teste._

_**Ser objetivo e não exaustivo:** sempre evitar casos de teste com muitos passos (mais de 20, por exemplo).
Nem sempre é possível manter um número reduzido de passos, mas um caso de teste muito extenso se torna exaustivo e pode fazer com que não se preste atenção em todos os passos._

_**Tornar evidentes as situações de falha:** o objetivo do caso de teste é encontrar bugs, portanto é necessário que o resultado esperado esteja claro. Desta forma, o testador saberá exatamente a resposta que o sistema deveria dar, deixando as falhas evidentes._

_**Ser autossuficiente:** todas as informações necessárias para a realização do teste devem estar dentro do Caso de Teste, sejam os pré-requisitos, documentos complementares, etc._

_**Atingir a maior cobertura possível:** os casos de teste devem cobrir o máximo de situações possíveis. É importante que existam casos de teste para cada fluxo documentado._

_**Estar sempre atualizado:** um caso de teste desatualizado irá confundir quem estiver testando, pois os resultados esperados já não estarão mais de acordo com o documentado._

_**Ser reutilizável:** se um caso de teste será utilizado somente uma vez, talvez nem haja a necessidade de escrevê-lo. O ideal é que os casos de teste sejam escritos para serem atualizados e reutilizados._

Estas orientações auxiliam quanto a itens importantes a serem levados em consideração na escrita do caso de teste.

Os casos de teste servirão como base para automação posteriormente.

###Em que momentos podemos aplicar estes conceitos?

A elaboração e manutenção de casos de teste acontecem em tempos diversos, abaixo serão citadas algumas ocasiões onde pode-se utilizar os conceitos que detalhamos acima:

Desenvolvimento de nova funcionalidade: Para elaborar casos de teste que contemplem o necessário para a validação correta do sistema, garantido qualidade, integridade e correto funcionamento do que foi desenvolvido, podemos aplicar os conceitos citados.

Pode-se utilizar também para manutenir os casos de teste. Devemos prezar sempre pela melhoria continua dos casos de teste, mantendo-os atualizados. Por vezes esta atualização dar-se a por alterações no sistema, que devem ser replicadas nas validações por testes.

Ainda no cenário de desenvolvimento, além de implementações padrões no sistema, podemos ter o desenvolvimento de customizações que visam abranger situações especificas para um usuário ou mais. Estas implementações devem ser testadas, inclusive pelo usuário que irá utilizá-la a fim de garantir que atenderá as necessidades pretendidas.

Um cenário comum é a realização de testes de regressão, que tem por objetivo garantir que o sistema legado (em uso), atende as especificações, garantindo sua correta funcionalidade. Nos testes de regressão, leva-se em consideração tanto sistema padrão quanto as customizações, garantindo que ambos permanecem funcionais. Exemplificando, na tela de pedido temos campos provenientes do produto padrão. Após solicitar o desenvolvimento de um campo utilizado pelo cliente "A", no momento da validação do sistema, deve-se elaborar casos de teste que verifiquem a funcionalidade do produto padrão e do campo implementado via customização.

##Mapa Mental

Ainda sobre modelagem de testes, um diagrama comum e muito utilizado é o Mapa Mental, que permite visualizar desde um contexto mais amplo até itens detalhados do sistema, de acordo com a estrutura de mapa definida por quem vai utilizá-lo.



Por definição, o Mapa Mental é o nome dado a um tipo de diagrama voltado para a gestão de informações, conhecimento e capital intelectual. Sua principal característica é o auxílio na compreensão e solução de problemas, bem como promover o aprendizado acelerado. Pode ser aplicado a qualquer tarefa, atividade, de modo individual ou em grupo, para planejar qualquer tipo de evento. Trata-se de um método para planejamento e registro gráfico cada vez mais usado em todas as áreas de conhecimento humano.

O Mapa deve ser criado e mantido pela equipe responsável e que detenha o conhecimento da mesma.

Vale ressaltar a importância de manter o mapa mental sempre atualizado.

---alterar imagem 


##Ferramentas de Gestão de Testes

Bem como as ferramentas de automação de testes vem ganhando espaço e utilidade no dia a dia das equipes, ferramentas voltadas à gestão de testes tem sido cada vez mais úteis e necessárias, pois, a partir da utilização das mesmas é possível aprimorar atuação das equipes, reutilizar testes, acompanhar os resultados e atividades executadas.

O objetivo dessas ferramentas está voltado para o controle dos testes, sejam eles manuais ou automatizados, permitindo que informações sejam coletadas e acompanhadas, possibilitando uma visão mais ampla para a tomada de decisão, fornecendo artefatos de acordo com os interesses e expectativas.

O nicho de mercado para estes itens contam atualmente, com uma extensa lista de opções de ferramentas desde distribuição gratuita, à ferramentas com licenciamento pago.

As ferramentas de gerenciamento podem ser utilizadas em todas as etapas do ciclo de vida do teste, e têm como grande vantagem a centralização de todas as informações relacionadas à evolução dos testes realizados no software.

Abaixo algumas ferramentas utilizadas:

---- imagem de ferramentas de gestão de testes 



Algumas ferramentas já executam ou tem integração com outras para gestão de defeitos.

#setup de base
##Populado

##Vazio

AnteriorIntrodução
PróximoAutomação de Testes
Made with Material for MkDocs