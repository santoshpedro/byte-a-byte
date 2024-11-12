---
layout: ../../layouts/post.astro
title: "Conceitos iniciais de banco de dados."
pubDate: 2024-11-12
description: "Aprenda a base que você precisa para começar a estudar banco de dados."
author: "pedro"
excerpt: "Neste conteúdo, abordo conceitos teóricos básicos que você precisa saber para entrar no universo das tecnologias de banco de dados. Nenhum pré-requisito é necessário, mas, se você já estiver familiarizado com tabelas, terá um melhor entendimento dos assuntos que vou apresentar aqui.

Vale lembrar que, apesar do meu esforço para simplificar, pode haver pequenos erros ou imprecisões que ajustarei ao longo dos estudos. Vamos focar no assunto de banco de dados sob a perspectiva dos bancos de dados relacionais, explorando como eles funcionam e como podemos manipulá-los.

"
image:
  src:
  alt:
tags: ["SQL", "MySQL", "Banco de Dados"]
---

## Abordagem inicial

Neste conteúdo, abordo conceitos teóricos básicos que você precisa saber para entrar no universo das tecnologias de banco de dados. Nenhum pré-requisito é necessário, mas, se você já estiver familiarizado com tabelas, terá um melhor entendimento dos assuntos que vou apresentar aqui.

Vale lembrar que, apesar do meu esforço para simplificar, pode haver pequenos erros ou imprecisões que ajustarei ao longo dos estudos. Vamos focar no assunto de banco de dados sob a perspectiva dos bancos de dados relacionais, explorando como eles funcionam e como podemos manipulá-los.

## Tópicos

