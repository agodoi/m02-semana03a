# Horário de Atendimento do Professor

* Terças e quintas das 8h às 16h, exceto em janelas nas quais reunião extraordinárias acontecem. As janelas são de até 1h.
* Demais dias da semana, estou no Slack, com tempo de respostas no mesmo dia.

# Horário de Atendimento do Monitor

* Segunda: 8h30 às 10h
* Quarta: 8h30 às 10h
* Sexta: 8h30 às 9h30

# Banco de Dados II - Create, Read, Update, Delete

O famoso CRUD são as 4 operações básicas sobre bancos de dados:

* Create --> cria tabela.
* Read --> lê tributos.
* Update --> atualiza tributos
* Delete --> destroi registros de dados. 

Nesta segunda aula sobre banco de dados, focaremos nestas instruções e na escrita de SQL para manipularmos os bancos.


## Conceitos do Dia

### DML - Data Manipulation Language

* INSERT: Quando você deseja adicionar novos itens (registros) à sua caixa de armazenamento de dados, você usa o comando INSERT. É como colocar um novo item em uma das divisórias. Você especifica em qual divisória (tabela) deseja adicionar o item e fornece os valores para todas as colunas relevantes.

```
-- Exemplo de comando INSERT para adicionar um novo registro à tabela "clientes"
INSERT INTO clientes (nome, email, idade) VALUES ('João', 'joao@email.com', 30);
-- Neste exemplo, estamos adicionando um novo cliente com nome 'João', e-mail 'joao@email.com' e idade 30 à tabela "clientes".
```

* SELECT: Às vezes, você quer ver o que está dentro das suas divisórias sem fazer nenhuma alteração. O comando SELECT é usado para isso. Você pode usar o SELECT para recuperar (selecionar) os dados que deseja ver. Por exemplo, você pode recuperar todos os itens de uma divisória específica ou apenas os itens que atendem a certos critérios.

```
-- Exemplo de comando SELECT para recuperar todos os registros da tabela "clientes"
SELECT * FROM clientes;
-- Este comando retorna todos os registros (linhas) da tabela "clientes" juntamente com todas as colunas (nome, email, idade).
```

* UPDATE: Se você precisar modificar um item que já está na sua caixa de armazenamento de dados, o comando UPDATE é o que você usa. É como mudar o valor de um item que já está dentro de uma das divisórias. Você especifica qual item deseja atualizar e fornece os novos valores para as colunas relevantes.

```
-- Exemplo de comando UPDATE para modificar o e-mail de um cliente na tabela "clientes"
UPDATE clientes SET email = 'novo_email@email.com' WHERE nome = 'João';
-- Neste exemplo, estamos atualizando o e-mail do cliente com nome 'João' para 'novo_email@email.com'.
```

* DELETE: Se você quiser remover um item da sua caixa de armazenamento de dados, o comando DELETE é o que você usa. É como tirar um item de uma das divisórias. Você especifica qual item deseja excluir e ele desaparece da sua caixa de armazenamento.

```
-- Exemplo de comando DELETE para remover um cliente da tabela "clientes"
DELETE FROM clientes WHERE nome = 'João';
-- Este comando remove o cliente com nome 'João' da tabela "clientes".
```

### DDL -  Data Definition Language

* CREATE: Este comando é usado para criar novas divisórias (tabelas), especificando o nome da tabela e os atributos que cada divisória terá. Por exemplo, se você quiser criar uma divisória para armazenar informações sobre clientes, usaria o comando CREATE TABLE.

* ALTER: Às vezes, você precisa fazer ajustes na estrutura da sua caixa de armazenamento, como adicionar uma nova divisória, renomear uma divisória existente ou adicionar/remover atributos de uma divisória. O comando ALTER é usado para fazer essas modificações na estrutura do banco de dados.

* DROP: Se por acaso você não precisar mais de uma divisória (tabela) na sua caixa de armazenamento, o comando DROP permite removê-la completamente. É como derrubar uma divisória e todas as coisas que estavam dentro dela desapareceriam junto.

## Atividade do Dia

Vamos manipular um banco de dados comum entre todos e aplicar o CRUD nele.

