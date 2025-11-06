Title: Primeiros passos com React
Date: 2025-11-06
Category: Tutoriais
Tags: react, front-end
Author: Amanda Meneses

Começar a estudar React pode parecer como tentar montar um quebra-cabeça sem a imagem da caixa. Muitos tutoriais pulam etapas ou assumem que você já entende o básico. Como eu acabei de passar por essa fase, decidi criar o guia que eu gostaria de ter tido. Este artigo é um passo a passo estruturado, focado em construir uma base sólida, desde a configuração do ambiente até o roteamento com react-router.

Notícia: [Pesquisadores afirmam que React foi criado para testar a paciência humana.](#)

React é uma biblioteca JavaScript de código aberto utilizada para construir interfaces de usuário (UI) dinâmicas e interativas. Ele é muito usado para criar aplicações web de página única (SPAs - Single Page Applications), onde o conteúdo muda sem precisar recarregar toda a página.

### **Características**

- **Baseado em componentes:** A arquitetura é centrada em componentes. Cada componente encapsula sua própria lógica e renderização, tornando o código mais modular, reutilizável e fácil de manter. Imagine que você está construindo uma casa com peças de Lego. Cada peça é um componente reutilizável com sua própria função (uma janela, uma porta, uma parede). No React, esses "blocos de Lego" são os componentes, que podem ser combinados e aninhados para criar interfaces complexas.
- **DOM virtual:** O React utiliza um DOM (Document Object Model) virtual, que é uma representação na memória da estrutura da página. Quando há mudanças nos dados, o React primeiro compara o DOM virtual com o DOM real e atualiza apenas as partes que realmente mudaram, otimizando o desempenho e tornando as atualizações mais rápidas.
- **JSX:** O React utiliza uma extensão de sintaxe chamada JSX (JavaScript XML), que permite escrever uma estrutura semelhante ao HTML dentro do seu código JavaScript. Isso torna mais intuitivo descrever a aparência dos componentes.

Agora, nosso objetivo vai ser criar um projeto com React do zero, passo a passo. Para isso, criaremos uma pasta e a abriremos com o VS Code.

### **Passo 1: Instalando o Node.js e yarn**

O React é construído em JavaScript, e precisamos do Node.js (ambiente de execução de JavaScript) e do seu gerenciador de pacotes (npm ou yarn) para criar e gerenciar nosso projeto.

**Para verificar se já estão instalados,** abra seu terminal (no Windows, pode ser o "Prompt de Comando" ou o "PowerShell"; no VS Code, pressione “ctrl + aspas” para abrir o terminal). Digite os seguintes comandos, um por vez, e pressione Enter após cada um:

```bash
node -v
npm -v
```

- Se aparecerem números de versão, significa que o Node.js e o npm já estão instalados no seu computador.
- **Instalando (caso não estejam instalados):** Se algum dos comandos acima não funcionar ou mostrar uma mensagem de erro, você precisará instalar o Node.js. Vá para o site oficial do [Node.js](https://nodejs.org/) e baixe a versão LTS, que é mais estável. A instalação geralmente inclui o npm automaticamente.
- Após a instalação, feche e abra o terminal novamente e execute os comandos `node -v` e `npm -v` para confirmar que tudo está funcionando.
- **Instalando o yarn:** O yarn é outro gerenciador de pacotes. Ele oferece algumas vantagens em termos de velocidade e determinismo. Se você quiser usá-lo em vez do npm, pode instalá-lo com o seguinte comando no seu terminal (depois de ter o npm instalado):
    
    ```bash
    npm install -g yarn
    ```
    
- Para verificar a instalação do yarn, digite:
    
    ```bash
    yarn -v
    ```
    

### **Passo 2: Criar o projeto com yarn e Vite**

O Vite é uma ferramenta de construção extremamente rápida para aplicações web modernas. Ele configura automaticamente toda a estrutura básica do projeto com as dependências necessárias e oferece um tempo de inicialização do servidor instantâneo. O yarn será nosso gerenciador de pacotes.

- Para criar o projeto, execute o seguinte comando no terminal do VS Code:

```bash
yarn create vite
```

Este comando vai baixar e instalar todas as dependências necessárias para o seu projeto e após finalizar, pedirá um nome para o projeto. Vamos chamar nosso primeiro projeto de `meu-primeiro-react`, mas você pode escolher o nome que quiser (sem espaços e em letras minúsculas é uma boa prática).

Após escolher o nome, o programa pedirá para selecionar o framework. Aqui, selecionaremos “React”. A seguir, ele pedirá para selecionar a variante. Para projetos mais rápidos, é aconselhável escolher “TypeScript + SWC”.

### **Passo 3: Entrando na pasta do projeto e instalando dependências**

Assim que o Vite terminar de criar o projeto, navegue até a pasta do seu novo aplicativo:

```bash
cd meu-primeiro-react
```

Agora, precisamos instalar as dependências do projeto (como o próprio React e outras bibliotecas essenciais). Com o yarn, isso é feito com o seguinte comando:

```bash
yarn
```

O yarn vai ler o arquivo `package.json` (que o Vite já criou) e baixar todas as dependências listadas na pasta `node_modules`.

### **Passo 4: Iniciando o servidor de desenvolvimento**

Com as dependências instaladas, podemos rodar o projeto:

```bash
yarn dev
```

Este comando irá iniciar um servidor de desenvolvimento local. Geralmente, ele indicará no seu terminal o endereço em que o seu aplicativo está rodando (algo como `http://localhost:5173/`). Abra esse endereço no seu navegador. Você deverá ver a página inicial padrão do React + Vite.

### **Passo 5: Explorando a estrutura do projeto**

Vamos dar uma olhada na estrutura de arquivos e pastas que o Vite criou:

```markdown
meu-primeiro-react/
├── node_modules/         (Contém todas as bibliotecas e dependências do projeto)
├── public/               (Contém a/rquivos estáticos como o favicon)
│   └── vite.svg
├── src/                  (Onde a maior parte do seu código React ficará)
│   ├── App.tsx           (O componente raiz do seu aplicativo)
│   ├── App.css           (Exemplo de CSS para o componente App)
│   ├── index.css         (Estilos globais)
│   ├── main.tsx          (O ponto de entrada do seu aplicativo React)
│   └── assets/           (Para imagens e outros recursos)
│       └── react.svg
├── .gitignore            (Especifica arquivos que o Git deve ignorar)
├── eslint.config.js      (Arquivo de configuração do ESLint)
├── index.html            (A página HTML principal que o React injetará o seu aplicativo)
├── package.json          (Arquivo de configuração do yarn, lista as dependências e scripts)
├── README.md             (Arquivo com informações sobre o projeto)
├── tsconfig.app.json     (Arquivo de configuração do TypeScript)
├── tsconfig.node.json    (Arquivo de configuração do TypeScript)
├── tsconfig.json         (Arquivo de configuração do TypeScript)
├── vite.config.js        (Arquivo de configuração do Vite)
└── yarn.lock             (Informações detalhadas sobre as versões das dependências)
```

### **Passo 6: Entendendo a conexão entre os arquivos**

Entender como os arquivos index.html, main.tsx e app.tsx se conectam é fundamental para compreender como funciona um projeto React.

**1. `index.html`**

O arquivo `index.html` é o arquivo que o navegador carrega quando você acessa a sua aplicação React. O React injeta a interface aqui, dentro da `div` com `id="root"`. Observe a tag `<script type="module" src="/src/main.tsx"></script>`. Esta é a chave da conexão, chamando o arquivo React.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React + TS</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

**2. `main.tsx`**

É o ponto de entrada do React. Ele é o primeiro script que o navegador executa após o `index.html` ser carregado (devido à tag `<script>` no HTML).

Ele faz 2 coisas principais:

- Importa a biblioteca React e o `App.tsx`, que é o seu componente principal
- Diz ao React para “injetar” o `App.tsx` dentro do `root` do HTML

```tsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.tsx'

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

**3. `App.tsx`**

Contém o componente funcional ou de classe que serve como o contêiner principal da sua aplicação React.

```tsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>
        <a href="https://vite.dev" target="_blank">
          <img src={viteLogo} className="logo" alt="Vite logo" />
        </a>
        <a href="https://react.dev" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.tsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </>
  )
}

