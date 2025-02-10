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

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/04_Pacote_Nuget_2.png"/>

- Instalar o EntityFrameworkCore

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/05_EntityFrameworkCore.png"/>

 # Qual a função da biblioteca EntityFrameworkCore?

A biblioteca EntityFrameworkCore (EF Core) é um ORM (Object-Relational Mapper) para o .NET que facilita a interação entre aplicações C# e bancos de dados relacionais.

### Principais funções do EF Core:

1. Mapeamento Objeto-Relacional (ORM) – Permite trabalhar com tabelas do banco de dados como objetos C# (modelos).
2. Migrations – Gera e aplica mudanças no banco de dados automaticamente com base no modelo da aplicação.
3. Consultas LINQ – Permite escrever consultas SQL usando LINQ, tornando o código mais legível e reutilizável.
4. Gerenciamento de Conexão – Cuida da conexão com o banco de dados e da execução de comandos SQL sem necessidade de interação direta.
5. Suporte a múltiplos bancos de dados – Pode ser usado com SQL Server, PostgreSQL, MySQL, SQLite, entre outros.

O EF Core simplifica o desenvolvimento ao evitar que você precise escrever SQL manualmente, tornando o código mais seguro e produtivo. 

 - Instalar o EntityFrameworkCore.SqlServer

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/06_EntityFrameworkSQL.png"/>

# Qual a função do EntityFrameworkCore.SqlServer?

O pacote EntityFrameworkCore.SqlServer é uma extensão do Entity Framework Core (EF Core) que permite que aplicações .NET utilizem o Microsoft SQL Server como banco de dados.

### Principais funções do EntityFrameworkCore.SqlServer

1. Fornece o provedor SQL Server – Permite que o EF Core interaja com bancos SQL Server.
2. Configurações otimizadas para SQL Server – Implementa funções específicas, como suporte a colunas IDENTITY, índices, JSON e Stored Procedures.
3. Compatibilidade com Migrations – Gera automaticamente scripts SQL compatíveis com SQL Server.
4. Executa consultas otimizadas – Traduz LINQ para consultas T-SQL eficientes no SQL Server.

- Instalar o EntityFrameworkCore.Design

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/07_EntityFrameworkDesign.png"/>

# Qual a função do EntityFrameworkCore.Design?

O pacote Microsoft.EntityFrameworkCore.Design é uma extensão do Entity Framework Core (EF Core) que fornece ferramentas para o desenvolvimento, especialmente para migrations e scaffolding. Ele é necessário para executar comandos como dotnet ef migrations add e dotnet ef database update.

### Principais funções do EntityFrameworkCore.Design

1. Habilita Migrations – Permite criar e aplicar migrations no banco de dados, facilitando a evolução do esquema.
2. Suporte a Scaffolding – Gera modelos de entidade a partir de um banco de dados existente (dotnet ef dbcontext scaffold).
3. Ferramentas de Desenvolvimento – Permite executar comandos do EF Core no terminal, como:
   - Criar migrations
   - Aplicar migrations ao banco
   - Reverter migrations
   - Gerar código a partir de um banco existente

- Instalar o EntityFrameworkCore.Tools

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/08_EntityCoreTools.png"/>

# Qual a função do EntityFrameworkCore.Tools?
 
O pacote Microsoft.EntityFrameworkCore.Tools adiciona suporte a comandos do Entity Framework Core (EF Core) no .NET CLI e no Package Manager Console (PMC) do Visual Studio. Ele é essencial para gerenciar migrations, atualizar o banco de dados, gerar código a partir de um banco existente e outras tarefas automatizadas.

### Aqui terminamos de instalar as dependencias necessárias.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Após a instalação das dependencias vamos retornar ao desenvolvimento da AppDbContext.cs

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/10_AppDbContext.png"/>

## 📌 O que esse código faz?

Ele define um contexto de banco de dados para uma aplicação ASP.NET Core usando Entity Framework Core (Ef Core).

O AppDbContext é responsável por gerenciar as operações com o banco de dados e mapear as classes AutorModel e LivroModel para tabelas no banco de dados.

## 📌Detalhamento do código

1️⃣ <b>Namespaces Importados</b>

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/11_BibliotecasCSharp.png"/>

- using Microsoft.EntityFrameworkCore; → Importa a biblioteca Entity Framework Core, que permite trabalhar com bancos de dados usando código C#.
- using WebAPI8_Video.Models; → Importa os modelos (AutorModel, LivroModel) que representam tabelas do banco de dados.

2️⃣ <b>Definição da Classe AppDbContext</b>

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/12_Context_BancoDados.png"/>

- namespace WebAPI8_Video.Data; → Define um espaço de nomes para organizar a estrutura da aplicação.
- public class AppDbContex : DbContext → Cria a classe AppDbContex, que herda de DbContext (classe base do EF Core).

  - Essa classe atua como um intermediário entre aplicação e banco de dados.
 
 

# Code First 

O modelo Code First é uma abordagem de desenvolvimento em que o código-fonte é a base para a criação e manutenção do banco de dados. Ou seja, primeiro você escreve as classes e modelos no código e, a partir deles, o esquema do banco de dados é gerado automaticamente.

### Como funciona o Code First?

#### 1. Definição do modelo

- O desenvolvedor cria classes que representam as entidades do banco de dados (como tabelas).

#### 2. Mapeamento para o banco

- Um ORM (Object-Relational Mapping) traduz essas classes para tabelas no banco de dados.

#### 3. Migrações

- Quando há mudanças no modelo, o banco é atualizado por meio de migrações, sem a necessidade de modificar o esquema diretamente.

# Quais linguagens utilizam Code First?

Várias linguagens e frameworks adotam essa abordagem, principalmente aquelas que trabalham com ORMs. Aqui estão algumas das principais:

#### 1. C# + Entity Framework

- No Entity Framework Core (EF Core), a abordagem Code First é muito popular.
- O desenvolvedor cria classes em C#, e o EF Core gera o banco com base nelas.

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/09_Code_First.png"/>

- A partir desse código, o EF Core cria a tabela Produto no banco de dados.

 
- 53:49
