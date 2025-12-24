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
Estrutura de dados é um formato de organizar, gerenciar e guardar dados de uma forma que permite acesso e modificação eficiente. JavaScript tem estrturas de dados primitivas (integrados) e não-primitivas (não integrado). Estruturas de dados primitivas vêm por padrão com a linguagem de programação e você pode implementá-las imediatamente (como arrays e objetos). Estruturas de dados não primitivas não vêm por padrão e você precisa 'codá-las' se você quiser usá-las.

### Keyed Structures
São coleções de dados chaveadas que são ordenadas por chaves e não index. Objetos _map_ e _set_ são coleções chaveadas e são iteráveis na ordem de inserção.

### Structured Data
Dados estruturados são usados por motores de busca, como Google, para entender o conteudo da página também para juntar informações sobre a web e o mundo em geral.
É também 'codado' usando marcação na página à qual as informações se aplicam.

### JSON
JavaScript Object Notation (JSON) é um formato padrão baseado em texto para representar estrutura de dados baseado na sintaxe de objetos de JavaScript. É comumente usado para transmitir dados em aplicações web (enviar algum dado do servidor para o cliente, para ser exibido em uma pagina web, ou vice versa).


### Coleções Indexados
Coleções indexadas são coleções que tem indices numéricos, por exemplo uma coleção de dados que são ordenadas pelo valor do index. Em JavaScript, um array é uma coleção indexada. Uma matriz é um conjunto ordenado de valores que possui um indice numerico.

#### Arrays
Arrays (matrizes) são objetos que armazenam uma coleçção de itens e podem ser atribuidos a uma variável.
Para declarar um array vazio:
```
let arr = new Array();
let arr = [];
```
Sendo que quase todas as vezes a gente usa a primeira forma para criar um array.

## Comparações de igualdade
Os operadores de comparação são usados em declarações lógicas para determinar igualdade ou diferença entre variáveis ou valores. Operadores de comparação podem ser usados em declarações de condicionais para comparar valores e fazer uma ação dependendo do resultado.
Alguns tipos de operadores de igualdade:
- `==`
- `===`
- `Object.is`

### Operadores de comparação de valores
Em JavaScript, o operador `==` converte o tipo dos operandos antes de comparar, enquanto o operador `===` compara os valores e os tipos dos operandos. O método `Object.is` determina se dois valores são o mesmo valor: `Object.is(value1, value2)`.
`Object.is()` não é equivalente a `==`. O `==` aplica vária coersões para ambos os lados (caso não sejam do mesmo tipo) antes de testar a igualdade (resultando em um comportamento como `"" == false` sendo `true`), mas `Object.is` não faz coersões de valores.
`Object.is()` também não é equivalente a `===`. A única diferença entre eles é o tratamento dos zeros com sinais e valores `NaN`. O `===` (e o `==`) tratam os valores `-0` e `+0` como iguais, mas tratam `NaN` como não igual a ele mesmo.

## Loops e Iterações
Loops oferecem uma forma fáci e rápida de fazer algo repetidamente.
Você pode pensar no loop como uma versão computadorizada de um jogo onde você diz para alguém dar X passos em uma direção, então Y passos em outra. Por exemplo, a ideia "Dê 5 passos para o Leste" poderia ser expressada desta forma como um loop:
```
for (let passo = 0; passo < 5; passo++) {
  // Anda 5 vezes, com valores de passo 0 até passo 4
  console.log('Andando para o Leste 1 passo');
}
```
### for
O loop `for` é uma construção de fluxo de controle padrão padrão em muitas linguagens de programação, incluindo JavaScript. É comumente usado para iterar determinadas sequências ou iterar um determinado numero de vezes e executar um pedaço de código para cada iteração.
```
for (let i = 0; i < 4; i++) {
  console.log(i);
}
```
Este código vai printar [0, 1, 2, 3].

### do ... while
A instrução `do ... while` cria um loop que executa uma instrução especificada até que a condição de teste seja `false`. A condição é checkada depois de executar o bloco `do`, ou seja primeiro o bloco é executado, depois checka se ele será executado novamente... Sempre será executado pelo menos uma vez um loop `do ... while`.
```
let i = 0
do {
  console.log(i)
} while (i > 0)
```
Este código vai printar [0].

### while
A declaração `while` cria um loop que executa um bloco especificado se o teste de condição for `true`. A condição é avaliada antes de executar o código.
```
let i = 0;
while (i < 3) {
  console.log(i);
  i++;
}
```
Este código vai printar [0. 1. 2].

