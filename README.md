# Horário de Atendimento do Professor

* Terças e quintas das 8h às 16h, exceto em janelas nas quais reunião extraordinárias acontecem. As janelas são de até 1h.
* Demais dias da semana, estou no Slack, com tempo de respostas no mesmo dia.

# Horário de Atendimento do Monitor

* Segunda: 8h30 às 10h
* Quarta: 8h30 às 10h
* Sexta: 8h30 às 9h30

# Banco de Dados II - Create, Read, Update, Delete

O famoso CRUD são as 4 operações básicas sobre bancos de dados:

* Create --> criação
* Read --> leitura
* Update --> atualização
* Delete --> destruição de registros de dados. 

Nesta segunda aula sobre banco de dados, focaremos nestas instruções e na escrita de SQL para manipularmos os bancos.


## Atividade do Dia

Vamos manipular um banco de dados comum entre todos e aplicar o CRUD nele.

Será o banco de dados do professor.


imagem do desespero

### Passo 1: Abrir o DBeaver

1.1) Inicialize o DBeaver. Teoricamente ele já deve ter sido instalado no autoestudos da semana 01. Mas caso esteja com defeito nele, faça:

  a) Caso não tenha instalado ou esteja com defeito, visite o site oficial do DBeaver (https://dbeaver.io/) e faça o download do instalador compatível com o seu sistema operacional (Windows, macOS ou Linux).
  b) Siga as instruções de instalação para instalar o DBeaver no seu computador.

### Passo 2: Configurar o DBeaver

2.1) Vá no canto esquerdo superior e procure pelo ícone **Criar nova conexão**. É uma tomada azul com o sinal de +.

2.2) Escolha o **PostgreeSQL** e clique em **Avançar**.

2.3) Em **Servidor**, escolha o **Conecte usando URL** e cole aquele link da etapa 2.12

2.4) Clique no botão **Testar conexão** para instalar drivers de primeira rodada. Esse botão **Testar conexão** está na parte inferior da atual tela.

2.5) Vai aparecer uma tela solicitando **download**. Confirme o download, pois vão vir drivers novos. 

2.6) Quando acabar o download, vai dar pau na sua conexão. Isso é normal, pois só usando a URL da etapa 2.12 para puxar drivers. Vamos resolver essa falha de conexão usando outra URL.

2.7) Com as credenciais do banco de dados do professor:

* senha: ZmTVzKJXGWyB65nRGeW7S2AkMUEI3gZ1
* host: dpg-cojpieu3e1ms73bflb6g-a.oregon-postgres.render.com
* usuário: bdgodoi_user
* banco de dados: bdgodoi

E na mesma tela da etapa 3.4, você agora escolhe **Conecte usando host** e preencha com as credenciais fornecidas.

2.8) Teste a conexão clicando em **Testar conexão** para mais uma vez atualizar drivers. E nessa hora, vai dar bom na sua conexão. Você pode clicar quantas vezes quiser nesse botão para testar a conexão.

2.9) Clique em **Concluir**

2.10) Agora você terá o seu banco de dados no menu vertical da esquerda, no campo **Navegador banco de dados**. Expanda os objetos clicando nas setinhas que estão ao lado de cada objeto. Você tem o **Bancos de dados**, **Administrar**, **Informações do sistema**. Expanda:

* Bancos de dados
   * Schemas
      * public
         * Tabelas (quando chegar aqui, você vai ver que está vazio, não tem nada! Normal até agora.)

### Passo 3: Fazendo o C (Create) do C R U D

       
3.1) Clique com o botão direito do mouse sobre **public** que está vazia e selecionar **Editor SQL** e depois **Abrir script SQL**. Nesse momento, vamos criar um pequeno script SQL que criar uma simples tabela SQL. Cole esse script lá:

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

3.2) Para rodar esse script, clique num **play laranja** minúsculo que tem logo na primeira linha do **create**. O resultado será uma tabela criada na parte de baixo da sua tela. **Caso apareça algum erro, o que será que você terá que mudar no código da etapa 3.1? Pense e fale para o professor ou para os seus colegas!!!**

Agora, dá uma paradinha e comente todas as linhas do código-fonte acima para que você possa tirar proveito disso num outro dia. Use esse forms para enviar seu comentário.


[Google Forms Preencha Aqui](https://docs.google.com/forms/d/e/1FAIpQLSfF5jHRCI_NoYLK8RiTBpbz3RLyTtnJ5E-uU9QxqmRILSCdaQ/viewform) 


3.3) Dando sequência, clique com o botão direito em **Tabelas** da etapa 2.10 e selecione **atualizar** e daí vai aparecer a tabela **users** que você acabou de criar. E dando 2 cliques na tabela **users** que você mudou para **XXX** (já que não pode ter duas tabelas de mesmo nome num mesmo banco de dados), você vai ver sua primeira tabela criada, seu primeiro banco de dados !!!! Chic! Vai estar tudo vazio, sim! Mas está criada.

3.4) Vamos dar um **INSERT** na sua tabela, que significa, entrar com dados novos. Para isso, volte no **Script SQL** da etapa 3.14, dê um enter no final da última linha e adicione essas novas linhas

```
insert into XXX (primeiro_nome, ultimo_nome, email, senha)
values ('aaaa', 'bbbb', 'cccc.dddd@gmail.com', 'inteli123' );
```

Caso tenha um erro dizendo que você já possui o users, significa que você está tentando rodar novamente o CREATE TABLE e isso não é possível. Apague ou comente as linhas do CREATE TABLE e só fique com o INSERT.


### Passo 4 - Implementar R U D do CRUD

4.1) Agora vem o desafio! Faça um código SQL que execute o **Read** no banco de dados do professor e faça o teste no seu DBeaver.

4.2) Faça um código SQL que execute o **Update** e faça o teste no seu DBeaver.

4.3) Por fim, faça um SQL que execute o **Delete** e faça o teste no seu DBeaver.

## Você deseja apresentar seu CRUD e tentar concorrer ao melhor CRUD da sala?

### Fale com o professor que nos últimos 20min da instrução, teremos as apresentações.

### Os 5 primeiros alunos inscritos concorrerão. Os 3 primeiros ganharão.

Colocar o chocolate aqui


### Passo 5 - Modelagem do seu Banco de Dados

Vamos te apresentar uma ferramenta show de bola que faz modelagem de banco de dados relacional.

Chama-se [SQLDesigner](https://github.com/ondras/wwwsqldesigner)

Por favor, faça o clone desse repositório no seu computador e aproveite a ferramenta.

5.1) Faça um clone do repositório [https://github.com/ondras/wwwsqldesigner](https://github.com/ondras/wwwsqldesigner) abrindo o seu terminal CMD na pasta que você deseja e digite ```git clone https://github.com/ondras/wwwsqldesigner```

5.2) Quando terminar, entre na pasta **wwwsqldesinger** que terá sido criada dentro da pasta em que você estava no item 5.1.

5.2) Digite ```npm install http-server -g``` que o npm vai fazer a instalação dos pacotes necessários para rodar no seu computador