export default App
```

- **`function App()`:** O JSX dentro do `return` descreve a estrutura visual inicial da sua aplicação. Ele pode incluir outros componentes, elementos HTML, texto, etc.
- **`export default App`:** Exporta o componente `App` como padrão, o que permite que ele seja importado facilmente no `main.tsx`.

**Resumindo:**

1. O navegador carrega o `index.html`
2. O navegador inicia a execução do `main.tsx`
3. O `main.tsx` importa a biblioteca React e o componente `App` do `App.tsx`, renderizando o componente `<App />` dentro do elemento `div` que existe no `index.html`
4. O componente `App` e seus filhos (outros componentes que ele pode renderizar) então controlam e atualizam a interface do usuário dentro do navegador

Essa é a cadeia de conexão para iniciar uma aplicação React com Vite e TypeScript. o `App.tsx` define o componente raiz da sua aplicação React, que é a base de toda a interface do usuário que será renderizada no navegador dentro do elemento `root` do `index.html` através da instrução no `main.tsx`.

Para entender facilmente, imagine que sua aplicação React é como um teatro:

- `index.html` é o teatro vazio com um palco montado. A `<div id="root">` é esse palco esperando a apresentação.
- `main.tsx` é o diretor da peça. Ele diz: “Vamos começar! A peça principal é o App. Entrem em cena no palco!”
- `App.tsx` é a peça que será encenada. Com todos os atores (componentes), cenário (HTML/JSX, CSS) e ações (interatividade com React).

### **Passo 7: Entendendo componentes e modificando o `App.tsx`**

- **O que é um componente?**

Pense em um componente como uma peça de Lego. Cada peça pode ser usada várias vezes e pode conter seus próprios estilos, comportamentos e conteúdo.

- **Modificando o `App.tsx`**

Inicialmente, o `App.tsx` criado pelo Vite vem com uma demonstração básica do React + Vite. Vamos começar simplificando o `App.tsx` original, removendo o código padrão do Vite. Substitua o conteúdo atual por algo mais limpo, assim:

```tsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>
        <h1>Hello world</h1>
      </div>
    </>
  )
}