Será o banco de dados do professor.


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/m02-semana03a/blob/main/imgs/desespero.jpg">
   <img alt="Desespero" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/m02-semana03a/blob/main/imgs/desespero.jpg)">
</picture>


## Passo 1 - Instalando uma ferramenta de modelagem de banco de dados

Vamos te apresentar uma ferramenta show de bola que faz modelagem de banco de dados relacional.

Chama-se [SQLDesigner](https://github.com/ondras/wwwsqldesigner)

Por favor, faça o clone desse repositório no seu computador e aproveite a ferramenta.

a) Faça um clone do repositório [https://github.com/ondras/wwwsqldesigner](https://github.com/ondras/wwwsqldesigner) abrindo o seu terminal CMD na pasta que você deseja e digite ```git clone https://github.com/ondras/wwwsqldesigner```

b) Quando terminar o clone, entre na pasta **wwwsqldesigner** que terá sido criada. Exemplo: c:\suapasta\wwwsqldesigner

c) Digite ```npm install http-server -g``` dentro da pasta **wwwsqldesigner** que o npm vai fazer a instalação dos pacotes necessários para rodar no seu computador.

d) Execute o comando ```http-server``` quando aparecer o IP local **http:127.0.0.1:8080** segura o Ctrl e clique nesse link que o seu navegador preferido irá abrir e executará o SQL Designer.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/m02-semana03a/blob/main/imgs/sqldesigner.png">
   <img alt="Desespero" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/m02-semana03a/blob/main/imgs/sqldesigner.png)">
</picture>


**se deu tudo errado, use esse link [https://sql.toad.cz/](https://sql.toad.cz/)**


d) Ao abrir o SQL Designer, já clica em **options** no menu direito vertical e mude de **mysql** para **postgresql** e mude a língua de **en** para **pt_BR** para deixar tudo em português brasileiro. O restante dos campos pode deixar como está o original.

## Passo 2 - Modelando um Banco de Dados

a) Basicamente, você vai brincar com 

  * **Add table** --> adiciona tabelas
  * **Edit table** --> edita uma tabela já existente
  * **Keys** --> adiciona a chave primária ou estrangeira
  * **Add field** --> adiciona atributos
  * **Edit field** --> edita os atributos

b) Clique em **add table** e clique em qualquer lugar da área de desenho para a adicionar um tabela. Insira um nome em **Name** e pode até adicionar **Commnet** na sua tabela que descreve rapidamente o que ela faz. **Boas práticas: use nomes e atributos em inglês que vai facilitar no futuro. E sempre use o plural como nome da entidade. Exemplo: users, jobs, profiles, etc.**

c) Quando você cria a tabela já entra automaticamente o **id**. **TODA TABELA (ENTIDADE) TEM O SEU ID que geralmente é autoincremental.**. Então a primeira tabela será id = 1, depois a segunda tabela será id = 2, depois id = 3, etc, etc.

d) Para apagar um **field**, clique nele e pressione **delete** no seu notebook.

e) A maioria das variáveis é do tipo **Varchar** com **size 100**.

f) Para criar um **foreign key**, clique sobre o **primary key** (atributo **id**) da tabela 1 desejada, depois clique em **Create foreign key** no menu vertical direito, e clique na tabela 2 desejada onde estará associada a primarey key. Veja uma imagem a seguir de como ficaria se você conectar duas tabelas (users e addresses).

* Na tabela users, o cpf é a chave primária, então aparece simplesmente **cpf**
* Na tabela address, o cpf é a chave estrangeira, então aparece **cpf_users**, mas isso pode ser editado


<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/m02-semana03a/blob/main/imgs/sqldesigner_pk_fk.png">
   <img alt="Desespero" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/m02-semana03a/blob/main/imgs/sqldesigner_pk_fk.png)">
</picture>


g) Se você clicar em **SAVE** da sua tabela, verá que tem como exportar os comandos SQL, mas cuidado, ele exporta como MySQL.


### Conceito

Quem fica com o **primary key** e **foreign key**?

