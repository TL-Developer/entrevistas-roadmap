# Perguntas Técnicas – Frontend (React)

## Fundamentos do React
- Qual a diferença entre `props` e `state` em componentes React?
- Como funciona o Virtual DOM e por que ele é importante no React?
- O que são Hooks em React? Quais você mais utiliza no dia a dia?

## Gerenciamento de Estado
- Quando você optaria por usar `useContext` em vez de Redux?
- Explique o fluxo de dados em uma aplicação usando Redux.
- Você já trabalhou com alguma alternativa ao Redux (ex: Zustand, Recoil, Jotai)? O que achou?
- O que é o padrão "Ducks" no Redux? Quais os benefícios dessa abordagem?

## Hooks Específicos
- Para que serve o `useMemo` e quando deve ser usado?
- Qual a diferença entre `useEffect` e `useLayoutEffect`?
- O que pode causar um memory leak ao usar `useEffect` e como evitá-lo?

## Performance e Otimizações
- O que são listas virtualizadas? Quando usá-las? Já utilizou algo como `react-window` ou `react-virtualized`?
- Como você evita renderizações desnecessárias em componentes React?
- Como o `React.memo` difere do `useMemo`?

## Arquitetura e Boas Práticas
- Como você organiza os diretórios de uma aplicação React grande? Já usou algum padrão como Atomic Design?
- Qual a sua opinião sobre CSS-in-JS versus CSS Modules?
- Já utilizou Server-Side Rendering com React? Com qual framework (ex: Next.js)?

## Integração com o Back-end
- Como você lida com chamadas assíncronas no React? Usa `axios`, `fetch`, `RTK Query`, `SWR` ou outra biblioteca?
- Como você trata erros de API e estados de carregamento em seus componentes?

## Testes
- Quais tipos de testes você aplica em aplicações React? (unitários, integração, E2E)
- Já usou ferramentas como Jest, Testing Library ou Cypress?

---

Essas perguntas podem ser usadas para entrevistas técnicas, quizzes, ou para montar um plano de estudo em frontend com React.

# Perguntas Técnicas – Microfrontends e Module Federation

## Conceitos Fundamentais
- O que são Microfrontends e qual problema eles procuram resolver?
- Quais são os principais desafios de trabalhar com uma arquitetura de Microfrontends?
- Qual a diferença entre um Microfrontend e um SPA (Single Page Application) modular?

## Module Federation (Webpack 5)
- O que é o Module Federation e como ele se relaciona com Microfrontends?
- Quais são os papéis do **host** e dos **remotes** em uma aplicação com Module Federation?
- Como funciona o compartilhamento de dependências com Module Federation (`shared` config)?

## Benefícios e Vantagens
- Quais são os principais benefícios em adotar Microfrontends?
  - Ex: Times independentes, deploys desacoplados, escalabilidade organizacional.
- Em que cenários uma arquitetura de Microfrontends pode trazer mais vantagens do que um monolito frontend tradicional?
- Quais vantagens o Module Federation traz em relação a outras abordagens, como iframes ou importação via pacotes NPM?

## Malefícios e Desvantagens
- Quais são os principais riscos ou desvantagens da adoção de Microfrontends?
  - Ex: Complexidade de configuração, duplicação de dependências, sobrecarga de rede.
- Como problemas como **inconsistência de estilos** e **isolamento de contexto** podem ser mitigados?
- Como o versionamento e o cache afetam o carregamento dinâmico de Microfrontends?

## Implementação
- Quais passos básicos são necessários para configurar o Module Federation no Webpack?
- Como você gerencia o roteamento entre diferentes Microfrontends?
- Já usou alguma solução pronta para Microfrontends, como Single-SPA, Nx, Bit.dev ou Module Federation Plugin da Webpack? Qual foi sua experiência?
- Como você garantiria uma boa experiência de desenvolvedor em uma arquitetura distribuída?

## Casos Reais e Escalabilidade
- Você já participou de algum projeto com Microfrontends? Como foi feita a divisão?
- Como garantir que diferentes equipes não entrem em conflito ao trabalhar em Microfrontends?
- Quais boas práticas você recomenda para manter a governança e a padronização entre Microfrontends?

---

Essas perguntas são úteis para entrevistas avançadas, avaliações técnicas ou discussões de arquitetura em projetos com foco em escalabilidade de frontends.

# Perguntas Técnicas – JavaScript (Nível Sênior)

## Conceitos Fundamentais
- O que é **hoisting** em JavaScript? Como ele afeta variáveis e funções?
- Qual a diferença entre `var`, `let` e `const` em termos de escopo e hoisting?
- Explique a diferença entre `==` e `===` em JavaScript. Quando faz sentido usar cada um?
- O que é **coerção de tipos** e como o JavaScript lida com ela?

## Escopo e Closures
- O que são **closures**? Você pode dar um exemplo prático?
- Qual a diferença entre **escopo léxico** e **escopo dinâmico**?
- O que é um **Immediately Invoked Function Expression (IIFE)** e para que serve?

## Assíncrono e Promises
- Qual a diferença entre **promises**, `async/await` e callbacks?
- O que é o **event loop** em JavaScript e como ele funciona?
- Como o JavaScript trata a **pilha de chamadas** (call stack) e a **fila de tarefas** (task queue)?

## Objetos e Prototypes
- Como funciona o sistema de **prototipagem** em JavaScript?
- Qual a diferença entre `Object.create()` e usar `class` com `extends`?
- O que é o **prototype chain** e como ele é percorrido?

## Funções Avançadas
- O que são **funções de alta ordem** (higher-order functions)? Cite exemplos.
- Explique a diferença entre `.call()`, `.apply()` e `.bind()`.
- O que é **currying**? Quando ele pode ser útil?

