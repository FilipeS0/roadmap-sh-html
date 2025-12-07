# CSS
CSS ou Cascading Style Sheets (folhas de estilo em cascata) é uma linguagem usada para estilizar documentos escritos em HTML ou XML. Com CSS podemos mudar cores, tamanho, comportamento estrutura mostrada no navegador de um documento HTML. Usando seletores como _tags_, _id_, _classes_ e `propriedades: valor` é possível fazer diversas coisas em uma página web.

## Básico de CSS
- Inline CSS
  - Usar a tag `<style>` dentro de uma tag HTML. 
- Internal CSS
  - Usar a tag `<style>` dentro da tag `<head>` e atribuir as propriedades no proprio documento HTML.
- External CSS
  - Usando algo como `<link rel="stylesheet" type="text/css" href="style.css">` vai linkar para um arquivo externo CSS, é o mais recomendado a se usar.

### Ordem de cascata
- *Tag name*: 0-0-1
- *Class*:    0-1-0
- *Id*:       1-0-0

## CSS Rules
CSS Rules são blocos de construção fundamentais de CSS. Cada regra especifica como determinado elemento deveria ser estilizado. Uma regra consiste em um _seletor_, que identifica o elemento a ser estilizado, e um bloco de declaração que contém uma ou mais pares de propriedade-valor que define os estilos que serão aplicados.
### Propriedades e valores
- Exemplo de propriedade:
  - `color`
- Exemplo de valor:
  - `rgb(0, 255, 0)`, `red`, `#00FF00`
### Seletores
- `#`
  - Usado para selecionar um ID
  - Especificidade: 1-0-0
- `.`
  - Usado para selecionar uma classe
  - Especificidade: 0-1-0
- `body` (nome de uma tag)
  - Usado para selecionar uma tag genérica
  - Especificidade: 0-0-1

## Comentários
Para fazer comentários em CSS deve-se usar `/*` `*/`. Se você utiliza o VSCode basta usar o atalho _CTRL + /_.

## Seletores simples
### Elemento
Usando o nome da tag, será algo mais genérico e aplicará em todos os elementos com esta tag. 
Ex.: 
```
p {
  font-size: 16px;
}
```
Todos os elementos `<p>` teram esta propriedade-valor atribuida acima.

### Classe
Usando o seletor de classe você faz o que deseja em elementos com esta classe. *Seletor mais recomendado para se usar em CSS.*
Ex.:
```
.nome-da-classe {
  background-color: white;
}
```
Todos os elementos com esta classe terão essa propriedade com este valor citado acima. 

### Id
Usando o seletor de Id você tem o mais alto nível de seletor simples em um CSS externo. Não recomendado apenas para estilização.
Ex.:
```
#nome-do-id {
  margin-right: 20px;
}
```
Em um documento HTML não se deve ter mais de 1 elemento com o mesmo Id, deve ser sempre exclusivo de apenas um elemento.

### Agrupamento de seletores
O agrupamento de seletores no css é bem simples basta usar uma `,` entre um seletor e outro.
Ex.:
```
p, .nome-da-classe, #nome-do-id, div {
  margin: 0
}
```
Assim todos esses elementos vão receber esta propriedade com este valor representado acima.

### Seletor universal
Com o seletor universal todos os elementos vão pegar as propriedades-valor especificado nele.
```
* {
  paddin: 0;
  box-sizing: border-box;
}
```
Muito usado para zerar os valores de margin e padding originais do browser e sobrescrever manualmente futuramente em determinadas tags.

## Seletores combinados
Seletores Combinados no CSS define a relação entre elementos baseados na posição na estrutura do documento. Eles permitem você _targetar_ elementos que são descendentes, filhos, irmãos adjascentes, ou irmãos no geral de outros elemetos. Isso fornece uma maneira poderosa de aplicar estilos baseados na hierarquia do HTML, indo alem dos simples seletores classe ou id.

### Descendente
O combinador descendente é apenas um ` `, um espaço em branco entre dois seletores. Usando o seletor descendente você vai consguir dar _target_ em todos os elementos dentro de um outro elemento que derem _match_ com o nome do seletor.
Exemplo 1:
```
div p {
  font-size: 20px;
}
```
Assim, com o exemplo acima todos os `<p>` dentro de uma `<div>` terão `font-size: 20px`. Mesmo se um paragrafo estiver dentro de outra tag ela ainda terá a estilização.

