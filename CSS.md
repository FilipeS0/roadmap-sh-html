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
