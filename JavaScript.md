# JavaScript
## Introdução a JavaScript
Javascript é a linguagem de programação necessária para adicionar interatividade a uma página web. Anda lado a lado com HTML e CSS, sendo assim as 3 tecnologias principais para um front-end.

Foi inicilmente criada por Brendan Eich da NetScape e foi anunciado primeiro na imprensa pela NetScape em 1995. Começou com o nome de Mocha, em seguida recebeu o nome de LiveScript, e só então em 1996, a NetScape querendo captalizar em cima do sucesso do Java pós o nome de JavaScript, embora não tivesse nada a ver uma linguagem com a outra.

Para usar JavaScript basta usar a tag `script` no fim de um documento HTML, podendo usar os scripts dentro do proprio corpo do documento, ou importando usando a propria tag script.

## Variaveis JavaScript 
Variável é um conteiner para um valor. Na maioria das vezes a gente precisa guardar uma informação para reutilizá-la ou manipular.

Variáveis são declaradas usando `var` (para variaveis de escopo global), `let` (para variáveis de escopo local) e `const` (para variaveis de escopo local).

### Hoistings 
O Hoisting funciona como se funções declaradas com a _keyword_ `function` fossem movidas para o topo do arquivo .js, e as variaveis `var` fossem declaradas no topo do arquivo também.
Não é exatamente assim, mas o comportamento é basicamente esse. Aqui vai um exemplo de como funciona a função:
```
console.log(hoist) // Output: undefined

var hoist = 'A variavel foi Hoisteada'
```
Neste exemplo a gente não tem um erro pois a _keyword_ `var` age como se fosse declarada antes como se o codigo fosse assim:
```
var hoist;
console.log(hoist) // Output: undefined

var hoist = 'A variavel foi Hoisteada'
```
Em funções acontece basicamente o mesmo, mas ela será executada normalmente mesmo estando abaixo de onde ela foi chamada. Veja:
```
hoist() // Output: "Hoisting"

function hoist() {
  console.log("Hoisting")
}
```
É como se a função fosse declarada antes de sua chamada, isto é `Hoisting`. Detalhe que se a função fosse usada de outra forma daria um erro. Exemplo:
```
hoist() // Output: "TypeError: experssion is not a function"

const hoist = function() {
  console.log("Não vai ser printado")
}
```
Aqui tem um erro pois a função não foi declarada com a _keyword_ `function`, e mesmo que fosse declarada com `var` ainda daria este mesmo erro.

### Regras para nomeação de variaveis

1. Ser descritiva
2. Não ser excessivamente descritiva
3. Abrevie palavras grandes
4. Usar letras maiúsculas e minúsculas para quebrar palavras

### Escopos de Variaveis
O escopo da variavel determina onde esta variável é acessível, JavaScript tem 3 tipos de escopos principais:
1. *Escopo global*: Variáveis declaradas fora de qualquer função ou bloco tem o escopo global. Podem ser acessadas e modificadas de qualquer parte do código;
2. *Escopo de Função*: Variáveis declaradas dentro de uma função tem o escopo de função. Elas só podem ser acessadas dentro desta função;
3. *Escopo de Bloco*: Variáveis declaradas usando `let` ou `cont` dentro de um bloco (tipo um `if` ou um `for`) tem escopo de bloco. Só podem ser acessadas dentro deste bloco.

## Data Types
Data type se refere ao tipo de data que uma variável pode 'segurar'. Existem 7 tipos primários em JavaScript (Number, BigInt, String, Boolean, Null, Undefined e Symbol). Objetos são não primários.
- String é um tipo primitivo que guarda uma sequência de caracteres, têm por característica uma dupla de sinais como `""` ou `''` ou ` `` ` e sempre se encerra com o mesmo que se inicia.
- undefined, sempre que uma variável é criada sem ter um valor atribuido ela recebe o valor de undefined (indefinido), assim como uma função retorna undefined se um valor não é retornado, assim como um método também... Ou seja sempre que um valor não é atribuido a um metodo, variavel ou uma função que não retorna nada, o valor será undefined.
- BigInt é mais utilizado para conseguir resultado com mais precisão com numeros muito grandes, extrapolando o tamanho de variaveis do tipo Number.
- Number representa numeros com pontos flutuantes como um 37 ou -8,4. Existe a função `Number()` que pode transformar um outro tipo em um Number.
- Boolean pode ser dois tipo `true` ou `false`, são valores lógicos e essenciais para controle do fluxo de um programa, muito usados em `while`, `for` `if`.
- null é a representação de nada, de uma variavel vazia, onde não aponta para nenhum objeto. Pode ser usada para zerar o valor de uma variável.
- Symbols eu não sei explicar bem.

Você pode usar `typeof operator` para imprimir o tipo de um valor, o output será uma string, ex: `console.log(typeof 42) // output: number`.

###  Objects
Objeto em JavaScript é um tipo de estrutura de dados com chaves e valores, valores que podem ser de qualquer tipo de dados. Por exemplo, posso criar um objeto carro com caracteristicas como pneu, cor, ano e cada caracteristica recebe um valor.

- Prototypes: é a forma de se fazer herança em JavaScript. Não consigo explicar a fundo no momento.
- Objetos integrados: existem diversos objetos integrados no JavaScript, alguns como `Math`, `Number`, `Date`, `String`, `Error`, `Function`, `Boolean`.

## Type Casting
Conversor de tipo (ou _typecasting_) significa a transferência de dado de um tipo para outro. Conversão implícita acontece quando o compilador (para linguagens compiladas) ou o _runtime_ (para linguagens de script) automaticamente convertem os tipos de dados. O código fonte também pode exigir explicitamente que uma conversão ocorra.

### Type Conversion/Type Coercion
Type coercion é uma conversão implicita automática de valores de uma tipo para outro (como string para numero). Type Conversion é parecido com o coercion porque eles convertem valores de um tipo para outro com uma diferença: type coercion é implicito. Type conversion pode ser tanto implicito quanto explicito.

### Implicit Type Casting
Conversão de tipo implícita acontece quando o compilador ou _runtime_ automaticamente converte o tipo de dado. JavaScript é uma linguagem de digitação livre e na maioria das vezes os operadores convertem automaticamente um valor para o tipo correto.

### Explicit Type Casting
É uma conversão explicita de um tipo para outro, onde é preciso especificar qual será o novo tipo de dado. Exemplos de métodos de conversão de tipo: `parseInt()`, `parseFloat()`, `toString()`.

## Estrutura de dados
