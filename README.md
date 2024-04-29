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


## Atividade do Dia

Vamos manipular um banco de dados comum entre todos e aplicar o CRUD nele.

Será o banco de dados do professor.


imagem do desespero




## Passo 1 - Modelagem do seu Banco de Dados

Vamos te apresentar uma ferramenta show de bola que faz modelagem de banco de dados relacional.

Chama-se [SQLDesigner](https://github.com/ondras/wwwsqldesigner)

Por favor, faça o clone desse repositório no seu computador e aproveite a ferramenta.

a) Faça um clone do repositório [https://github.com/ondras/wwwsqldesigner](https://github.com/ondras/wwwsqldesigner) abrindo o seu terminal CMD na pasta que você deseja e digite ```git clone https://github.com/ondras/wwwsqldesigner```

b) Quando terminar, entre na pasta **wwwsqldesinger** que terá sido criada dentro da pasta em que você estava no item 5.1.

c) Digite ```npm install http-server -g``` que o npm vai fazer a instalação dos pacotes necessários para rodar no seu computador.

d) Execute o comando ```http-server``` quando aparecer o IP local **http:127.0.0.1:8080** segura o Ctrl e clique nesse link que o seu navegador preferido irá abrir e executará o SQL Designer.

colocar uma imagem do SQL Designer

d) Ao abrir o SQL Designer, já clica em **options** no menu direito vertical e mude de **mysql** para **postgresql** e mude a língua de **en** para **pt_BR** para deixar tudo em português brasileiro. O restante dos campos pode deixar como está o original.

## Passo 2 - Inserindo Tabela no SQL Designer

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

f) Quem fica com o **primary key** e **foreign key**?

f.1) **1:1 (Um para Um):**

   * Primary Key fica na tabela principal, geralmente a que tem menos atributos, enquanto a foreign key fica na segunda tabela.
   * **Exemplos:**
      * **CPF:** Um cliente só pode ter um CPF.
      * **Código de Produto:** Um produto só pode ter um código único.
   * **Como modelar?** Adicione um primary key na primeira tabela e uma foreign key na segunda tabela.
  
f.2) **1:N (Um para Muitos):**

  * Primary Key fica na tabela principal, foreign key fica na segunda tabela.
  * **Exemplos:**
     * **Pedidos:** Um cliente pode ter vários pedidos.
     * **Itens do Pedido:** Um pedido pode ter vários itens.
  * **Como modelar?** Adicione um primary key na primeira tabela e várias foreign key nas demais tabelas.
     
f.3) **N:1 (Muitos para Um):**

* Primary Key fica na segunda tabela com cardinalidade 1, foreign key fica na primeira tabela, com cardinalidade N.
* **Exemplos:**
    * **Categoria:** Muitos produtos pertencem a uma única categoria.
    * **Endereço:** Vários endereços pertencem a um único cliente.
* **Como modelar?** Adicione primary key na segunda tabela e várias foreign key nas "primeiras" tabelas.

f.4) **N:N (Muitos para Muitos):**

* Não é possível resolver isso com a conexão de 2 primary key ou 2 foreign key entre elas. Você precisará de uma terceira tabela, chamada de **tabela de transição**.
* **Exemplos:**
  * **Autores e Livros:** Vários autores podem escrever vários livros.
  * **Alunos e Turmas:** Vários alunos podem estar matriculados em várias turmas.
* **Como modelar?** Numa terceira tabela, adicione uma foreign key da primeira e da segunda tabela.

g) Para criar um **foreign key**, busque por ela no menu vertical à direita, e clique na tabela desejada que você vai criar um foreign key.

Crie a tabela chamada **shopping_list**


6.2) Se você clicar em **SAVE** da sua tabela, verá que tem como exportar os comandos SQL, mas terá que fazer algumas adaptações para o postgresql.

## Passo 3 - Crie um novo modelo de Banco de Dados

a) Crie um banco de dados que tenha 2 tabelas.

