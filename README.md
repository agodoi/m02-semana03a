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

3.1) Inicialize o DBeaver. Teoricamente ele já deve ter sido instalado no autoestudos da semana 01. Mas caso esteja com defeito nele, faça:

  a) Caso não tenha instalado ou esteja com defeito, visite o site oficial do DBeaver (https://dbeaver.io/) e faça o download do instalador compatível com o seu sistema operacional (Windows, macOS ou Linux).
  b) Siga as instruções de instalação para instalar o DBeaver no seu computador.

### Passo 2: Configurar o DBeaver

3.2) Vá no canto esquerdo superior e procure pelo ícone **Criar nova conexão**. É uma tomada azul com o sinal de +.

3.3) Escolha o **PostgreeSQL** e clique em **Avançar**.

3.4) Em **Servidor**, escolha o **Conecte usando URL** e cole aquele link da etapa 2.12

3.5) Clique no botão **Testar conexão** para instalar drivers de primeira rodada. Esse botão **Testar conexão** está na parte inferior da atual tela.

3.6) Vai aparecer uma tela solicitando **download**. Confirme o download, pois vão vir drivers novos. 

3.7) Quando acabar o download, vai dar pau na sua conexão. Isso é normal, pois só usando a URL da etapa 2.12 para puxar drivers. Vamos resolver essa falha de conexão usando outra URL.

3.8) Volte no RENDER, na etapa 2.11 e copie o segundo link de conexão externa **PSQL Command Connect from the command line** e cole num arquivo TXT. Será uma coisa assim:
PGPASSWORD=RGeW7S2AkMUEI3gZ1 psql -h dpg-cos73bflb6g-a.oregon-postgres.render.com -U bdgodoi_user bdgodoi

3.9) Com a URL que acabou de pegar, separe os dados **senha** que é tudo que está após **PGPASSWORD** até o primeiro espaço vazio que é o mesmo que antes de **psql**. Separe o hostname do seu computador que é tudo que está após **h** até o **.com**. Separe o usuário que está após o **-U** e o nome do banco de dados que é tudo que está no final da URL. Então você precisa de uma tabela assim:

* senha: RGeW7S2AkMUEI3gZ1
* host: dpg-cos73bflb6g-a.oregon-postgres.render.com
* usuário: bdgodoi_user
* banco de dados: bdgodoi

3.10) Voltando no DBeaver, e na mesma tela da etapa 3.4, você agora escolhe **Conecte usando host** e preencha com os dados que você acabou de coletar: senha, host, usuário e banco de dados.

3.11) Teste a conexão clicando em **Testar conexão** para mais uma vez atualizar drivers. E nessa hora, vai dar bom na sua conexão. Você pode clicar quantas vezes quiser nesse botão para testar a conexão.

3.12) Clique em **Concluir**

3.13) Agora você terá o seu banco de dados no menu vertical da esquerda, no campo **Navegador banco de dados**. Expanda os objetos clicando nas setinhas que estão ao lado de cada objeto. Você tem o **Bancos de dados**, **Administrar**, **Informações do sistema**. Expanda:

* Bancos de dados
   * Schemas
      * public
         * Tabelas (quando chegar aqui, você vai ver que está vazio, não tem nada! Normal até agora.)
       
3.14) Clique com o botão direito do mouse sobre **public** que está vazia e selecionar **Editor SQL** e depois **Abrir script SQL**. Nesse momento, vamos criar um pequeno script SQL que criar uma simples tabela SQL. Cole esse script lá:

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

3.15) Para rodar esse script, clique num **play laranja** minúsculo que tem logo na primeira linha do **create**. O resultado será uma tabela criada na parte de baixo da sua tela. Caso apareça algum erro, corrija no código-fonte da etapa 3.14.

3.16) Clique com o botão direito em **Tabelas** da etapa 3.13 e selecione **atualizar** e daí vai aparecer a tabela **users** que você acabou de criar. E dando 2 cliques na tabela **users**, você vai ver sua primeira tabela criada, seu primeiro banco de dados !!!! Chic! Vai estar tudo vazio, sim! Mas está criada.

3.17) Vamos dar um **INSERT** na sua tabela, que significa, entrar com dados novos. Para isso, volte no **Script SQL** da etapa 3.14, dê um enter no final da última linha e adicione essas novas linhas

```
insert into users (primeiro_nome, ultimo_nome, email, senha)
values ('Fusca', 'Herbie', 'fusca.herbie@gmail.com', 'inteli123' );
```

Caso tenha um erro dizendo que você já possui o users, significa que você está tentando rodar novamente o CREATE TABLE e isso não é possível. Apague as linhas do CREATE TABLE e só fique com o INSERT.



