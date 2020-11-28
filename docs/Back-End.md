# Back-End

Como já citado, a API do Back-End foi desenvolvida com o framework <a href="https://expressjs.com/pt-br/">Express.JS</a>, o framework back-end de Node.JS mais utilizado atualmente para desenvolvimento de APIs.

Para uma melhor organização do código, foi utilizado o Design Pattern <a href="https://pt.wikipedia.org/wiki/MVC">MVC</a> (<a href="https://github.com/JonathanLemes/grsoft-teste-backend/tree/main/src/models">Model</a>, <a href="https://github.com/JonathanLemes/grsoft-teste-backend/tree/main/src/views">View</a>, <a href="https://github.com/JonathanLemes/grsoft-teste-backend/tree/main/src/controllers">Controller</a>), organizado pelas pastas do <a href="https://github.com/JonathanLemes/grsoft-teste-backend/tree/main/src/">/src</a>. Apesar disto, a autenticação e seus Controllers ficaram separadas na pasta <a href="https://github.com/JonathanLemes/grsoft-teste-backend/tree/main/src/auth">/src/auth</a>.

## Banco de dados

### Design

Conforme solicitado, o banco de dados principal foi criado através de MySQL. O banco planejado contém quatro tabelas: *Users*, *Categories*, *Products* e a *RELATION_Categories_Products*, responsável pela relação *n:m* das tabelas *Categories* e *Products*. O banco foi hospedado em um servidor <a href="https://devcenter.heroku.com/">Heroku</a>, como pode ser visto no arquivo *ormconfig.json*.

O Design do banco foi bem simples, seguindo a imagem:

![DB_Design](https://i.ibb.co/Ct1nF4B/db-design.png)
>**Nota:** Os dados *Categories.url* e *Users.email* são *Unique*.

Apesar da tabela *Products* conter o campo *description*, eu optei por não utilizar a descrição no Front-End por questões de UI.

### ORM (Object Relational Mapping)

Para uma melhor abstração do banco de dados (além da fácil adaptação para outros tipos de bancos), utilizei o <a href="https://typeorm.io/">TypeORM</a>. O TypeORM asbtrai o código para a syntax do JavaScript, tornando a alteração para qualquer banco que o mesmo suporta (MySQL / MariaDB / Postgres / CockroachDB / SQLite / Microsoft SQL Server / Oracle / SAP Hana / sql.js) ocorrendo apenas através da alteração do arquivo *ormconfig.json*.

A criação de tabelas foi feita através de <a href="https://typeorm.io/#/migrations">*Migrations*</a> via *queryRunner* em conjunto com o *TypeORM/Table*, limitando sua criação e exclusão a comandos simples de terminal, sem necessitar da mudança das *queries* (o que ocorreria pela criação padrão de *queryRunner.query()*).

## API REST Express.JS

A API REST do Express.JS foi planejada para o cadastro de cada um dos dados, além das *queries* seleção para a recuperação dos dados. O servidor é criado via *ts-node-env* pela execução do arquivo <a href="">*server.ts*</a> e as rotas executadas pelo <a href="">routes.ts</a>. As rotas redirecionam cada requisição para o Controller responsável.

Por questões de segurança e seguindo o padrão de aplicativos maiores, a API REST está hospedada em um servidor Heroku diferente do Banco de Dados, com as rotas sendo acessadas através da url base <a href="https://fast-mountain-02347.herokuapp.com/">https://fast-mountain-02347.herokuapp.com/</a> (*ex.: https://fast-mountain-02347.herokuapp.com/categories*).

## Autenticação JWT

Assim como as maiores aplicações atuais (*ex.: Facebook*), o login é feito pela geração e autenticação de um token JWT. Através do token JWT, o usuário pode loggar apenas no primeiro acesso ao app, mantendo este dado armazenado localmente para próximos acessos, sem necessitar a troca de dados sensíveis (e-mail e senha) enquanto o token não expirar. 

Infelizmente, o servidor utilizado para a hospedagem do Front-End não dá suporte para o armazenamento local do token (ao menos em seu plano gratuito), mas ao rodá-lo localmente, apenas o primeiro login é necessário, o que comprova a eficácia do JWT. Seu funcionamento pode ser visto nos arquivos <a href="https://github.com/JonathanLemes/grsoft-teste-backend/blob/main/src/auth/authController.ts">*authController.ts*</a> e <a href="https://github.com/JonathanLemes/grsoft-teste-backend/blob/main/src/auth/authMiddleware.ts">*authMiddleware.ts</a>*

## TDD (Test-Driven Development)

O código possui uma rotina de teste automatizada. A rotina de testes foi através da *lib* <a href="https://jestjs.io/">Jest</a>, em conjunto com a <a href="https://github.com/visionmedia/supertest#readme">Supertest</a>. Para executar a rotina, basta rodar o comando:

```bash
yarn test
```

Basicamente, os testes executam separadamente cada tipo de rota da API REST (POST, GET, DELETE), totalizando três testes. O resultado é retornado no próprio terminal.

Visto que não é recomendada a utilização do banco de dados de produção para os testes, optei por criar temporariamente um banco SQLite, exatamente por não precisar separar portas, hosts ou usuários. O banco criado é armazenado em */tests/unit/database.sqlite*. Caso os testes funcionem no banco temporário, pela utilização do TypeORM, são descartados problemas no código da API REST.

---

### Feito por: Jonathan Fillipe Lemes