1. [O que é um dado?](#o-que-é-um-dado)
2. [O que é um banco de dados?](#o-que-é-um-banco-de-dados)
    1. [Sistema de Banco de Dados](#sistema-de-banco-de-dados)
3. [SQL - Structured Query Language](#sql---structured-query-language)
4. [O que é uma query(consulta)?](#o-que-é-uma-queryconsulta)
5. [SQL x MySQL](#sql-x-mysql)


## O que é um dado?

Antes de entrar no mar, você terá que aprender a ser um marinheiro, e para ser um bom marinheiro, é essencial conhecer bem o seu barco. Mas qual parte do nosso barco queremos entender primeiro?
A resposta é simples: *os dados*. Tudo o que você faz usando SQL envolve consumir ou manipular dados, pois eles são a parte essencial e o motivo pelo qual aprendemos SQL e bancos de dados.

Afinal, *o que realmente é um dado*?

Um *dado* é uma unidade básica de informação. Por si só, um *dado* pode ser pouco claro e difícil de entender, pois é apenas um valor bruto. Entretanto, quando organizado e interpretado, ele pode se transformar em informação, tornando-se útil para compreender um contexto específico.

Aqui estão algumas formas que um dado pode assumir:

1. Números: *25*, *3.4*, *129*
2. Palavras ou textos: "laptop", "verde", "SQL"
3. Datas e horários: *11 de novembro de 2024*, "11/11/2024", *14:30*

*Dados vs. Informação*

Um *dado* é um **valor bruto**, enquanto a informação é um *dado* processado e interpretado, facilitando a compreensão e possibilitando a tomada de ações. Por exemplo, o número *25* isoladamente não representa nada e não nos ajuda a entender o contexto. No entanto, quando interpretamos e processamos o dado, ele se torna uma informação: *"25°C"* indica que o valor 25 se refere à temperatura, facilitando o entendimento.

Em resumo, dados são o conhecimento que temos sobre algo. Quando você curte uma foto em uma rede social, essa ação é registrada como um dado no banco de dados da plataforma. A informação, por outro lado, é o motivo pelo qual você curtiu aquela publicação – por exemplo, uma foto de um gato fofo. Sozinho, esse dado pode parecer irrelevante, mas se houver várias curtidas em publicações sobre o mesmo tema (gatos fofos), isso gera a informação de que: *"Você gosta de animais/gatos fofos".*

Os termos *dado* e *informação* estão frequentemente relacionados, e, muitas vezes, um dado é uma **informação em potencial** que, em conjunto com outros *dados*, se torna ainda mais **valioso**.

## O que é um banco de dados?

Para entender o que é um banco de dados, precisamos saber como ele é composto, ou seja, quais são as bases e o que define um banco de dados. A imagem abaixo ilustra a relação entre dados, tabelas e o banco de dados.

![RELAÇÃO DADOS TABELA E BANCO](public/image/comandos-sql-mysql/relacao-dados-tabela-banco-de-dados.jpg)

O primeiro item da imagem, *os dados*, representa o núcleo (alicerce) dessa relação. Como discutido anteriormente, os dados se tornam mais completos e valiosos quando combinados com outros dados. Mas como fazemos a relação entre esses dados? A resposta é: *tabelas*. As *tabelas* são compostas por dados agrupados sob um mesmo contexto. De modo geral, todos os dados em uma tabela estão relacionados de alguma forma e se complementam.

![Tabela de Usuário](public/image/comandos-sql-mysql/tabela-usuario.jpg)

Na imagem acima, temos a tabela de **usuário**, que é composta por cinco atributos (ou colunas) que têm como função tornar as informações do usuário mais compreensíveis. Vamos considerar que o usuário tenha apenas um identificador único (*id*), que é numérico e não possui nenhuma outra informação associada. Nesse caso, temos uma tabela cheia de usuários, mas com números como identificadores únicos, o que pode tornar a identificação e distinção de pessoas confusa, pois, na vida real, geralmente usamos nomes, apelidos ou *nicks* para identificá-las.

É por isso que conjuntos de dados são extremamente importantes. Se a tabela de usuário agora contém nome e e-mail junto com o *id*, a informação fica muito mais clara para quem está visualizando.

*Por que manter o **id** se usamos outros dados para identificar uma pessoa?*

O *id* serve como um identificador único e, embora não represente diretamente uma pessoa (como nomes e apelidos), garante a integridade dos dados. É verdade que em alguns contextos da vida real usamos números para identificar pessoas, como o CPF ou RG no Brasil. Mas, assim como o *id*, o CPF sozinho não teria muita utilidade. Imagine acessar um banco de dados do governo que contém apenas números de CPF, sem nomes, endereços ou outras informações associadas. Isso tornaria a busca e identificação de alguém muito complicada.

O *id*, portanto, garante que cada entrada na tabela de usuários seja única, permitindo distinguir entre duas pessoas, mesmo que elas tenham informações semelhantes, como nome e apelido. Isso é crucial para manter a integridade dos dados e assegurar que cada registro realmente pertence a uma pessoa específica.

Depois de entender que dados agrupados formam tabelas, é importante compreender que as tabelas também possuem relacionamentos. Esses relacionamentos tornam a informação contida nos dados mais visível e facilitam o entendimento. Assim como os dados, as tabelas se relacionam de forma lógica. Por exemplo, se temos uma tabela de *usuário*, podemos ter outra tabela que se relaciona com ela no mesmo contexto, criando um ecossistema de informações mais completo.

Para ilustrar, vamos supor que o usuário faça compras dentro do nosso aplicativo. Nesse caso, precisamos de uma tabela de compras para registrar todas as transações de compra realizadas pelos usuários. Vinculamos essas transações ao *ID* do usuário, pois é ele que garante que o usuário que fez a transação seja identificado de forma única, já que não existem *IDs* iguais.

Tabelas podem ter relacionamentos ou não, e isso é definido pelo planejamento feito por quem projeta o banco de dados. Depois de compreendermos dados, tabelas e relacionamentos, finalmente chegamos ao objetivo desta seção: explicar o conceito de banco de dados. Um banco de dados é composto por um conjunto de tabelas que armazenam os dados, bem como pelos relacionamentos entre elas. Esses relacionamentos estruturam e conectam as tabelas, permitindo que os dados sejam vinculados de maneira organizada. Em resumo, todas as tabelas e seus relacionamentos formam o banco de dados.

Com base nisso, você pode ter um ou mais bancos de dados agrupados por finalidade, como um banco de dados para a área de finanças, outro para documentos e outros para informações que um aplicativo possa necessitar. Um aplicativo pode ter um ou mais bancos de dados, e isso também depende das escolhas do projetista.

### Sistema de Banco de Dados

Um sistema de banco de dados, também conhecido como Sistema de Gerenciamento de Banco de Dados ou SGBD, é usado para 
manipular o banco de dados. Alguns exemplos incluem PostgreSQL, MySQL, Oracle e MongoDB. Entre esses, o MongoDB 
trabalha com banco de dados não relacional, ou comumente chamado de banco de dados NoSQL. Mas não entraremos em 
detalhes sobre NoSQL neste post. Você só precisa saber, por ora, que o MongoDB também é um SGBD.

De modo geral, um SGBD é projetado para gerenciar e manipular bancos de dados de maneira eficiente e segura. Eles atuam como
um intermediário entre a aplicação ou usuário e os dados armazenados no banco de dados. Agora vamos listar alguns componentes de 
um SGBD para que você possa identificá-los ou até mesmo criar um, quem sabe?

1. **Banco de Dados**: Onde os dados propriamente ditos são armazenados. Aqui, os dados podem ser estruturados de diversas maneiras (relacional, orientado a objetos, documentos, etc.). Neste post, focamos em bancos de dados relacionais, onde os dados são organizados em tabelas com linhas e colunas.

2. **Sistema de Backup e Recuperação**: Garante que os dados possam ser restaurados em caso de falhas, como queda de energia ou falhas de hardware.

3. **Sistema de Segurança e Controle de Acesso**: Define permissões e autenticações para assegurar que apenas usuários autorizados possam acessar ou modificar os dados.

4. **Linguagem de Consulta (SQL ou outras)**: A linguagem usada para interagir com o banco. Nos bancos relacionais, a Structured Query Language (SQL) é usada para realizar operações, como criar, atualizar, ler e deletar dados.

Esses são apenas alguns dos componentes principais de um SGBD. No próximo tópico iremos nos aprofundar na linguagem SQL (Structured Query Language), que é fundamental para interagir com bancos relacionais. Entender a linguagem SQL é essencial se você quiser se aprimorar em banco de dados.



### SQL - Structured Query Language

A linguagem SQL, ou Structured Query Language, é a forma de comunicação que temos com um banco de dados relacional (composto por tabelas). Para entender melhor, imagine que a cozinha de um restaurante é um banco de dados, e que essa cozinha armazena as comidas e pratos (dados). Para se comunicar com a cozinha, você precisa do garçom. Ele ouve o seu pedido, anota e vai até a cozinha fazer a solicitação do seu prato.

Nesse meio tempo, o garçom também pode verificar se o seu pedido está em conformidade com o que a cozinha oferece — nunca se sabe quando você pode pedir um prato que não está no cardápio. Após confirmar que seu pedido está correto, o garçom o passa para a cozinha, onde os cozinheiros preparam sua comida, e então o garçom a leva de volta e a entrega na sua mesa.

Nesta analogia, o garçom é a linguagem SQL, e você utilizou o tempo todo para se comunicar com banco de dados(cozinha). Mas um restaurante não tem somente pedidos, então iremos separar suas funções.

A primeira função é para os pedidos do restaurante, onde apresentarei o termo **DML (Data Manipulation Language)**. O DML é a parte da linguagem SQL responsável por lidar diretamente com os dados, como se estivéssemos manipulando os pratos pedidos pelos clientes. Abaixo, veremos o que o DML pode fazer:

1. **`SELECT`**: Quando o garçom traz o cardápio para o cliente escolher um prato, ele está ajudando o cliente a "selecionar" algo da cozinha (consulta de dados). É como o comando `SELECT`, que busca informações específicas do banco de dados.
2. **`INSERT`**: Quando o cliente faz um pedido novo, o garçom registra e envia esse pedido à cozinha para preparar um prato (inserção de dados). Esse processo representa o comando `INSERT`, que insere novos dados no banco de dados.
3. **`UPDATE`**: Se o cliente quiser ajustar algo no pedido, como trocar um ingrediente ou adicionar um extra, o garçom atualiza o pedido e informa a cozinha (atualização de dados). Esse é o papel do comando `UPDATE`, que modifica dados existentes.
4. **`DELETE`**: Se o cliente decidir cancelar um prato ou remover um item do pedido, o garçom informa à cozinha para que o prato não seja preparado (exclusão de dados). Esse é o equivalente ao comando `DELETE`, que remove dados específicos do banco de dados.

A próxima função serve para organizar e configurar o restaurante. O **DDL (Data Definition Language)** é responsável por essa função no banco de dados:

1. **`CREATE`**: É como o processo de configurar o restaurante inicialmente. Imagine que o restaurante precisa de diferentes estações de preparo (seções) para cada tipo de prato: uma para saladas, outra para massas e assim por diante. Criar essas estações é como o comando `CREATE`, que cria tabelas e estruturas no banco de dados.
2. **`ALTER`**: Com o tempo, o restaurante pode precisar de ajustes. Talvez a estação de saladas precise ser ampliada para atender mais pedidos, então a cozinha é reorganizada para isso. Isso é como o comando `ALTER`, que modifica tabelas e estruturas existentes para atender novas necessidades.
3. **`DROP`**: Se a estação de sobremesas não for mais necessária, ela pode ser desmontada e removida da cozinha. Da mesma forma, o comando `DROP` exclui tabelas ou estruturas inteiras que não são mais necessárias.

Toda essa estrutura forma o que conhecemos como SQL, e você a utilizará toda vez que precisar definir, consultar ou manipular dados no banco de dados.

### O que é uma query(consulta)?

Uma query(ou consulta) é uma requisição que fazemos ao banco de dados para recuperar, manipular ou analisar dados específicos Em SQL, uma query geralmente é um código(instrução) escrito(a) para obter exatamente as 
informações que você deseja,  utilizando critérios, filtros e condições.

Usando o exemplo anterior do restaurante, imagine que temos um cliente que é vegetariano e nosso querido garçom está treinado para atender quaisquer pedidos dos clientes. Ao fazer o pedido, o cliente menciona que só deseja ver opções vegetarianas. O garçom, então, traz o cardápio com uma seleção de pratos, mas desta vez com uma condição: ele entrega ao cliente um cardápio (SELECT) que contém somente pratos vegetarianos.

Em termos de SQL, isso seria como fazer uma consulta SELECT com uma condição (WHERE) para exibir apenas os pratos vegetarianos. A query seria algo assim:
```sql title="somente-pratos-vegetarianos.sql" showLineNumbers {2-3}
SELECT nome 
FROM pratos 
WHERE tipo = 'vegetariano';
```

---

Agora, o cliente decide fazer um pedido específico: ele escolhe um prato vegetariano e informa ao garçom. O garçom, então, anota o pedido e o registra na lista de pedidos da cozinha para que seja preparado. Essa ação é semelhante a uma query INSERT, que adiciona um novo registro (pedido) ao banco de dados.

Em SQL, a query para esse novo pedido seria assim:
```sql title="fazer-pedido-vegetariano.sql" showLineNumbers {2-3}
INSERT INTO pedidos (cliente, prato, quantidade) 
VALUES ('Cliente Vegetariano', 'Salada de Grão-de-Bico', 1);
```
Aqui, o garçom está usando INSERT para adicionar um novo pedido ao banco de dados, informando o nome do cliente, o prato escolhido e a quantidade.

---

Durante a refeição, o cliente vegetariano decide que quer uma alteração no seu pedido: ele gostaria de trocar um ingrediente, pedindo ao garçom que substitua o queijo pelo tofu. O garçom retorna à cozinha e atualiza o pedido com essa mudança. Isso corresponde a uma query UPDATE, que modifica um dado existente no banco de dados.

Em SQL, a query para essa atualização seria:
```sql title="alterar-pedido.sql" showLineNumbers {2-3}
UPDATE pedidos 
SET ingrediente = 'tofu' 
WHERE cliente = 'Cliente Vegetariano' AND prato = 'Salada de Grão-de-Bico';
```
Aqui, o garçom usa UPDATE para atualizar o ingrediente do pedido do cliente vegetariano, garantindo que ele receba a refeição conforme solicitado.

---

No final, o cliente decide que quer cancelar uma das opções de sobremesa que havia pedido. Ele chama o garçom e pede para remover essa sobremesa. O garçom, então, vai até a cozinha e remove esse prato específico da lista de pedidos. Essa ação é semelhante ao comando DELETE, que exclui um registro do banco de dados.

Em SQL, a query para cancelar esse pedido seria:
```sql title="cancelar-pedido.sql" showLineNumbers {2-3}
DELETE FROM pedidos 
WHERE cliente = 'Cliente Vegetariano' AND prato = 'Sobremesa de Frutas';
```
Aqui, o garçom usa DELETE para remover o pedido da sobremesa, atendendo à solicitação do cliente.

## Resumo

Este conteúdo abordou de forma simples e menos técnica como um banco de dados funciona, facilitando para que o assunto possa chegar em mais pessoas. Com o conhecimento adquirido aqui, você terá uma base para buscar conteúdos mais específicos sobre banco de dados. Você aprendeu o que são dados e como eles populam as tabelas. Também viu como as tabelas se relacionam e como o banco de dados é formado a partir dessas tabelas. Agora, pode escolher se aprofundar mais em SQL ou pesquisar sobre o SGBD que deseja utilizar em seus estudos.

Agradeço por ler até aqui e ressalto que trarei mais conteúdo sobre banco de dados de forma mais técnica e aprofundada. Fique de olho nos próximos posts!