export default App
```

Depois de salvar, você verá o conteúdo aparecendo na tela.

Agora, podemos apagar do `App.tsx` o que não está sendo utilizado. Tudo o que não está sendo utilizado ficará com visual apagado devido ao ESLint. O código ficará assim:

```tsx
import "./App.css";

function App() {
  return (
    <>
      <div>
        <h1>Hello world</h1>
      </div>
    </>
  );
}

export default App;
```

- Também podemos apagar todos os arquivos .css e suas importações. Para começar com uma estilização do zero, apagamos todos os arquivos `.css` (`App.css` e `index.css`) dentro da pasta `src`. Também removemos as linhas de importação desses arquivos tanto em `App.tsx` (`import "./App.css";`) quanto em `main.tsx` (`import './index.css';`).
- **Limpeza das Pastas `assets` e `public`:** Removemos o conteúdo dentro das pastas `assets` (onde estavam as logos) e `public` (onde estava o `vite.svg` do favicon).
- **Remoção da Referência ao Favicon no `index.html`:** Já que removemos o `vite.svg`, apagamos a linha que o referenciava no `<head>` do `index.html`:

Agora, os erros param de acontecer e temos um projeto em branco com “Hello world”.

Para o nosso primeiro projeto, vamos criar um site com uma Navbar, uma Section e um Footer. Para isso, no nosso `App.tsx`, podemos escrever o seguinte:

```tsx
function App() {
  return (
    <>
      <nav>
        <div>
          <h1>Barra de navegação</h1>
        </div>
      </nav>

      <section>
        <div>
          <h1>Seção 1</h1>
        </div>
        <div>
          <h2>Seção 2</h2>
        </div>
      </section>

      <footer>
        <h1>Footer</h1>
      </footer>
    </>
  );
}

