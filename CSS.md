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
O [box model](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model) descreve como elementos em uma webpage são estruturados como caixas retangulares. Cada caixa consiste de conteúdo (texto, imagem, etc), _padding_ (espaço ao redor do conteudo), uma _border_ (uma linha ao redor do _padding_) e uma _margin_ (espaço ao redor da borda). É crucial entender _box-model_ para controlar o tamanho e espaçamento de elementos em uma _webpage_.

## Padding
[Padding](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/padding) se refere ao espaço entre o conteudo de um elemento e sua borda. Isso essencialmente cria uma 'almofada' ao redor do conteúdo dentro da box do elemento. Você pode controlar a quantidade de _padding_ em todos os quatro lados de um elemento (top, right, bottom, left) individualmente ou settar um valor uniforme para todos os lados.

## Margin
[Margin](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/margin) em CSS define o espaço ao redor da borda de um elemento HTML. Isso cria um _gap_ entre o elemento e outros elementos ao redor em uma pagina web. As margens podem ser _settadas_ em todos os 4 lados de um elemento e pode ter valores negativos ou positivos.

## Width/Height
[Largura e altura](https://www.programiz.com/css/width-height) em CSS define o tamanho da area de um conteudo. a propriedade `width` setta o espaço horizontal que um elemento ocupa, enquanto a propriedade `height` seta o espaço vertical. Estas propriedades podem ser especificadas usando vários valores unitários como px, %, ou palavras-chave como `auto`.

## Border
No CSS, a propriedade borda define a linha que rodeia o conteudo e o _padding_ de um elemento HYML. Isso controla o estilo da borda (tipo `solid`, `dashed`, ou `dotted`), largura (grossura da borda) e cor. Você pode settar todas estas propriedades de uma vez usando o atalho `border`, ou individualmente usando `border-style`, `border-width` e `border-color`.

## Outline
No CSS, a propriedade [outline](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/outline) desenha uma linha ao redor do elemento, fora da borda. Diferente das bordas, _outlines_ não afetam as dimensões do elemento ou a posição no layout. eses são principalmente usadas para destacar elementos, frequentemente por propositos de acessibilidade como indicar foco. Você pode controlar o estilo, cor, e largura do _outline_. Tem os mesmos valores de uma borda `outline-style`, `-color` e `-width`.

## Box Shadows
[Box shadows](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/box-shadow) no CSS são efeitos visuais que adicionam profundidade e dimensão ao elemento criando uma sombra ao redor de seus quadros. Estas sombras podem ser customizadas em termos de cores, desvio (distancia horizontal e vertical), raio de desfoque (blur), e raio de propagação (spread), permitindo designers simular várias condições de iluminação e criar interfaces visualmente apelativas. 

## Unidades CSS
[CSS Units](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units) define o tamanho do elemento e propriedades em uma pagina web. eles especificam como medidas como width, height, font size e margins são interpretadas pelo browser. Estas unidades podem ser absolutas, como px ou cm, ou podem ser relativas, como em, rem, ou viewports (vw, vh), permitindo flexibilidade e responsividade do layout que adapta a diferentes tamanhos de telas e resoluções.

### Absolute x Relative units
Unidades absolutas no CSS representam medidas fixas, como pixels(px) ou centimetros(cm), e vai sempre renderizar no mesmo tamanho sem considerar o tamanho da tela ou outros fatores. Unidades relativas, por outro lado, são baseadas em outros valores, como o tamanho da fonte (font-size) dos elementos pais (em), a largura da janela (vw), ou o tamanho da fonte do elemento raiz (rem), permitindo layouts mais flexiveis e responsivos.

### Unidades com funções
Unidades com funções no CSS permite calcular valores dinamicamente para propriedades usando funções como `calc()`, `min()`, `max()` e `clamp()`. Estas funções te habilita fazer operações matematicas e comparações diretamente dentro do CSS, fazendo seus designs mais flexiveis e responsivos se adaptando a diferentes tamanhos de telas e contextos.

## Display
A propriedade display no CSS controla como um elemento é renderizado em uma página web, especificamente definindo seu tipo de caixa e como ela interage com outros elementos. Isso determina se um elemento é tratado como um elemento `block-level` (pegando toda a _width_ disponivel), um elemento `inline` (fluindo dentro do texto), ou algo diferente, como uma tabela ou um container _grid_.

### Inline
A propriedade `display: inline;` no CSS é usada para especificar que um elemento deveria ser exibida como um elemento _inline_. Elementos _inline_ flui pelo conteudo como um texto dentro de um paragrafo. Um elemento _inline_ ocupa somente a largura suficiente para conter o conteudo. Setar valores de _width_ e _height_ não tem efeito em um elemento _inline_.

### Block
A propriedade `display: block;` no CSS faz um elemento se comportar como um elemento `block-level`. Isso significa que ele usará toda a largura disponível para si, começando de uma nova linha e empurrando elementos ao seu lado para uma nova linha também. Elementos do tipo _block_ geralmente compõe a maior parte estrutural de uma página web.

### Inline-Block
A propriedade `display: inline-block` vai ter as característivas dos dois citados acima, vai ser inline e vai conseguir setar altura e largura.

### None
Se um elemento está com `display: none;` é como se ele não existisse, ele não vai usar nenhum espaço de uma página web.

### Visibility
Se um elemento tem a propriedade `visibility: hidden;` ele desaparece da página mas o espaço que ele ocupava não some igual no `display: none;`.

## Position
Posição (position) no CSS controla como um elemento é colocado dentro de um 'container' ou do documento em si. Isso permite você definir precisamente onde um elemento aparece na página, influenciando sua relação com outros elementos e o layout geral. Diferentes valores de posições oferecem variados niveis de controle.

### Posição relativa
Posição relativa permite deslocar um elemento de sua posição normal no fluxo do documento. Ao invés de ser fixado em um local, o elemento é movido em relação a onde deveria estar se ele estivesse estaticamente posicionado. Este movimento não afeta o posicionamento de outros elementos ao seu redor, eles se comportam como se o elemento ainda estivesse em sua posição original. Daí pode especificar a quantidade de movimento usando as propriedades `top`, `right`, `bottom` e `left`.

### Posição absoluta
Posição absoluta em CSS permite posicionar com precisão um elemento em relação a seu ancestral posicionado mais proximo (um ancestral com valor de posição diferente de `static`). Se esse tipo de ancestral não existe, o elemento é posicionado em relação a seu container inicial, que é normalmente o elemento `<html>`. Elementos com a `position: absolute` são removidos do fluxo normal do documento, o que significa que ele não altera a posição dos elementos ao seu redor.

### Posição Pegajosa (Sticky)
A Sticky position no CSS é um híbrido de posição relativa e fixa. Um elemento com `position: sticky;` é inicialmente posicionado relativamente, mas quando o usuário _scrolla_ para um ponto onde o elemento normalmente sairia da tela, ele se torna fixo, grudando no deslocamento especificado (ex.: `top: 0`) até o limite do bloco que o contém seja alcançado.

### Posição fixa
Posição fixa em CSS permite que um elemento seja travado em relação a janela do navegador. Isto significa que mesmo quando o usuário _scrolla_ a página, o elemento continua visível na mesma posição na tela. É frequentemente usado para barras de navegação, rodapés ou outros elementos que precisam persistir na tela.

### Posição estática
Posição estática é o valor padrão que um elemento recebe na propriedade `position`. Elementos com posições estáticas são renderizados na ordem que eles aparecem no HTML, seguindo o fluxo normal do documento. Eles não podem ser movidos usando as propriedades `top`, `right`, `bottom` e `left`.

## Z-Index / Stacking Context
Z-index em CSS controla a ordem de empilhamento vertical dos elementos que se sobrepõem. Elementos com um valor z-index maior vai aparecer na frente de elementos com um valor menor. O contexto de empilhamento (stacking context) é uma conceituação tridimensional de elementros HTML ao longo de um eixo z imaginario em relação ao visualizador, que determina a ordem em que o elemento aparece, na frente ou atrás de outros.

## CSS Specificity
A especificidade de CSS é o conjunto de regras que browsers usam para determinar qual declaração CSS se aplica em um elemento quando existe conflito de multiplas regras. Isso é essencialmente um sistema de peso que prioriza determinados seletores de CSS sobre outros, garantindo que o estilo mais relevante seja aplicado. Entender especificidade é crucial para controlar como seus estilos de CSS são aplicados e resolver problemas inesperados.

## Tabelas
No CSS tabelas são usadas para formatar dados tabulares em uma pagina web, organizando informações dentro de linhas e colunas. O CSS fornece propriedades para controlar a aparência de tabelas, incluindo bordas, espaçamento, alinhamento e estilização de células individuais, linhas e colunas. Estas propriedades habilitam desenvolvedores criar apelos visuais e tabelas bem estruturadas que mostram dados de forma eficaz.
Algumas propriedades:
* `border-collapse`
* '`border-spacing`
* `caption-side`
* `empty-cells`
* `table-layout`

## Listas
Listas no CSS são usadas para estilizar o elemento lista do HTML, como as `ul`, `ol` e `dl`. O CSS fornece propriedades para controlar a aparência de marcadores de listas (_bullets_ ou numeros), a posição deles e o estilo no geral dos itens na lista. Isso permite customizar a aparencia visual da lista além do estilo padrão do navegador.

## Imagens e Filtros
O CSS permite incorporar imagens em seus web designs e manipular sua aparência. Você pode usar CSS para controlar o tamanho da imagem, a posição e como ela interage com o conteudo ao seu redor. Além disso, os filtros de CSS permitem a aplicação direta de efeitos visuais, como desfoque, ajuste de cores e transformações, para imagens, deste modo melhorando seu apelo visual sem requerer edições de imagens de softwares externos.

## Pseudo-classes
Pseudo-classes no CSS são palavras-chaves adicionadas ao seletor que especifica um estado especial do elemento selecionado. Eles deixam você estilizar um elemento baseado em coisas como interações do usuário (ex: colocar o mouse em cima de um hyperlink), sua posição na estrutura do documento (ex: o primeiro elemento filho usando `first-child`) ou outras caracteristicas de elemento. Eles permitem você aplicar estilos aos elementos dinamicamente sem precisar modificar o HTML ou usar JavaScript.

## Pseudo-elementos
Pseudo-elementos no CSS deixam você estilizar partes especificas de um elemento. Eles permitem você adicionar estilos a elementos que não existem defato na estrutura do HTML, como a primeira linha de um parágrafo ou o conteúdo antes ou depois de um elemento. Isto é feito usando dois pontos duas vezes (::) seguido pelo nome do pseudo-elemento.

## Flow Layout
O fluxo do layout é a forma padrão que elementos são posicionados em uma pagina web. Elementos são mostrados um após o outro, como palavras em uma frase, seguindo o fluxo natural do HTML. Elementos _block-level_ tomam a largura completa disponível e começam em uma linha nova, enquanto elementos _inline_ fluem dentro do conteúdo, ocupando apenas o espaço necessário.

### Floating Elements
Elementos flutuantes no CSS permitem você retirar um elemento do fluxo natural do documento e posicioná-lo à esquerda ou à direita do seu container. Outros conteúdos seguirão ao redor do elemento flutuante. Esta tecnica é comumente usada para criar layouts onde textos são quebrados ao redor de imagens ou para posicionar elementos lado a lado.

### Layout Multicoluna
Layout multicolunas no CSS permite você dividir um bloco de conteudo em multiplas colunas, similiar ao layout de jornais. Este recurso possibilita texto e outros conteudos fluírem automaticamente de uma coluna para a próxima, melhorando a legibilidade e fazendo o uso eficiente do espaço de tela, especialmente para artigos longos ou listas. Você pode controlar o numero de colunas, o _gap_ entre elas e uma regra (linha) entre as colunas para uma separação visual.

### Flexbox
Flexbox é um modelo de layout do CSS que fornece uma maneira eficiente de organizar, alinhar e distribuir espaço entre itens em um conteiner, mesmo quando seus espaços são desconhecidos ou dinâmico. Ele simplifica a criação de layouts complexos, oferecendo ferramentas poderosas para controlar a direção, a ordem, o tamanho e o alinhamento dos elementos dentro de um conteiner. Flexbox é particularmente útil para projetar interfaces de usuario responsivas e adaptaveis.

### Grid Layout
Grid Layout é um sistema de layout bidimensional para o CSS, possibilitando você controlar a posição e tamanho de elementos em um _grid_ conteiner. Ele divide uma pagina web em linhas e colunas, permitindo posicionamento preciso de conteudo e criando layouts complexos com facilidade. Este metodo oferece flexibilidade e controle sobre a disposição de elementos, superando metodos como _floats_ ou _position_.

## Animações
### Transforms
Transforms no CSS permite você alterar o formato e a posição de elementos em um espaço bi ou tridimensional. Isto inclui operações como _rotação_ (rotate), _dimensionamento_ (scale), _distorcer_ (skew) e translatar (_translate_) elementos, fornecendo uma maneira de criar efeitos visualmente atraentes e manipular o layout sem afetar o fluxo do documento subjacente.

### Transitions
Transições no CSS permite você mudar suavemente valores de propriedades durante um período especificado. Ao inves de uma mudança abrupta, uma transição cria um efeito gradual quando uma propriedade do CSS muda, como ao passar o mouse sobre um elemento ou quando uma classe é adicionado ou removida. Isto adiciona um polimento visual e melhora a experiencia do usuario fazendo interações mais fluidas e responsivas.

### Keyframes
Animação Keyframe no CSS permite você controlar os passos intermediários em uma sequencia de animação CSS. Ao inves de só definir o estado do começo e do fim, você pode especificar vários pontos (keyframes) ao longo da linha do tempo da animação, definindo os estilos que um elemento deveria ter em cada ponto. Isto fornece um controle sobre como a aparencia de um elemento muda com o tempo, permitindo animações complexas e visualmente atraentes.

## Media Queries
