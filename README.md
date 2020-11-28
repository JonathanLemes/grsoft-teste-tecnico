# GRSoft-Teste-Técnico
Teste técnico para a empresa GRSoft

[![Print_tela_principal](https://i.ibb.co/SXgyHyj/Designpng.png)](https://expo.io/@jonathanfillipe/projects/grsoft-teste-mobile)

---

## Execução

O app foi feito utilizando como base o framework <a href="https://docs.expo.io/">*Expo*</a>, para facilitar o *deploy* em nuvem. Dito isso, é necessário o download do app *Expo* para executar nativamente tanto em <a href="https://play.google.com/store/apps/details?id=host.exp.exponent&hl=pt_BR&gl=US">*Android*</a> quanto <a href="https://apps.apple.com/br/app/expo-client/id982107779">*iOS*</a>.

### Expo Cloud

Para executar no Expo Cloud, basta abrir o app Expo no seu celular e ler o QR Code projeto no site Expo.io, que pode ser acessado <a href="https://expo.io/@jonathanfillipe/projects/grsoft-teste-mobile">clicando aqui</a>.

### Localmente

Caso queira executar o projeto em sua máquina local (recomendável para ver o funcionamento da <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico/blob/main/docs/Back-End.md#autentica%C3%A7%C3%A3o-jwt">autenticação JWT</a>), será necessário clonar o repositório <a href="https://github.com/JonathanLemes/grsoft-teste-mobile/">grsoft-teste-mobile</a>.

```bash
git clone https://github.com/JonathanLemes/grsoft-teste-mobile.git
cd ./grsoft-teste-mobile
```

Certifique-se que você tem instalado em sua máquina o <a href="https://nodejs.org/en/download/">Node.JS</a> o gerenciador de pacotes <a href="https://classic.yarnpkg.com/pt-BR/docs/install/#windows-stable">Yarn</a> e o <a href="https://docs.expo.io/#quick-start">Expo-CLI</a> (instalado obrigatoriamente após o Node.JS).

Após clonar o repositório e navegar para a pasta criada através do terminal, instale todas as dependências do projeto.

```bash
yarn install
```

Por fim, execute o Expo.

```bash
expo start
```

Acessando a porta <a href="http://localhost:19002/">19002</a> do seu navegador durante a execução do Expo, você terá acesso à Expo Developer Tools. Nesta dashboard, o app pode ser executado nativamente através do app Expo em seu celular com a leitura do QR Code do canto inferior esquerdo da tela.

---

## Detalhes do desafio

- Criar uma interface em React Native:
  1. Tela de Login.
  2. Tela listando Categoria de Produtos.
  3. Tela listando Produtos conforme a categoria escolhida na tela anterior.
  
- Usar MySQL no servidor com uma API em Node.JS.
- Upar isso em um servidor web.

- O sistema deverá funcionar seguindo os passos abaixo:
  1. Na tela inicial temos Splash apresentando o sistema.
  2. Ao logar sendo validado será redirecionado a tela de categorias de produtos.
  3. Ao clicar em uma categoria o usuario deverá ser conduzido a tela listando produtos.
 
- Documentar a API informando os endpoints.

Prazo estimado para entrega até a proxima segunda-feira dia 30/11/2020.

---

## Desenvolvimento

O primeiro passo para a criação do app foi o design. Todo o planejamento foi feito através do <a href="https://www.figma.com/">Figma</a> e pode ser acessado <a href="https://www.figma.com/file/auUufEiyCGwfAVO2QK505I/Projeto-GRSoft?node-id=0%3A1">clicando aqui</a>.

Seguindo o desafio, decidi separar o código em dois repositórios distintos, sendo um para o Back-End com uma API em <a href="https://expressjs.com/pt-br/">Express.JS</a> e o outro para o Front-End em <a href="https://reactnative.dev/">React Native</a>.

1. <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico/tree/main/docs/Back-End.md">Documentação do Back-End</a>.
2. <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico/tree/main/docs/Front-End.md">Documentação do Front-End</a>.

---

## Versionamento

Obviamente, o versionamento do código foi feito via Git, mas vale citar a utilização do *Commitzen*, juntamente com o <a href="https://github.com/commitizen/cz-cli">*cz-cli*</a>. Desta forma, todos os *commits* são padronizados, seguindo boas práticas de programação e versionamento, úteis principalmente em casos de grandes equipes trabalhando em um mesmo código.

---

### Feito por: Jonathan Fillipe Lemes

<!--<a href="https://ibb.co/KL7SxKJ"><img src="https://i.ibb.co/TbRdMWs/1-Landing-page.png" alt="1-Landing-page"></a>
<a href="https://ibb.co/DCPhHgM"><img src="https://i.ibb.co/wWZVFrQ/2-Sign-In-page.png" alt="2-Sign-In-page"></a>
<a href="https://ibb.co/LJKr9bV"><img src="https://i.ibb.co/hZ0c2h3/3-Sign-Up-page.png" alt="3-Sign-Up-page"></a>
<a href="https://ibb.co/Dg3kWn0"><img src="https://i.ibb.co/R4LPbWR/4-Categories-page.png" alt="4-Categories-page"></a>
<a href="https://ibb.co/8B1LPXV"><img src="https://i.ibb.co/n0xNQRS/5-Products-page.png" alt="5-Products-page"></a>
<a href="https://ibb.co/n0gDS4r"><img src="https://i.ibb.co/Ct1nF4B/db-design.png" alt="db-design"></a>
<a href="https://ibb.co/Z6rXvXj"><img src="https://i.ibb.co/SXgyHyj/Designpng.png" alt="Designpng"></a>-->