## Arrays e Métodos Funcionais
- Qual a diferença entre `map()`, `filter()` e `reduce()`? Dê exemplos práticos.
- O que acontece quando você usa `forEach()` com `await` dentro?
- Como funciona o `Array.prototype.flatMap()`?

## Memory Management
- O que é um **memory leak** em JavaScript e como preveni-lo?
- Como o **garbage collector** do JavaScript decide o que limpar da memória?

## Código Seguro e Boas Práticas
- Quais práticas você adota para evitar problemas com **variáveis globais**?
- Como você lida com erros assíncronos em grandes aplicações?
- Já utilizou **proxy objects**? Para que eles são úteis?

## Extras
- Qual a diferença entre `null`, `undefined` e `NaN`?
- O que é o `Symbol` em JavaScript e onde ele pode ser útil?
- O que são **generators** e como diferem de funções tradicionais?

---

Essas perguntas são ótimas para entrevistas técnicas, quizzes avançados ou para mapear lacunas de conhecimento em JavaScript moderno.


# Perguntas Técnicas – Navegador, Memória e Performance Frontend

## Memória: Heap e Stack
- Qual a diferença entre a **stack** e a **heap** na execução do JavaScript no navegador?
- O que é uma **stack overflow** e como ela pode acontecer em aplicações JavaScript?
- Dê um exemplo prático de quando algo é armazenado na stack e quando vai para a heap.
- Como o **garbage collector** do V8 (engine do Chrome) identifica e remove objetos não utilizados?

## Event Loop e Concorrência
- Explique como funciona o **event loop** no JavaScript.
- Qual a diferença entre a **microtask queue** (ex: `Promise`) e a **macrotask queue** (ex: `setTimeout`)?
- O que é a **call stack** e como ela interage com o event loop?
- Como você explicaria o funcionamento do event loop para alguém de backend que está começando no frontend?

## Ferramentas do Chrome para Diagnóstico
- Quais ferramentas do **Chrome DevTools** você usa para analisar performance de renderização?
- Como você identifica **memory leaks** usando a aba **Memory**?
- Para que serve a aba **Performance** e quais métricas você costuma observar nela?
- Como utilizar o **Lighthouse** para medir performance, acessibilidade e boas práticas?
- O que é o **Coverage tab** e como ele pode ajudar a identificar CSS e JS não utilizados?

## Performance de Renderização
- O que significa **reflow** e **repaint** no contexto do navegador?
- Como evitar **layouts thrashing** e reflows desnecessários?
- Quais técnicas você aplica para melhorar a performance de scroll em listas grandes?
- Já utilizou técnicas de **debounce** ou **throttle**? Em quais situações?

## Otimizações Gerais
- Quais boas práticas você adota para reduzir o tempo de carregamento (First Paint e Time to Interactive)?
- Como o uso de **lazy loading**, **code splitting** e **tree shaking** pode melhorar a performance?
- Como o uso de **Service Workers** pode impactar a performance e experiência offline?
- Quais estratégias você usa para lidar com imagens pesadas e fontes externas?

---

Essas perguntas ajudam a avaliar a profundidade do conhecimento sobre o funcionamento do navegador, algo essencial para otimização de experiências frontend em larga escala.

# Perguntas Técnicas – TypeScript

## Fundamentos
- Qual a principal diferença entre TypeScript e JavaScript?
- O que são **tipagens estáticas** e como elas ajudam na qualidade do código?
- Como funciona o processo de **transpilação** do TypeScript para JavaScript?

## Tipos Básicos e Avançados
- Quais são os tipos primitivos do TypeScript?
- O que é `any` e por que seu uso deve ser evitado?
- Qual a diferença entre os tipos `unknown`, `any`, `never` e `void`?
- Para que serve o tipo `Record`?

## Interfaces e Types
- Qual a diferença entre `type` e `interface` em TypeScript? Quando usar cada um?
- Como estender uma `interface`? E como fazer interseção entre tipos (`&`)?
- É possível declarar duas vezes a mesma interface? O que acontece?

## Generics
- O que são **Generics** e por que são úteis em funções e componentes?
- Como declarar uma função genérica que recebe um array de qualquer tipo e retorna o primeiro elemento?
- Você já utilizou **constraints** com generics (`<T extends SomeType>`)?

## Inferência e Narrowing
- O que é **type inference** no TypeScript?
- Como o TypeScript faz o **narrowing** de tipos usando `typeof`, `instanceof` ou `in`?
- Como funciona o `as const` e para que ele é usado?

## Utilitários e Tipos Avançados
- Quais são os principais **utility types** do TypeScript (ex: `Partial`, `Pick`, `Omit`, `Readonly`, `Required`)?
- Já usou o `keyof` e `typeof` como operadores de tipo? Pode dar um exemplo?
- Como criar um tipo que representa todas as chaves de um objeto?

## Ambientes e Configuração
- O que é o `tsconfig.json` e quais opções você considera essenciais?
- O que o `"strict"` habilita no TypeScript?
- Como configurar `paths` e `aliases` para facilitar imports em projetos grandes?

## Integração com Bibliotecas
- Como você adiciona tipagens em bibliotecas que não possuem tipos nativos?
- Para que serve o pacote `@types`? Quando é necessário instalá-lo manualmente?
- Como lidar com bibliotecas de JS puro em projetos TypeScript?

## Boas Práticas
- Você prefere usar tipagem explícita ou deixar o TypeScript inferir? Por quê?
- Como você lida com APIs REST onde os dados são dinâmicos ou desconhecidos até o runtime?
- Já usou **zod**, **io-ts** ou bibliotecas similares para validação de tipos em tempo de execução?

---

Essas perguntas são úteis para medir conhecimento técnico em TypeScript, tanto em entrevistas quanto em avaliações de equipe.