### Child
O combinador _child_ (filho) é utilizado usando `>` entre dois elementos e funciona apenas nos elementos que sao filhos diretos, ou seja, como no exemplo acima em descendente que qualquer paragrafo teria aquela estilização se dentro de uma `<div>`, aqui não acontece assim. Somente os elementos que estão na primeira 'camada' do elemento pai.
Ex.:
```
<div>
  <p> yada <p/>
  <nav>
    <p> yada <p/>
  <nav/>
<div/>
```
Neste cenário apenas o primeiro paragrafo seria estilizado, caso usasse o Exemplo 1.

### Next Siblling
O combinador Next Sibling (próximo irmão) é representado pelo símbolo `+`, ele seleciona um elemento que vem logo em seguida do seletor anterior.
Ex.:
```
<div>
  <p>Donald Duck<p>
  <p>Donald Duck lives in Duckburg.</p>
</div>

<div>
  <span><p>I will not be styled.</p></span>
  <p>I will not be styled.</p>
</div>

<p>Donald Duck's best friend is Mickey.</p> ←
<p>Some other text.</p>
```
Se eu usar `div + p` o unico paragrafo que seria selecionado seria o penultimo, por ele ser irmão direto de uma `<div>`.

### Subsequent Sibling
O combinador Subsequent Sibling (irmão subsequente) seleciona todos os irmãos que compartilham o mesmo pai. É utilizado o `~` como símbolo.
Ex.:
```
<article>
  <span>This is not red because it appears before any paragraph.</span>
  <p>Here is a paragraph.</p>
  <code>Here is some code.</code>
  <span>
    This span is red because it appears after the paragraph, even though there
    are other nodes in between.
  </span>
  <p>Whatever it may be, keep smiling.</p>
  <h1>Dream big</h1>
  <span>
    Doesn't matter how many or what kind of nodes are in between, all spans from
    the same parent after a paragraph are red.
  </span>
</article>
<span>
  This span is not red because it doesn't share a parent with a paragraph.
</span>
```
Se eu uso alguma estilização com `p ~ span` todos os elementos `<span>` que estão dentro do `<article>` serão estilizados por serem filhas do _article_. Caso estivessem dentro de um `<p>` por exemplo, já não seriam filhos da mesma tag e não funcionaria.

## Seletores de Atributos
Os seletores de atributos em CSS dão _target_ em elementos HTML baseado na presença ou valor de seus atributos. Eles permitem estilizar elementos mais precisamente que usando apenas nomes de tags ou classes. Por exemplo, eu posso selecionar todos os elementos com uma classe específica, ou apenas aquelas onde o valor do atributo dá _match_ com uma certa string.

- Atributo existent:
  - `[data-value] {}`
    
- Atributo tem este exato valor:
  - `[data-value="foo"]`
    
- Valor do atributo contém este valor em algum lugar nele:
  - `[data-value*="foo"]`
    
- Atributo tem este valor em algum lugar em uma lista separada por espaços:
  - `[data-value~="foo"]`

- Valor do atributo começa com isto:
  - `[data-value^="foo"]`
 
- Valor do atributo começa com isto em uma lista separada por ífens (`-`):
  - `[data-value|="foo"]`
 
- Atributo finaliza com este valor:
  - `[data-value$="foo"]`

 Obs.: Usar em aspas (`""`) vai funcionar em alguns casos, mas pode ter problema dependendo do browser. Então é recomendado sempre usar.


## Estilo de Texto
Estilo de Texto (TEXT STYLING) é o controle da aparência de elementos de texto em uma página web. Isto inclui propriedades que afetam a 'font' -family, -size, -weight, -color e -style. Também abrange propriedades para texto como text... -align, -decoration, -transform, letter-spacing e line-height.

### Fontes
- `font-family` no CSS são maneiras de especificar o tipo de letra usada para mostrar o texto em uma página web.
- `font-style` no CSS é usado para alterar a aparência de um texto, onde pode colocar como normal, oblique, italic.
- `font-weight` se refere a _thikness_ ou _boldeness_ dos caracteres. No CSS é uma propriedade que permite você especificar quão forte ou leve a fonte deve parecer. Os valores podem ser númericos (como 100, 400, 700) ou descritivos (como `normal`, `bold`, `lighter`, `bolder`) oferecendo controle sobre a ênfase visual do texto.
- `font-size` usado para determinar o tamanho do texto no browser. É uma propriedade fundamental que controla a legibilidade de elementos textuais. Existem varias unidades diferentes para fontes como: px, em, rem, %, vw/vh. É importante escolher o tamanho certo para a fonte para criar um apelo visual e um design acessível.
- `font-variant` usada para controlar a exibição de diferentes variações de uma fonte, como 0 riscado, glifos alternativos e outros.
- `font` usando esta propriedade você consegue atribuir o que quer sem precisar usar as propriedades citadas acima. Ex.: `font-family`, `font-weight` ... basta usar `font: "Arial", bold`.
Com o Google Fonts é possível encontrar diversas fontes gratuitas para nosso website. Ao invés de depender apenas da limitada quantidade de fontes que vem por padrão no computador, só precisa _linkar_ a fonte em um arquivo HTML e atribui-lá onde você quer usá-la.