a) **1:1 (Um para Um):**

   * Primary Key fica na tabela principal, geralmente a que tem menos atributos, enquanto a foreign key fica na segunda tabela.
   * **Exemplos:**
      * **CPF:** Um cliente só pode ter um CPF.
      * **Código de Produto:** Um produto só pode ter um código único.
   * **Como modelar?** Adicione um primary key na primeira tabela e uma foreign key na segunda tabela.
  
b) **1:N (Um para Muitos):**

  * Primary Key fica na tabela principal, foreign key fica na segunda tabela.
  * **Exemplos:**
     * **Pedidos:** Um cliente pode ter vários pedidos.
     * **Itens do Pedido:** Um pedido pode ter vários itens.
  * **Como modelar?** Adicione um primary key na primeira tabela e várias foreign key nas demais tabelas N.
     
c) **N:1 (Muitos para Um):**

* Primary Key fica na segunda tabela com cardinalidade 1, foreign key fica na primeira tabela com cardinalidade N.
* **Exemplos:**
    * **Categoria:** Muitos produtos pertencem a uma única categoria.
    * **Endereço:** Vários endereços pertencem a um único cliente.
* **Como modelar?** Adicione primary key na segunda tabela e várias foreign key nas "primeiras" tabelas. Em resumo, fica igual ao caso de 1:N.

Então, **1:N** = **N:1**

d) **N:N (Muitos para Muitos):**

* Não é possível resolver isso com a conexão de 2 primary key ou 2 foreign key entre elas. Você precisará de uma terceira tabela, chamada de **tabela de transição**.
* **Exemplos:**
  * **Autores e Livros:** Vários autores podem escrever vários livros.
  * **Alunos e Turmas:** Vários alunos podem estar matriculados em várias turmas.
* **Como modelar?** Numa terceira tabela, adicione uma foreign key da primeira e da segunda tabela.


**Chave estrangeira sempre fica na tabela N**


## Passo 3 - Sua vez! Crie um Banco de Dados

a) Modele um banco de dados

Sua missão é criar uma parte do cenário do seu projeto com 4 tabelas:

* 2 tabelas tipo 1:1 --> que serão as tabela 1 e tabela 2, respectivamente.
* 2 tabelas tipo N:N --> aproveite a tabela 1 e faça ela relacionar com a tabela 3, mas você vai precisar criar a tabela 4, porque tabela 1 (N) e tabela 3 (N) só se relacionam através de uma tabela de transição, lembra?

b) Crie uma chave primária para Tabela 1 e uma estrangeira para Tabela 2 e faça a relação entre elas;

c) Na tabela 4, crie uma chave estrangeira para Tabela 1 e Tabela 3 e faça as conexões.

d) Implemente esse novo modelo de banco de dados DBeaver. Use o host (Render) do professor.

e) Só tenha cuidado para os nomes das entidades para não coincidir com o colega, pois caso contrário, vai dar B.O. no ```CREATE TABLE```.


## Passo 4: Implemente seu Banco de Dados no DBeaver

a) Inicialize o DBeaver. Teoricamente ele já deve ter sido instalado no autoestudos da semana 01. Mas caso esteja com defeito nele, faça:

  a.1) Caso não tenha instalado ou esteja com defeito, visite o site oficial do DBeaver (https://dbeaver.io/) e faça o download do instalador compatível com o seu sistema operacional (Windows, macOS ou Linux).
  a.2) Siga as instruções de instalação para instalar o DBeaver no seu computador.


b) Vá no canto esquerdo superior e procure pelo ícone **Criar nova conexão**. É uma tomada azul com o sinal de +.

c) Escolha o **PostgreeSQL** e clique em **Avançar**.

d) Na aba **Principal**, em **Servidor**, escolha **Conecte usando Host** e cole as seguintes informações:

* host: dpg-cojpieu3e1ms73bflb6g-a.oregon-postgres.render.com
* banco de dados: bdgodoi
* nome de usuário: bdgodoi_user
* senha: ZmTVzKJXGWyB65nRGeW7S2AkMUEI3gZ1

e) Clique no botão **Testar conexão** para instalar drivers de primeira rodada e testar sua conexão com o Render. Esse botão **Testar conexão** está na parte inferior da atual tela.

