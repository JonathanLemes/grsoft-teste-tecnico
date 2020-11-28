# Front-End

Como já citado, o Front-End da aplicação foi desenvolvido com o framework <a href="https://reactnative.dev/">React Native</a>, que utiliza dos componentes nativos da plataforma que se encontra para um melhor desempenho e estilização. Contudo, os testes foram feitos apenas em dispositivos Android, o que torna possível algumas falhas na estilização da plataforma iOS (facilmente corrigidas por leves ajustes de valores).

Após planejado o design no <a href="https://www.figma.com/file/auUufEiyCGwfAVO2QK505I/Projeto-GRSoft?node-id=0%3A1">Figma</a>, a estilização ficou por parte do *StyleSheet* do próprio *React Native*, o que, apesar de não ser facilmente manipulável como a *lib Styled-Components* (que adapta o CSS comum em browser para o *React Native*), evita possíveis erros da adaptação destes códigos.

Para executar o código Front-End, leia a aba <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico#execu%C3%A7%C3%A3o">*Execução*</a> do arquivo <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico#grsoft-teste-t%C3%A9cnico">README.md</a> principal.

---

## Routes

Conforme dito na <a href="https://github.com/JonathanLemes/grsoft-teste-tecnico/tree/main/docs/Back-End.md">documentação do Back-End</a>, a autenticação é realizada via token JWT (armazenando-o quando executado localmente). Por este motivo, as rotas foram reparadas na pasta */src/routes*. A rota da autenticação navega entre as telas *Landing*, *SignIn* e *SignUP*, sem colidir com a rota principal do app, que o usuário só tem acesso com um token JWT válido para o servidor.

Após validado o token, o arquivo <a href="https://github.com/JonathanLemes/grsoft-teste-mobile/blob/master/src/routes/index.tsx">*/src/routes/indes.tsx*</a> altera a rota do usuário para a principal, descartando a rota de autenticação caso o usuário execute o app novamente.
>**Nota:** como já citado, a rota de autenticação só pode ser descartada caso o usuário armazene o token JWT localmente, o que não é possível com a execução via *Expo Cloud*.

---

## React Context API

Tanto o framework *React.JS* quanto o *React Native* disponibilizam uma API local para a troca de informações entre todas as instâncias de suas aplicações, chamada de <a href="https://pt-br.reactjs.org/docs/context.html">*Context API*</a>. Esta API, localizada na pasta <a href="https://github.com/JonathanLemes/grsoft-teste-mobile/tree/master/src/contexts">*/src/contexts*</a>, foi instanciada tanto para a comunicação com a API REST quanto para cálculos dinâmicos dos valores de tamanho de acordo com a tela do usuário.
>**Nota:** Os cálculos são feitos pelo fato de que o *StyleSheet* do *React Native* suporta apenas valores absolutos, e são feitos de acordo com o *pixel ratio* da tela do usuário.

A maior vantagem de utilizar a *Context API* para comunicação com a API REST é o fato de passar a responsabilidade da comunicação para um arquivo global, separando a regra de negócios e diminuindo possíveis falhas em pontos diferentes do código. Neste caso, a responsabilidade de comunicação com a API REST está no arquivo <a href="https://github.com/JonathanLemes/grsoft-teste-mobile/tree/master/src/contexts/apiContexts.tsx">*/src/contexts/apiContexts.tsx*</a>, que é apenas referenciado nos arquivos que necessitam de seus dados globais por meio do React Hook *useContext*.

[![Print_tela_produtos](https://i.ibb.co/n0xNQRS/5-Products-page.png)](https://expo.io/@jonathanfillipe/projects/grsoft-teste-mobile)

---

### Feito por: Jonathan Fillipe Lemes