export default App;
```

Isso funciona para criarmos o projeto, porém poderíamos fazer a mesma coisa com HTML. Queremos ter outras páginas além da página inicial, e seria trabalhoso copiar e colar vários blocos de código em arquivos diferentes. Aqui entra o poder do React. Com ele, podemos componentizar o código para reaproveitá-lo.

### **Passo 8: Criando um novo componente**

Primeiro, criaremos uma pasta “components” dentro da pasta “src”. Agora, criaremos o nosso primeiro componente, o arquivo `Navbar.tsx` (note a primeira letra maiúscula, uma convenção para nomes de componentes React). Ele retornará o nosso Navbar:

```tsx
export function Navbar() {
  return (
    <nav>
      <div>
        <h1>Barra de navegação</h1>
      </div>
    </nav>
  );
}
```

- **`export function Navbar() { ... }`**: Definimos e exportamos um componente funcional chamado `Navbar`.
- **`return (...)`**: Retornamos o JSX que representa a estrutura da nossa barra de navegação.

Nota: um componente React deve retornar um único nó pai. Se escrevermos o seguinte:

```tsx
export function Navbar() {
  return (
    <nav>
      <div>
        <h1>Barra de navegação</h1>
      </div>
    </nav>
    <div>
        <h1>Hello World</h1>
    </div>
  );
}
```

o código quebrará. Portanto, se quisermos retornar mais de um elemento, usamos o fragment (`<>` e `</>`) para englobar todo o bloco:

```tsx
export function Navbar() {
  return (
    <>
      <nav>
        <div>
          <h1>Barra de navegação</h1>
        </div>
      </nav>
      <div>
        <h1>Hello World</h1>
      </div>
    </>
  );
}
```

Agora, com o componente criado, podemos importá-lo e chamá-lo no `App.tsx`. Ele se tornou uma “peça” que podemos colocar em qualquer página do nosso projeto.

```tsx
import { Navbar } from "./components/Navbar";

function App() {
  return (
    <>
      <Navbar />

      <section>
        <div>
          <h1>Seção 1</h1>
        </div>
        <div>
          <h2>Seção 2</h2>
        </div>
      </section>

      <footer>
        <h1>Footer</h1>
      </footer>
    </>
  );
}

export default App;
```

### **Passo 9: Criando outros componentes**

Agora, criaremos o componente Section. Para isso, realizaremos o mesmo procedimento do passo anterior. Criaremos o arquivo “Section.tsx” dentro da pasta “components” com o seguinte código:

```tsx
export function Section() {
  return (
    <>
      <section>
        <div>
          <h1>Seção 1</h1>
        </div>
        <div>
          <h2>Seção 2</h2>
        </div>
      </section>
    </>
  );
}
```

Importamos e chamamos ele no App.tsx:

```tsx
import { Navbar } from "./components/Navbar";
import { Section } from "./components/Section";

function App() {
  return (
    <>
      <Navbar />

      <Section />

      <footer>
        <h1>Footer</h1>
      </footer>
    </>
  );
}

export default App;
```

Para criar o último componente, criamos o arquivo “Footer.tsx” dentro da pasta “components” com o seguinte código:

```tsx
export function Footer() {
  return (
    <>
      <footer>
        <h1>Footer</h1>
      </footer>
    </>
  );
}
```

A seguir, podemos importá-lo e chamá-lo no `App.tsx`:

```tsx
import { Navbar } from "./components/Navbar";
import { Section } from "./components/Section";
import { Footer } from "./components/Footer";

function App() {
  return (
    <>
      <Navbar />

      <Section />

      <Footer />
    </>
  );
}

