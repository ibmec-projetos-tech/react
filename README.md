# React

## Conceitos iniciais do React

**_React_** surgiu através de uma necessidade do **Facebook**, onde o código era grande e de difícil manutenção. Por isso as pessoas engenheiras do Facebook precisaram pensar em uma solução escalável e eficiente, nessa necessidade nasceu o **_React_**.
Com o tempo essa tecnologia se tornou open-source, conquistou muitos adeptos e grandes empresas passaram a utilizá-la.

O **_React_** é, atualmente, uma das principais bibliotecas `Javascript` para construção de interfaces de usuário. Esta poderosa ferramenta foi criada pelos times de desenvolvimento do **Facebook** com objetivo de organizar, componentizar e, consequentemente, tornar muito mais eficiente cada parte das aplicações que a utilizam.

A ideia principal é tornar possível dividir a sua aplicação em pequenos blocos, reutilizáveis ou não, que podem fazer a gestão das suas próprias informações através do seu estado, ou seja, reagir a eventos, interações, dados, etc. Toda vez que houver uma mudança em um componente, o **_React_** atua especificamente na renderização dele, sem que seja necessário atualizar os outros blocos.

A componentização permite ainda utilizar funções específicas, estilizações, testes e outras tecnologias no exato local em que ela será utilizada, permitindo que qualquer possível refatoração do código se torne mais simples, bem endereçada e fácil de se encontrar.

