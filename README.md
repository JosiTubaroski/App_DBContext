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

 3️⃣ <b> Construtor da Classe </b>

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/13_ConstrutorClasse.png"/>

 - public AppDbContex(DbContextOptions<AppDbContex> options)

   - O construtor recebe um objeto DbContextOptions<AppDbContex>, que contém configurações do banco de dados, como o provedor (SQL Server, SQLite, etc.) e a string de conexão.

 - : base(options)

   - Passa as opções para o construtor da classe base (DbContext), garantindo que o EF Core use essas configurações corretamente.

 4️⃣ <b> DbSets (Tabelas do Banco) </b>

 <img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/14_DbSet.png"/>

 - DbSet<AutorModel> Autores → Representa a tabela Autores no banco de dados.
 - DbSet<LivroModel> Livros → Representa a tabela Livros no banco de dados.
 - O DbSet<T> permite executar operações CRUD (Create, Read, Update, Delete) no banco.

## 📌 Resumo

- ✔ AppDbContex é o intermediário entre a aplicação e o banco de dados.
- ✔ Ele usa DbSet<T> para representar tabelas no banco.
- ✔ O construtor recebe opções de configuração (como o tipo de banco e string de conexão).
- ✔ Ele é registrado no DI e usado nos Controllers para acessar os dados.

# O que é um contexto de banco de dados para uma aplicação ASP.NET?

O <b>contexto de banco de dados</b> em uma aplicação <b>ASP.NET Core</b> utilizando <b>Entity Framework Core (EF Core)</b> é uma <b>classe que gerencia a conexão</b> entre a aplicação e o banco de dados.

Essa classe é responsavel por:

- ✔ Configurar a conexão com o banco de dados (ex.: SQL Server, MySQL, SQLite).
- ✔ Definir quais tabelas a aplicação irá manipular (via DbSet<T>).
- ✔ Executar operações CRUD (Create, Read, Update, Delete).
- ✔ Aplicar migrações e mapear classes para tabelas no banco (ORM - Object Relational Mapping).

# 📌 Como funciona um contexto de banco de dados?

No Entity Framework Core, o contexto de banco é uma classe que herda de DbContext, que é a classe base para interação com o banco.

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/15_Heran%C3%A7a.png"/>

📌 Explicação do código acima:

1. Herdamos de DbContext → AppDbContext : DbContext.
2. Definimos um construtor que recebe as opções do contexto.
3. Criamos propriedades DbSet<T>, que representam tabelas no banco de dados.

# O que são construtores de classes no ASP.NET?

No <b>ASP.NET Core</b>, um construtor é um método especial que é executado automaticamente quando um objeto de uma classe é criado. Ele serve para <b>inicializar propriedades e configurar dependências</b> da classe.

Construtores são usados tanto em Controllers, Services, Contextos de Banco de Dados, e outras partes da aplicação.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 📌 O que são Models no ASP.NET Core?

No ASP.NET Core, as Models(ou Modelos) são classes que representam dados e a lógica de negócio da aplicação. Elas são responsáveis por definir como os dados serão estruturados, armazenados e manipulados.

As <b>Models</b> fazem parte do Padrão MVC(Model-View-Controller) e são usadas tanto em APIs quanto em aplicações web.

#📌 Para que servem as Models?

- ✔ Definir a estrutura dos dados que serão manipulados na aplicação.
- ✔ Interagir com o banco de dados quando usadas com Entity Framework Core (EF Core).
- ✔ Validar os dados antes que sejam processados.
- ✔ Mapear objetos para JSON em APIs REST.

# 📌 Resumo

✅ Models são classes que representam dados e regras de negócio.
✅ Elas são usadas pelo Entity Framework Core para mapear tabelas do banco.
✅ As Models são validadas usando Data Annotations ([Required], [MaxLength], etc.).
✅ Controllers usam Models para manipular os dados e criar APIs.

# 📌 O que é o padrão MVC (Model-View-Controller)?