export default App;
```

Agora, nosso `App.tsx` está muito mais limpo, modular e conciso. Em vez de ter toda a estrutura da página (navbar, seção, footer) diretamente dentro dele, estamos importando e usando componentes reutilizáveis. Isso demonstra o poder da componentização no React:

- **Organização:** Código separado em arquivos lógicos.
- **Reutilização:** Os componentes `Navbar`, `Section` e `Footer` podem ser usados em outras partes da nossa aplicação, se necessário.
- **Manutenção:** Alterações em um componente afetam apenas aquele componente, tornando a manutenção mais fácil.
- **Legibilidade:** O `App.tsx` agora descreve a estrutura da página de forma mais clara, apenas listando os componentes que a compõem.

### **Passo 10: Adicionando navegação**

A navegação é essencial para qualquer aplicação web com múltiplas páginas. Vamos adicionar navegação usando o React Router DOM, que é a biblioteca mais usada para lidar com rotas.

**Instalar o React Router DOM**
    
Primeiro, precisamos adicionar a biblioteca ao nosso projeto. Abra o terminal dentro da pasta do projeto e execute o seguinte comando:
    
```bash
yarn add react-router-dom
```
    
Este comando irá baixar e instalar o `react-router-dom` como uma dependência do seu projeto.
    
**Configurando as rotas no `App.tsx`**
    
Agora, vamos modificar o `App.tsx` para configurar as rotas. Precisamos importar alguns componentes do `react-router-dom`:
    
```tsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { Footer } from "./components/Footer";
import { Navbar } from "./components/Navbar";
import { Section } from "./components/Section";

function App() {
  return (
    <>
      <Navbar />
      <Section />
      <Footer />
    </>
  );
}

export default App;
```
    
**Componentes importados:**
    
- `BrowserRouter`: Um componente que envolve todo o conteúdo que precisa ter acesso ao roteamento. É como o controlador da navegação do seu site. Ele permite que você use rotas com URLs (como `/`, `/sobre`, `/contato`).
        
```tsx
<BrowserRouter>
	{/* Aqui dentro ficam as rotas da sua aplicação */}
</BrowserRouter>
```
        
- `Routes`: Um componente que atua como um container para definir suas rotas. Ele renderiza o primeiro `<Route>` que corresponder à URL atual. Pense nele como uma lista de caminhos possíveis dentro do site.
        
```tsx
<BrowserRouter>
  <Routes>
	  {/* Cada Route define uma página diferente */}
  </Routes>
</BrowserRouter>;
```
        
- `Route`: Define uma rota específica. Ele recebe duas propriedades principais:
    - `path`: O padrão da URL que esta rota corresponde (por exemplo: `/`, `/sobre`, `/contato`).
    - `element`: O componente que deve ser renderizado quando esse endereço for acessado.
    
**Exemplo:**
    
```tsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { Footer } from "./components/Footer";
import { Navbar } from "./components/Navbar";
import { Section } from "./components/Section";