### Algumas propriedades de textos
- `color` vai definir a cor do texto, podendo atribuir a cor de diversas formas como usando nome ("red" or blue ...), hexadecimal (#FF1199), RGB (255, 0, 0), RGBA (igual o RGB mas tem um valor no final para a transparência), HSL (_hue_, _saturation_, _lightness_) e HSLA (HSL + transparência).
- `direction` vai definir para que direção a escrita vai, da esquerda para direita (LTR) e tem direita para esquerda (RTL), usado para outras linguas como árabe e hebraico.
- `text-align` é usado para definir como o texto se alinhará, ex: `center`, `start`, `end`, `right`, `left`, `justify`.
- [text-decoration](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-decoration) no CSS se refere ao estilo aplicado ao texto para melhorar sua aparência ou transmitir um significado específico. Envolve linhas sobre o conteudo, sob o conteudo, riscando o conteudo (~asim~).
- [text-transform](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-transform) controla a 'capitalização' de texto. Pode transformar um texto em _uppercase_, _lowercase_, _capitalize_ ou deixar normal.
- [text spacing](https://www.codeguage.com/v1/courses/css/text-spacing) envolve ajudar o espaço entre caracteres, palavras e linhas de texto. Para isso é usado [`letter-spacing`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/letter-spacing), [`word-spacing`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/word-spacing) e [`line-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/line-height).
- [text-shadows](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-shadow) no CSS adiciona profundidade e interese visual criando uma cópia borrada por trás do texto. Multiplas sombras podem ser aplicadas em um só texto. usando `text-shadow` você vai indicar o desvio horizontal, desvio vertical, raio de desfoque e a cor da sombra.


## Opacidade
A [opacidade](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/opacity) no CSS controla a transparência de um elemento. Isso determina o quanto do background por trás do elemento será visível. Um valor de `1` significa que o elemento é opcao (sem transparência), enquanto o valor `0` significa que é invisível, completamente transparente. Então os valores entre `0` e `1` devem ser usados para quando quiser algum nível de transparência.

## Background
No CSS o termo "background" se refere a propriedade que controla a aparência visual do _background_ de um elemento. Isto inclui aspectos como _background_ _color_, _image_, sua posição (_position_), se ele se repete (_repeats) e seu tamanho (_size_). Estas propriedades permitem você adicionar interesse visual e customizar a aparência de seus websites.

- [Cor do background](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background-color) preenche o background de todo o elemento incluindo deu _padding_, mas não a borda ou a _margin_. Você pode especificar a cor usando o nome, hexadecimal da cor, valor RGB, entre outros formatos.
- [Imagem de background](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background-image) é setada por uma url `background-img: url("link.png");`, mas pode ter outros valores separados por uma `,`. Alguns valores são: `linear-gradient(to top, color1, colo2)` (para colocar um 'degradê' linear, pode escolher a direção "to bottom", "to right" "to left") e `radial-gradient` (para coocar um 'degradê' circular, direções são "0deg"(top), "90deg"(right), "180deg"(bottom), "270deg"(left)).
- [Posição do background](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background-position) no CSS controla onde uma imagem de _background_ é colocada dentro do seu elemento. É possível usar valores como `right`, `left`, `bottom`, `top` e `center` ou também valores númericos (px, %, etc) para setar a posição exata.
- [Anexo de background](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/background-attachment) essa propriedade vai controlar como a imagem de fundo se comporta quando a página é _scollada_. Pode escoher valores como `fixed` que a imagem fica estática, `scroll` que vai subir junto da página e `local` a imagem é local ela vai subir junto com o elemento.

## Cores
- RGB: pode ser setada usando valores inteiros (variam de 0 a 255) ou % `rgb(0, 0, 0)`.
- HSL: mais fácil de ser ajustado pois primeiro é setada pela tonalidade (0 a 360 graus), depois sua saturação (0 a 100%) e iluminação (0 a 100%).
- HEX: valores hexadecimais têm 6 digitos e um `#` como prefixo.
- Cores nomeadas: cores mais básicas pode usar apenas seus nomes (red, black, white ...).
- RGBA, HSLA: a adição do sufixo `A` representa sua opacidade.

## Box Model