b) Crie uma chave primária e uma estrangeira e faça a relação entre elas;

c) Implemente esse novo modelo de banco de dados DBeaver. Você pode usar continuar usando o host (Render) do professor.



## Passo 4: Abrir o DBeaver

a) Inicialize o DBeaver. Teoricamente ele já deve ter sido instalado no autoestudos da semana 01. Mas caso esteja com defeito nele, faça:

  a.1) Caso não tenha instalado ou esteja com defeito, visite o site oficial do DBeaver (https://dbeaver.io/) e faça o download do instalador compatível com o seu sistema operacional (Windows, macOS ou Linux).
  a.2) Siga as instruções de instalação para instalar o DBeaver no seu computador.

## Passo 5: Configurar o DBeaver

a) Vá no canto esquerdo superior e procure pelo ícone **Criar nova conexão**. É uma tomada azul com o sinal de +.

b) Escolha o **PostgreeSQL** e clique em **Avançar**.

c) Em **Servidor**, escolha o **Conecte usando URL** e cole aquele link da etapa **2.12**

d) Clique no botão **Testar conexão** para instalar drivers de primeira rodada. Esse botão **Testar conexão** está na parte inferior da atual tela.

e) Vai aparecer uma tela solicitando **download**. Confirme o download, pois vão vir drivers novos. 

f) Quando acabar o download, vai dar pau na sua conexão. Isso é normal, pois só usando a URL da etapa **2.12** para puxar drivers. Vamos resolver essa falha de conexão usando outra URL.

g) Com as credenciais do banco de dados do professor:

* senha: ZmTVzKJXGWyB65nRGeW7S2AkMUEI3gZ1
* host: dpg-cojpieu3e1ms73bflb6g-a.oregon-postgres.render.com
* usuário: bdgodoi_user
* banco de dados: bdgodoi

E na mesma tela da etapa 3.4, você agora escolhe **Conecte usando host** e preencha com as credenciais fornecidas.

h) Teste a conexão clicando em **Testar conexão** para mais uma vez atualizar drivers. E nessa hora, vai dar bom na sua conexão. Você pode clicar quantas vezes quiser nesse botão para testar a conexão.

i) Clique em **Concluir**

j) Agora você terá o seu banco de dados no menu vertical da esquerda, no campo **Navegador banco de dados**. Expanda os objetos clicando nas setinhas que estão ao lado de cada objeto. Você tem o **Bancos de dados**, **Administrar**, **Informações do sistema**. Expanda:

* Bancos de dados
   * Schemas
      * public
         * Tabelas (quando chegar aqui, você vai ver que está vazio, não tem nada! Normal até agora.)

## Passo 6: Fazendo o C (Create) do C R U D

       
a) Clique com o botão direito do mouse sobre **public** que está vazia e selecionar **Editor SQL** e depois **Abrir script SQL**. Nesse momento, vamos criar um pequeno script SQL que criar uma simples tabela SQL. Cole esse script lá:

```
create table users(
id SERIAL primary key,
primeiro_nome VARCHAR(50) not null,
ultimo_nome VARCHAR(50) not null,
email VARCHAR(100) not null,
senha VARCHAR(100) not null,
created_at TIMESTAMP default NOW(),
update_at TIMESTAMP default NOW()
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


## Passo 7 - Implementar R U D do CRUD

a) Agora vem o desafio! Faça um código SQL que execute o **Read** no banco de dados do professor e faça o teste no seu DBeaver.

b) Faça um código SQL que execute o **Update** e faça o teste no seu DBeaver.

c) Por fim, faça um SQL que execute o **Delete** e faça o teste no seu DBeaver.

## Você deseja apresentar seu CRUD e tentar concorrer ao melhor CRUD da sala?

### Fale com o professor que nos últimos 20min da instrução, teremos as apresentações.

### Os 5 primeiros alunos inscritos concorrerão. Os 3 primeiros ganharão.

Colocar o chocolate aqui