O MVC (Model-View-Controller) é um padrão de arquitetura de software usado para organizar a estrutura de aplicações web. Ele separa a aplicação em <b>três camadas principais</b>:

1️⃣ <b>Model (Modelo)</b> - Gerencia os dados e a lógica de négocios
2️⃣ <b>View (Visão)</b> - Responsável pela interface com usuário
3️⃣ Controller (Controlador) – Atua como intermediário entre Model e View.

O ASP.NET Core MVC usa esse padrão para criar aplicações web e APIs organizadas e escaláveis.

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

### Criando as Models da Aplicação.

## 1) AutorModel.cs

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/16_AutorModels.png"/>

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/17_AutorModelCodigo.png"/>

# Detalhando o Código

### 📌 1. Importação de Biblioteca

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/18_Importacao_Biblioteca.png"/>

- ✔ System.Text.Json.Serialization → Essa biblioteca permite customizar a serialização JSON no .NET.
- ✔ Ela é usada para ignorar, formatar ou modificar como os objetos são transformados em JSON.

### 📌 2. Definição da Classe AutorModel

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/19_Models.png"/>

- ✔ namespace WebAPI8_Video.Models → Define o espaço de nomes onde essa classe pertence.
- ✔ Ele agrupa classes relacionadas (neste caso, Modelos da aplicação).

### 📌 3. Declaração da Classe AutorModel

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/20_ClasseModels.png"/>

- ✔ Define a classe AutorModel, que representa um autor dentro do sistema.
- ✔ Essa classe será usada para armazenar e manipular informações de autores no banco de dados.

### 📌 4. Propriedades da Classe

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/21_PropriedadeClasseAutor1.png"/>

- ✔ Id → Identificador único do autor (chave primária no banco de dados).

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/22_Propriedade_2.png"/>

- ✔ Nome → Nome do autor (ex: "Machado").

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/23_Propriedade_3.png"/>

- ✔ Sobrenome → Sobrenome do autor (ex: "de Assis").

### 📌 Conclusão

<p>✅ AutorModel representa um autor, com Id, Nome e Sobrenome.</p>
<p>✅ Livros é uma lista que armazena os livros escritos por esse autor.</p>
<p>✅ [JsonIgnore] evita que a lista de livros apareça na serialização JSON.</p>
<p>✅ Isso é útil para evitar circularidade e melhorar a performance das respostas da API.</p>

## 2) LivroModel.cs

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/24_LivroModels.png"/>

## Detalhamento do Código

1. Namespace (WebAPI8_Video.Models)

   - O código define um namespace chamado WebAPI8_Video.Models.
   - Namespaces servem para organizar e estruturar as classes dentro de um projeto, evitando conflitos de nome entre diferentes partes do código.
  
2. Classe LivroModel

   - A classe LivroModel representa um modelo de dados para um livro.
   - É comum em aplicações ASP.NET Core Web API utilizar classes como essa para representar os dados que serão armazenados, manipulados e expostos via API.

3. Propriedades da classe LivroModel

   - public int Id { get; set; }
     - Identificador único do livro (chave primária).
     - Tipo int, usado para identificação numérica de registros no banco de dados.
    
   -  public string Titulo { get; set; }
      - Armazena o título do livro.
      - Tipo string, pois representa um texto.
    
   - public AutorModel Autor { get; set; }
     - Representa um objeto da classe AutorModel, indicando que cada livro tem um autor.
     - Essa é uma relação de composição onde um livro possui um autor.
    
 4. Dependência de AutorModel

    - AutorModel não está definido no código fornecido, mas pelo nome podemos supor que seja uma classe que representa um autor de livros.
    - O relacionamento entre LivroModel e AutorModel indica que um livro possui um autor.
    - Provavelmente a classe AutorModel é definida em outro arquivo dentro do mesmo namespace (WebAPI8_Video.Models).

### 📌 Criando a string de conexão - Arquivo appsenttings.json

<img src="https://github.com/JosiTubaroski/App_DBContext/blob/main/img/25_App_Setings_Json.png"/>




 
- 53:49