O exemplo mais prático de uma aplicação **_React_** é a própria [documentação](https://legacy.reactjs.org/) dela. Além de ser possível visualizar as principais componentizações, como header, menu lateral, conteúdo principal, barra lateral, submenus e footer, conseguimos acessar menus diferentes sem que a página recarregue. Super eficiente, certo? Existem diversas outras ferramentas, como o próprio Facebook e o Slido, que funcionam da mesma forma dinâmica.

# Criando uma aplicação React

Para criar uma aplicação **_React_**, precisaremos primeiro relembrar o conceito de gerenciadores de pacotes.

O gerenciador de pacotes que utilizamos nas nossas aplicações é o **NPM**. Ele é o responsável por instalar e gerenciar as versões dos pacotes que utilizamos nas nossas aplicações. Portanto, usaremos ele para instalar os pacotes no nosso projeto.

Podemos também utilizar o **NPX** para **executar** o comando de um pacote, sem instalá-lo diretamente.

Para criarmos nossas aplicações _React_ , utilizaremos o pacote `create-react-app`. Como ele é um pacote que tem como função a criação de todos os arquivos necessários para termos uma aplicação _React_, não precisamos instalá-lo. Desta forma, criaremos ela executando o seguinte comando no terminal:

```bash
npx create-react-app nome-da-aplicacao
```

Após o NPX terminar de executar, perceba que um novo diretório foi criado com o nome da aplicação que você utilizou ao executar o comando acima, contendo todos os arquivos necessários de uma aplicação _React_.

Além disso, o terminal irá apresentar alguns comandos iniciais para começarmos a trabalhar na nossa aplicação:

|![Imagem que demonstra os comandos básicos do npm para usar o create-react-app](img/npm-commands.png)|
|:--:|
| Imagem que demonstra os comandos básicos do npm para usar o create-react-app |

Perceba que ele sugere a você acessar o diretório criado e executar o comando `npm start`.

```bash
cd nome-da-aplicacao
npm start
```

O comando `npm start` é um `script` predefinido pelo _React_ que inicia o servidor da sua aplicação. Utilizando esse comando, uma nova página deverá abrir no seu navegador, contendo a sua aplicação. Se você seguiu os passos até aqui, algo parecido com o exemplo abaixo deverá aparecer na sua tela, o que significa que tudo está funcionando corretamente.

|![Imagem que demonstra que tudo funciona corretamente, mostrada no navegador](img/all-done.png)|
|:--:|
| Imagem que demonstra que tudo funciona corretamente, mostrada no navegador |

# JSX

O `JSX`, ou `Javascript Syntax Extension`, como o próprio nome sugere, é uma extensão de sintaxe para Javascript. Sua utilização é recomendada pela documentação do React, pois ela demonstra como a interface deverá se comportar, de forma lógica e descritiva.

Vamos ver um exemplo:

```jsx
const element = <h1>Hello, world!</h1>;
```

> ⚠️ **Atenção** ⚠️
>
> Os códigos com a sintaxe JSX só funcionam dentro do contexto do React, ou seja, não funcionam em JS puro ou rodando diretamente no console do navegador, por exemplo. Você pode brincar com o JSX em exemplos interativos do [CodeSandbox](https://codesandbox.io/s/new?file=/src/App.js) que aparecem no conteúdo ou em scripts `.js` ou `.jsx` que importam o React em projetos criados pelo comando `npx create-react-app`.

A construção de um elemento JSX é bem parecida com um elemento HTML, com pequenas diferenças para que não haja conflito do HTML com o JS. Um exemplo disso é a declaração de uma `class` no HTML, que é substituída por `className` no JSX, pois haveria conflito de sintaxe com as classes do JS.

Caso fossemos declarar a mesma variável sem o JSX, precisaríamos utilizar funções como o `createElement` que recebe como parâmetro um componente, um objeto com as `props` e o conteúdo que será encapsulado por este componente. Seriam necessárias sequências relativamente longas de instruções de código para conseguirmos montar e manipular uma árvore de componentes. Para visualizarmos essa complexidade, vamos refazer o código acima sem o JSX:

```jsx
const element = React.createElement('h1', null, 'Hello, world')
```

Agora imagine uma aplicação inteira sendo construída dessa forma. Ficaria muito mais difícil de ser compreendida, certo? O JSX encaixa-se perfeitamente para resolver este dilema.

É importante frisar que o uso do JSX em aplicações React não é obrigatório, mas a complexidade da construção de uma aplicação fica menor e o código fica mais intuitivo quando o utilizamos.

## Incorporando expressões no JSX

Por ser um código Javascript, o JSX permite injeções de algoritmos dentro da estrutura HTML. Portanto, é possível que se aplique diretamente na estrutura da aplicação códigos que renderizarão outras diversas expressões, por exemplo:

```jsx
const nome = 'Jorge Maravilha';
const element = <h1>Hello, {nome}</h1>;
```

E se aprofundarmos um pouco mais chamando uma função na nossa constante element?

```jsx
function nomeCompleto (nome, sobrenome) {
  return `${nome} ${sobrenome}`;
}

const element = <h1>Hello, {nomeCompleto('Jorge', 'Maravilha')}</h1>;
```

Agora, vamos incorporar a nossa constante `element` na função `helloWorld`, retornar um código JSX e encapsulá-la em uma `div`:

```jsx
function helloWorld (nome, sobrenome) {
  return <h1>Hello, {`${nome} ${sobrenome}`}</h1>;
}

const element = helloWorld('Jorge', 'Maravilha');
const container = <div>{element}</div>;
```

No JSX é necessário substituir `class` por `className`, para evitar conflitos entre o `Javascript` e o `HTML`, mas também podemos utilizar expressões `Javascript` para atribuir valor à este atributo.

```jsx
const nome = 'Jorge Maravilha';
const classe = 'hello-class';
const element = <h1 className={classe}>Hello, {nome}</h1>;
```

# ReactDOM

O `ReactDOM` é o responsável por renderizar e atualizar seu código dentro do **_HTML_**, exibindo assim seus elementos `React`.

Para entendermos como ele funciona, podemos ou criar um novo projeto `React` usando o `create-react-app` ou usar o projeto criado na seção inicial.

Feito a escolha, vamos abrir o projeto e procurar pelo arquivo `index.js`. 
>Esse é o arquivo raiz das nossas aplicações React e é nele que fazemos o vínculo dos nossos componentes React com o DOM do navegador, utilizando o ReactDOM.

Ao utilizar o React, a forma como manipulamos os elementos vai mudar. Inclusive, é considerado uma **_má prática_** manipular o DOM no _React_ diretamente como no JavaScript puro. Com isso, não vamos mais utilizar as funções que manipulam o DOM, tais como: `appendChild`, `removeChild`, `querySelector`, etc.

>No JavaScript puro é possível pegar os elementos via _querySelector_, por exemplo, e com algum _addEventListener_ escutar um evento, chamar uma função e atribuir ou mudar uma propriedade desse elemento.

Agora, você pode estar se perguntando: Como fazemos para, por exemplo, mudar o estilo de elementos se não podemos manipular o DOM diretamente usando o React?

Resposta: No _React_ cada componente pode receber um conjunto de informações (chamadas de _props_), ou ter informações contidas internamente (chamadas de _estado_). Toda vez que qualquer uma dessa informações for atualizada, a função `ReactDOM.render` irá aplicar as mudanças necessárias e o DOM será atualizado automaticamente.

Aviso:Aprenderemos mais sobre `props` e `estado`! Por ora, basta você saber que o _React_ tem uma forma própria de atualizar a DOM e que nós ainda vamos estudar _MUITO_ sobre isso ;)

Talvez você possa ter a sensação inicial de que é mais fácil fazer tudo isso com JavaScript puro, mas com o andar do módulo e do curso, você verá que o uso do _React_ vai simplificar, e muito, sua vida tornando os projetos , que seriam extremamente complexos com JavaScript puro, mais aceitáveis com _React_.

# CSS e Import

Para importar um arquivo que está dentro do próprio projeto ou que esteja em uma biblioteca externa, você pode utilizar o `import`, com a seguinte sintaxe:

```jsx
import myImport from 'file';
```

Onde o `myImport` é a variável pela qual você acessará o módulo importado. Caso você queira importar algo que não seja a exportação _default_, será necessário colocar o nome do que está sendo importado entre chaves:

```jsx
import { myImport } from 'file';
```

A origem do arquivo importado é indicada após o `from`, e pode ser um caminho relativo ou o nome da biblioteca que foi instalada no projeto:

```jsx
import React from 'react' // importando de uma biblioteca
import Header from './components/Header.js' // importando de um caminho relativo
```

A utilização de CSS (estilização) em componentes React não é nada muito diferente de como é feito no `HTML`, você deve criar um arquivo para manter todo o seu `CSS` e então deverá importá-lo onde você deseja utilizá-lo e colocar as `classes` e `ids` que você criou nos elementos da sua página.

Para facilitar o entendimento veja o exemplo abaixo:

```css
/* App.css */
.App {
  background-color: #282c34;
  text-align: center;
}
```

```jsx
// App.js
import React from 'react';
import './App.css';

function App() {
  return (
    <div className='App'>
      <h1>APP</h1>
    </div>
  );
}

export default App;
```

# Criando o primeiro componente React

O React nos permite criar uma tela com um conjunto de diferentes peças reutilizáveis e com lógica isolada: **os componentes**.

Esses componentes podem ser criados de duas formas: mediante funções ou com a criação de classes - uma das inovações trazidas pelo ES2015 (ES6). As classes surgiram como um "açúcar sintático" sobre funções, dando a possibilidade de criar novos objetos.

Você pode se aprofundar mais nesses conceitos acessando a [documentação oficial sobre classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).

> Em ciência da computação, o termo _"açúcar sintático"_ se refere ao conceito de tornar uma construção mais simples de ser lida e compreendida. Você pode encontrar mais sobre esse conceito [aqui](https://pt.wikipedia.org/wiki/A%C3%A7%C3%BAcar_sint%C3%A1tico).

## Componentes de classe

Você pode pensar que uma classe e uma função são exatamente a mesma coisa, afinal, ambas recebem atributos, e nós as chamamos em seguida. Porém, uma classe pode possuir `métodos`, que nada mais são do que ações que toda entidade criada a partir de uma classe pode realizar.

Em `React`, classe é uma das formas de renderizar os componentes na página. Então, quando um componente precisa ser alterado, utilizamos componentes de classe, para que possamos utilizar seus estados para realizar essas alterações.

Podemos atribuir vários `métodos`, os quais podem, inclusive, alterar o próprio estado do objeto. Por enquanto, só precisamos saber que `métodos` existem e não precisamos nos preocupar, pois veremos com detalhes os `métodos de classe` mais adiante em `React`, junto com `estado da aplicação`.

Mas não se preocupe, pois você verá isso em breve, com muito mais detalhamento.

<iframe src="https://player.vimeo.com/video/455999516" width="640" height="360" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

A principal diferença entre o uso de componentes por classe e o uso de componentes por função reside no fato de aqueles gerados por classe terem acesso a métodos e ao estado próprios de qualquer componente React gerado via classe, como o método `render()`, que te permite renderizar todo o conteúdo criado na tela, os quais são acessíveis somente por componentes criados por classe na maior parte das versões do React. A sintaxe para criar um componente com classes é a seguinte:

```jsx
import React from 'react';

class ReactClass extends React.Component {
  render() {
    return (
      <h1>My first React Class Component!</h1>
    )
  }
}
```

<iframe src="https://player.vimeo.com/video/456001191" width="640" height="360" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