f) Caso apareça uma tela solicitando **download**. Confirme o download, pois vão vir drivers novos. 

g) Clique em **Concluir**

h) Agora você terá o banco de dados do professor no menu vertical da esquerda, no campo **Navegador banco de dados**. Expanda os objetos clicando nas setinhas que estão ao lado de cada objeto. Você tem o **Bancos de dados**, **Administrar**, **Informações do sistema**. Expanda:

* Bancos de dados
   * Schemas
      * public
         * Tabelas (quando chegar aqui, você vai ver que está vazio, não tem nada! Normal até agora.)

## Passo 5: Fazendo o C (Create) do C R U D

       
a) Clique com o botão direito do mouse sobre **public** que está vazia e selecionar **Editor SQL** e depois **Abrir script SQL**. Nesse momento, copie e cole o seu SQL do SQLDesigner. Você pode usar os exemplos dados no início dessa material.

```
-- Drop table 'addresses' if it exists
DROP TABLE IF EXISTS addresses;

-- Drop table 'users' if it exists
DROP TABLE IF EXISTS users;

-- Create table 'users'
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  cpf BIGINT
);

-- Create table 'addresses'
CREATE TABLE addresses (
  id SERIAL PRIMARY KEY,
  cpf_users BIGINT REFERENCES users(id)
);

```


b) Para rodar esse script, clique num **play laranja** minúsculo que tem logo na primeira linha do **create**. O resultado será uma tabela criada na parte de baixo da sua tela. **Caso apareça algum erro, o que será que você terá que mudar no código da etapa 3.1? Pense e fale para o professor ou para os seus colegas!!!**

Agora, dá uma paradinha e comente todas as linhas do código-fonte acima para que você possa tirar proveito disso num outro dia. Use esse forms para enviar seu comentário.


[Google Forms Preencha Aqui](https://docs.google.com/forms/d/e/1FAIpQLSfF5jHRCI_NoYLK8RiTBpbz3RLyTtnJ5E-uU9QxqmRILSCdaQ/viewform) 


c) Dando sequência, clique com o botão direito em **Tabelas** da etapa 2.10 e selecione **atualizar** e daí vai aparecer a tabela **users** que você acabou de criar. E dando 2 cliques na tabela **users** que você mudou para **XXX** (já que não pode ter duas tabelas de mesmo nome num mesmo banco de dados), você vai ver sua primeira tabela criada, seu primeiro banco de dados !!!! Chic! Vai estar tudo vazio, sim! Mas está criada.

d) Vamos dar um **INSERT** na sua tabela, que significa, entrar com dados novos. Para isso, volte no **Script SQL** da etapa 3.14, dê um enter no final da última linha e adicione essas novas linhas

```
insert into XXX (primeiro_nome, ultimo_nome, email, senha)
values ('aaaa', 'bbbb', 'cccc.dddd@gmail.com', 'inteli123' );
```

Caso tenha um erro dizendo que você já possui o users, significa que você está tentando rodar novamente o CREATE TABLE e isso não é possível. Apague ou comente as linhas do CREATE TABLE e só fique com o INSERT.


## Passo 6 - Implementar R U D do CRUD

a) Agora vem o desafio! Faça um código SQL que execute o **Read** no banco de dados do professor e faça o teste no seu DBeaver.

b) Faça um código SQL que execute o **Update** e faça o teste no seu DBeaver.

c) Por fim, faça um SQL que execute o **Delete** e faça o teste no seu DBeaver.

## Você deseja apresentar seu CRUD e tentar concorrer ao melhor CRUD da sala?

### Fale com o professor que nos últimos 20min do fechamento, teremos as apresentações.

### Os 3 primeiros alunos inscritos concorrerão. O primeiro leva uma caixa de Bis.

<picture>
   <source media="(prefers-color-scheme: light)" srcset="https://github.com/agodoi/m02-semana03a/blob/main/imgs/bisps__98269.jpg">
   <img alt="Bis" src="[YOUR-DEFAULT-IMAGE](https://github.com/agodoi/m02-semana03a/blob/main/imgs/bisps__98269.jpg)">
</picture>