### break / continue
* `break` só pode ser usada para sair de um bloco de loop ou de um switch.
* `continue` só pode ser usada para pular uma iteração em um loop.

### for ... of
A declaração `for ... of` executa um loop que opera em uma sequencia de valores originados de um objeto iteravel. Objetos iteraveis incluem instancias de componentes integrados como Array, String, TypedArray, Map, Set, NodeList (e outras coleções do DOM), chamando uma função personalizada com instruções a serem executadas para o valor de cada objeto distinto.
```
for (variavel of iteravel) {
  declaração
}
```
- `variavel` A cada iteração, um valor de uma propriedade diferente é atrivuido á variável.
- `iteravel` Objeto cujo atributos serão iterados.
- `declaração` Uma declaração a ser executada a cada iteração.

### for ... in
A declaração `for ... in` itera sobre todas as propriedades enumeraveis de um objeto que são chaveadas por strings (ignorando as chaveadas por Symbols), incluindo propriedades enumeraveis herdadas.

## Controle de fluxo
Em JavaScript, o controle de fluxo é uma maneira de como seu computador roda o código de cima para baixo. Começa pela primeira linha e termina na última linha, a não ser que tenha alguma declaração mude o fluxo de controle do programa como um loop, uma condicional, etc.
Nós podemos controlar o fluxo do programa através de qualquer uma destas estruturas:
- Sequencial (modo padrão);
- Declarações de Condições;
- Tratamento de exceções;
- Loops e Iteraçõs.

### Declarações de Condicionais
Quando você escreve um código, você frequentemente quer executar diferentes ações para diferentes decisões. Você pode usar declarações de condicionais em seu código para fazer isso. Em JavaScript, nós temos três declarações de condições: `if`, `if...else` e `switch`.

#### if else
A declaração `if` executa um bloco de código se a condição for _truthy_ (verdadeira). Se a condição é _falsy_, outro bloco de codigo é executado no `else`.
```
if (condição) {
  bloco de código 1
} else {
  bloco de código 2
}
```
Se a condição é verdadeira primeiro bloco de código é executado senão o segundo será.

#### Switch case
A instrução `switch` avalia uma expressão, combinando o valor da expressão com uma série de cláusulas `case`, e executa a instrução com o primeiro `case` com o valor correspondente até uma instrução de `break` ser encontrada. A claúsula `default` de um `switch` será executada caso nenhum dos `case`s correspondam com o valor da expressão (basicamente o mesmo comportamento de um `else`).
```
switch (expressao) {
  case value1:
    //Aqui será executado caso a expressao corresponda com o value1
    break;
  case value2:
    //Aqui será executado caso a expressao corresponda com o value2
    break;
  ...
  case valueN:
    //Aqui será executado caso a expressao corresponda com o valueN
    break;
  default:
    //Aqui será executado caso a expressao não corresponda a nenhum dos valores anteriores
    break;
}

```

### Tratamento de exceções
No JavaScript, todas exceções são objetos simples. Embora a maioria das exceções sejam implementações da classe global Error, qualquer objeto antigo pode ser `thrown`(lançado). Com isto em mente, há duas maneiras de lançar uma exceção: diretamente via um objeto de Error, e através de um objeto personalizado.

#### Declaração Throw
A declaração _Throw_ lança uma exceção definida pelo usuário. A execução da função atual será interrompida (o código abaixo do throw não será executado) e o controle será passado ao primeiro bloco `catch` na stack de chamadas. Se não tiver um bloco de `catch` para pegar o _throw_, o programa será encerrado.
```
throw expression;
```
- `expression` é a expressão a ser lançada.

#### try/catch/finally
Estas são maneiras de tratamentos de erros em JavaScript. Dentro de um bloco de código `try` nós temos o código para rodar, dentro do bloco `catch` nós temos o código para rodar, dentro do bloco `finally` nós temos o código que roda depois da execução dos blocos de códigos anteriores, independente do resultado.

#### Error Objects
Quando um erro acontece de _runtime_ (tempo de execução), um novo objeto `Error` é criado e lançado. Com este objeto `Error`, nós podemos determinar o tipo de erro e tratar de acordo com seu tipo.

##### Tipos de erros
Além dos construtores de erros, JavaScript também possui outros construtores de erros principais.
Como:

* AggragateError - Uma coleção de erros lançados simultaneamente.
* EvalError - Um erro que ocorre durante a avaliação de uma expressão JavaScript.
* InternalError - Um erro interno do JS, frequentemente indicando um bug no mecanismo.
