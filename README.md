# Iniciando a construção do Projeto

Após a criação do projeto podemos excluir alguns arquivos que vem como modelo, e nesse caso não vamos precisar.

- A classe de Controllers (De Exemplo)
- A Model de Exemplo.

##### Criar a conexão com o banco de dados para persistir as informações com o Banco de Dados que nesse caso será o SQL Server. 

- Criar uma nova pasta chamada Data

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/01_CriarPastaData.png"/>

- Criar uma Classe dentro da pasta

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/02_CriarClasse.png"/>

- Essa classe vai chamar: AppDbContext.cs

  Essa classe é responsavel pelo "meio de campo" entre o nosso código c# e o Banco de Dados.
  Vamos nos comunicar com o banco de dados através desse contexto.

##### Instalar as dependencias do Projeto, através do NuGet

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/03_Pacote_NuGet.png"/>


- 53:49