function App() {
  return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/login" element={<Footer />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}

export default App;
```
    
A rota que criamos tem um caminho que se chama `/login`. Agora, se acessarmos `/login` (http://localhost:5173/login), apenas o componente `<Footer />` será mostrado na tela.
    
Vamos continuar com a nossa analogia da peça de teatro para entender como o roteamento funciona:
    
- As cenas da peça são as páginas do site.
- `<BrowserRouter>` é como o diretor da peça. É ele que controla tudo o que vai aparecer no palco (navegador).
- `<Routes>` lista todas as cenas (páginas) podem entrar em cena.
- Cada `<Route>` é uma cena diferente da peça.
    
> 💡   
>    Quando usamos React Router, ele muda apenas o que precisa na tela, sem recarregar o site inteiro. Você muda o ambiente (conteúdo), mas tecnicamente continua dentro da mesma estrutura, sem sair ou recarregar tudo. Isso deixa a navegação muito mais rápida e fluida. É devido a isso que dizemos que o React é usado para criar aplicações web de página única (**SPAs - Single Page Applications**). 
>    
>    SPA é um tipo de aplicação web que carrega uma única página HTML e atualiza o conteúdo dinamicamente, sem recarregar a página inteira toda vez que o usuário navega.
    
    
Continuando, podemos criar várias rotas:
    
```tsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { Footer } from "./components/Footer";
import { Navbar } from "./components/Navbar";
import { Section } from "./components/Section";

function App() {
  return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/login" element={<Footer />} />
          <Route path="/" element={<Navbar />} />
          <Route path="/section" element={<Section />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}
    
export default App;
```
    
Porém, se criarmos rotas dessa forma, precisaríamos adicionar vários componentes dentro do `element`. Em vez de chamarmos por componentes, podemos criar rotas e chamar por páginas.

### **Passo 11: Criando páginas**

Para isso, dentro da pasta “src”, criaremos a pasta “pages” e, dentro dela, criaremos o arquivo “Home.tsx”. Nela, podemos retornar os componentes que criamos anteriormente:

```tsx
import { Navbar } from "../components/Navbar";
import { Section } from "../components/Section";
import { Footer } from "../components/Footer";

export function Home() {
  return (
    <>
      <Navbar />
      <Section />
      <Footer />
    </>
  );
}
```

Também podemos criar uma página de login, criando o arquivo “Login.tsx”  dentro de “pages”:

```tsx
import { Navbar } from "../components/Navbar";
import { Footer } from "../components/Footer";

export function Login() {
  return (
    <>
      <Navbar />
      <div>
        <h1>Login</h1>
      </div>
      <Footer />
    </>
  );
}
```

Agora, podemos organizar o arquivo `App.tsx` para criar os caminhos para cada página:

```tsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { Home } from "./pages/Home";
import { Login } from "./pages/Login";

function App() {
  return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/login" element={<Login />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}

export default App;
```

Quando quisermos que um componente apareça em todas as páginas (por exemplo, o footer), podemos colocá-lo dentro do `BrowserRouter` em vez de adicioná-lo nos arquivos de cada página:

```tsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import { Home } from "./pages/Home";
import { Login } from "./pages/Login";
import { Footer } from "./components/Footer";

function App() {
  return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/login" element={<Login />} />
        </Routes>
        <Footer />
      </BrowserRouter>
    </>
  );
}

export default App;
```

Observe que `<Footer />` não é uma rota, então não é necessário englobá-lo dentro de `Routes`, mas ele é um componente que queremos em todas as páginas. Se posteriormente o footer conter links, é necessário que ele esteja dentro do `BrowserRouter`.

Podemos ainda organizar as rotas em um arquivo separadamente. Isso é eficiente para quando tivermos muitas rotas. Para isso, criaremos a pasta “routes” dentro de “src” e o arquivo “index.tsx” dentro dela contendo as rotas:

```tsx
import { Route, Routes } from "react-router-dom";
import { Home } from "../pages/Home";
import { Login } from "../pages/Login";

export function AppRoutes() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/login" element={<Login />} />
    </Routes>
  );
}
```

Agora, precisamos chamar e importar as rotas no App.tsx:

```tsx
import { BrowserRouter } from "react-router-dom";
import { Footer } from "./components/Footer";
import { AppRoutes } from "./routes";

function App() {
  return (
    <>
      <BrowserRouter>
        <AppRoutes />
        <Footer />
      </BrowserRouter>
    </>
  );
}

export default App;
```

Após todas as alterações que fizemos, a estrutura do nosso projeto ficará assim:

```markdown
meu-primeiro-react/
├── node_modules/         
├── public/               
├── src/                  
│   ├── assets/           
│   ├── components/       (Pasta criada para componentes)
│   │     ├── Footer.tsx        
│   │     ├── Navbar.tsx        
│   │     └── Section.tsx       
│   ├── pages/            (Pasta criada para páginas)
│   │     ├── Home.tsx        
│   │     └── Login.tsx       
│   ├── routes/           (Pasta criada para rotas)
│   │     └── index.tsx
│   ├── App.tsx
│   └── main.tsx
├── .gitignore
├── eslint.config.js
├── index.html
├── package.json
├── README.md
├── tsconfig.app.json
├── tsconfig.node.json
├── tsconfig.json
├── vite.config.js
└── yarn.lock
```

### **O que você aprendeu no React até aqui:**

**Fundamentos**

- O que é React e por que usá-lo
- Diferença entre HTML/CSS/JS e React
- Criar um projeto com Vite + React + TypeScript
- Entender a função do index.html
- Compreender como o main.tsx conecta o React ao HTML
- Saber o papel do App.tsx como componente principal

**Componentes**

- Criar e organizar componentes
- Importar e usar componentes dentro do App.tsx
- Usar fragmentos (`<> </>`) para retornar múltiplos elementos

**Roteamento com React Router**

- Instalar o react-router-dom
- Entender e usar `BrowserRouter`, `Routes` e `Route`
- Criar navegação entre páginas
- Compreender o conceito de SPA (Single Page Application)