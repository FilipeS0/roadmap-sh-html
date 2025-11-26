# HTML
Minha jornada como fullstack... 
Comecando por HTML

## O que é Markup Language
É um tipo de linguagem computacional, assim como _Programming Language_ também é. 
Ex.: 
- HTML 
- XML 
- XHTML 
- SVG 
- markdown

## Ferramentas básicas para um FrontEnd Developer
### HTML
Extends for HyperText Markup Language. É a linguagem utilizaada para fazer a estrutura de uma pagina web, por exemplo. HTML é estático e usado para mostrar o conteudo/corpo da pagina.

### CSS 
Extends for Cascade Styling Sheets. É utilizada para estilizar a pagina web, pois sem o CSS o HTML é mbem rústico, apenas uma pagina preto e branco. Com o CSS é possivel mudar as cores, introduzir animações ao passar o mouse por cima de elementos, alterar tamanho de fontes e diversas outras coisas.

### JavaScript
EcmaScript6 ou JavaScript popularmente conhecido, esta é uma linguagem de programação, é o que traz a interatividade para webpages, é com ele que um site fica responsivo e dinamico.

## Como a Internet funciona
A internet é um composto de _networks_. 
_Network_ é um composto de aparelhos conectados, por exemplo em uma casa temos celulares, TVs, computadores e qualquer outra coisa que possa ter conexão a internet faz parte de uma Network local.

### O que é HTTP
HTTP extends for _HyperText Transfer Protocol_ (Protocolo de Transferência de Hiper Texto), é o que permite um navegador web fazer requests do cliente para o servidor e mandar respostas do servidor para o cliente. Existem protocolos como GET, POST, DELETE ... Também existem tipos diferentes de HTTP, como o HTTPS (Protocolo mais seguro que evita que requests sejam interceptados no meio do caminho), HTTP/2 (Versão mais usada atualmente) é uma atualização do muito utilizado HTTP/1.1 e também surgiu o HTTP/3 que ainda vem ganhando popularidade (preciso procurar saber melhor sobre este).

### Domain name
Nome do domínio, um exemplo google.com, onde ao invés de usar um ip onde só são numeros e pontos a gente usa um nome mais amigavel, facil de memorizar. Os DNS traduzem os nomes para endereços de IP, o que ajuda na acessibilidade. Por isso não precisamos buscar sites usando 197.124.122.244.

### Hosting
Hospedagem, existem algumas maneiras de hospedagem são:
#### VPS
Extends for _Virtual Private Server_ Com uma VPS você tem melhor flexibilidade de alocação de recursos. Aqui é possível aumentar ou reduzir o processamento para determinados momentos do dia, ou da semana, ou um período em especial como por exemplo Black Friday, onde muitos sites precisam de mais processamento devido ao grande tráfego online.

#### Servidor compartilhado
Neste tipo de servidor sua aplicação web está dividindo os recursos de um servidor com outras aplicações webs. O ideal é usar este tipo de servidor apenas para pequenos projetos onde não haverá grande volume de acessos, como: blog pessoal, projeto pessoal pequeno... Pois como mencionado anteriormente por ser um servidor compartilhado ele pode ter mais instabilidades caso aconteça de um dos web apps hosteados nesse server tenha um volume maior que os outros ele pode consumir mais processamento que deveria e assim limitando ainda mais os outros que ali estão. Também caso aconteça um DDOS, um ataque Hacker em algum desses apps que estão nesse mesmo server sua aplicação ficará instável também, podendo ficar offline por conta de outras aplicações...

#### Servidor dedicado
Este é o que grandes empresas necessitam para manter suas aplicações online, pois normalmente elas terão grande fluxo de dados sendo enviado, o que vai consumir muito processamento, também o fato de não querer ter instabilidade por motivos de terceiros faz desta uma boa opção para quem não pode deixar suas aplicações offline.

### DNS
Extends for Domain Name System (Sistema de Nomes de Domínios). Traduz dominios de sites como github.com para 192.30.252.0/22 por exemplo, ou seja, o usuário digita o nome do site o web browser "pergunta" ao DNS que endereço é esse o DNS então traduz e manda o endereço de IP que aponta para esse Domain Name. 

### Browsers
Navegadores, são eles:
- Chrome
- Safari
- Opera
- Firefox
Estes que processam os arquivos HTML, CSS, JavaScript (engine V8) e mostram para o usuario.

### SEO
Search Engine Optimization (Otimização de mecanismos de procura), é a prática de melhorar sua página web para que mecanismos de busca a encontrem mais facilmente, por exemplo uma pagina bem estruturada com as devidas tags e com um conteudo interessante é essencial para ficar nas primeiras paginas dos sites de pesquisa. Por isso é importante trabalhar bem SEO para que sua webpage se saia bem.

## Tags Básicas
- !DOCTYPE: ```<!DOCTYPE>``` não é uma tag _HTML_, ela é usada para o browser identificar que é um documento HTML.
- ```<html>``` É a tag raiz, onde contém todas as outras tags html.
- ```<body>``` O corpo do arquivo HTML, onde se encontra todo o conteúdo.
- ```<head>``` Onde se encontram os metadados.

## Tags Textuais
- Headings: começando do ```<h1>``` e indo até o ```<h6>```, onde h1 seria o assunto principal de uma pagina e quanto os seguintes headings seriam subtopicos referentes ao principal.
- ```<title>```: titulo da página, esse se encontra dentro da tag ```<head>```.
- ```<p>```: Usada para fazer paragráfos.
- ```<hr>```: Vai mostrar uma linha horizontal no navegador, usada para fazer uma separação na pagina.
- ```<br>```: Usado para quebrar uma linha de um paragrafo
- ```<srong>```/```<em>```: Têm valor semantico para dar força/ênfase a determinada parte de um texto.
- ```<a>```: Anchor tag, tag âncora. Pode ser usada para referenciar alguma coisa na propria página (referenciando um id ou algo assim) ou encaminhar o usuario para outra pagina (referenciando um link externo mesmo).
- ```<mark>```: Para marcar uma parte de um texto como se fosse um marca texto sobre.
- ```<pre>```: Utilizada para usar um texto preformatado onde não quer mudar a estrutura em que foi escrito (um exemplo é um poema, um codigo de programação).
- ```<sup>```/```<sub>```: Usadas para representar calculos matemáticos ou textos que ficam acima/abaixo da linha comum.

## Agrupamento de Texto
- ```<div>```: Usada para criar divisorias no corpo do documento HTML. Em uma div vc coloca tags textuais usando a div como um container.
- ```<span>```: Usada para criar containers Inline level, ou seja, que não quebra a linha ou separa o texto do restante. Pode ser usado para estilizar uma parte do texto e diferenciar das demais.

## Atributos padrão
- Id : Deve ser único, nunca usar mais de um mesmo id em outros elementos. Id é o seletor de mais alto nível de especificidade quando comparado com o restante.
- Class : Diferente do Id, classes podem ser atribuidas a diversos elementos que você queira compartilhar do mesmo comportamento ou estilização. Também tem um nível abaixo em especificidade em relação ao Id.
- Data Attributes : São para tags que permitem comportamentos diferentes, um exemplo é o button:submit, submit seria o atributo, então é uma forma de especificar também. Aqui tem o mesmo nível de especificidade de uma classe, então quem prevalece é quem vem por ultimo.

## Tipos de listas
- `<ul>` : lista desordenada, onde a lista não precisa de uma ordem numerica ou algo do tipo, são mostrados itens com _bullets points_ e contem itens com a tag `<li>`.
- `<ol>` : lista ordenada, onde cada item da lista é enumerado. Contém tipos diferentes, numeral (1. 2. ...), alfabetico (a. b. ... ou A. B. ...), romano (i. ii. ... ou I. II. ...).
- `<dl>` : lista de definição, esta é a diferente das demais, pois seus itens não são em `<li>`, mas em outras tags como `<dt>` Definition term (termo de definição), onde é colocado o termo e `<dd>` (definition description) onde é colocado a descrição do termo.
(Listas podem ser aninhadas sendo uma contida em uma outra).

## Tag para Tabela
`<table>` é uma tag usada para mostrar tabelas, pode ser composta por `thead`, `tbody`, `tfoot` que serão a composição mais robusta da tabela, mas a parte principal são as tags: 
- `<tr>` para criar uma nova linha, aqui que serão contidas as proximas tags.
- `<th>` para ser Header, o nome de uma coluna ou linha.
- `<td>` onde preenche o dado de uma celula.

## Medias tags
- `<img>` para imagens, usando o atributo `src=""` vai referenciar onde está a imagem e mostrar no documento HTML.
- `<video>` basicamente como uma imagem para pegar o arquivo e mostrar, porém com diversas funcionalidades extras, onde é possivel settar para ao abrir a pagina web o video iniciar tocando, onde pode colocar seletor de volume (baixar e aumentar), também é possível colocar o botão de play/pause, e diversas outras funcionalidades.
- `<audio>` assim como o video também tem diversas funcionalidades, autoplay, volume, pause/play.
- Content Security Policy (CSP), é uma segurança padrão usada para previnir _cross-site scripting_ (XSS). É uma boa prática não importar imagens, videos, audios ... de outros sites, pois pode acontecer um clickjacking ou ataque de injeção de codigos. Mas também o site que está _hosteando_ a imagem pode trocar esta imagem e colocar algo não relacionado ao esperado.
- `<iframe>` pode conter um outro elemento HTML, um exemplo clássico é trazer um video do YouTube para seu website sem que o usuario precise acessar outra pagina ou seja redirecionado para assistir.

## Forms
### Atributos do formulario
Formulários existem  `method=GET` e `method-POST`. 
- `GET` é utilizado para pedir dados do servidor, quando usado é perceptivel pois os dados ficam na URL do site e há um limite de caracteres. 
- `POST` é utilizado para enviar dados para um servidor, para criar ou atualizar um recurso. Por exemplo enviando uma senha, dados de uma compra, upload de imagem.
Também tem o atributo `action="pagina-para-lidar-com-formulario"`.
### Tags para usar em um formulário
As principais tags são: 
- `<label>` Basicamente é o nome do caixa do formulário, é o que diz o que uma caixa de input espera que o usuario escreva. Ex.: email, senha ... Detalhe que esta tag pode referenciar um `<input>`, ou seja, ao clickar em um label o teclado estará habilitado para digitar na barra de texto em que ele está referenciando.
- `<input>` o input existem em diversos tipos como: submit, reset, email, password, name, button, checkbox, color, date, tel, number, range, search, radio, color, file... E cada um vai ter um comportamento e um tipo de entrada que é aceitável. Cabe se aprofundar melhor neste em uma outra hora.
- `<textarea>` é um tipo de input também, aqui é para grandes textos.
- `<select>` usado junto com a tag `<option>` para escolher, por exemplo, cidade, país ...

### Validação de formulários 
Validar os campos preenchidos no formulário é importante, para que os dados recebidos sejam precisos e aceitáveis. Para isso é usado alguns atributos dentro das tags de `<input>`. 
Ex.: 
- atributo `required`: para que o formulário só possa ser enviado caso este campo de input seja preenchido.
- `min-length` e `max-length`: exige um numero mínimo de caracteres e delimita um numero máximo.
- `pattern`: específica um determinado padrão para o dado que está sendo inserido. ex.: telefone (xx) xxxxx-xxxx.
- `min`, `max`, `step`: especifica o minimo, máximo de valor em input númerico, e o incremento, por valor começando do minimo.

## Marcação Semântica
Usando tags semânticas torna a página mais acessível para humanos e máquinas, por isso é importante aprender tags e suas funções para que o que você está construindo seja melhor de se ler, melhor de se encontrar. Só usando as tags corretas e uma boa estrutura você consegue bons resultados em mecanismos de busca.

### Citação/Aspas
- `<abbr>` Abreviação para alguma sigla, usar o atributo `title` com o nome do que a abreviação extende para.
- `<cite>` Usada para fazer citação de um livro, filme, fala, letra de música, enfim, para trazer uma citação. As letras ficam em italico.
- `<blockquote>` Representa citação de uma seção de um outro texto. Pode ser usada junto de uma tag `<cite>` (para trazer a url da citação).
- `<address>` Usado para informar o contato de um autor ou dono de um documento ou artigo. Pode conter endereço físico, endereço de email, telefone e link de redes sociais. Tipicamente usada no _footer_ de uma pagina.
- `<q>` Parecido com o _blockquote_, mas essa tag é melhor utilizada para pequenas citações, até pq diferente da `<blockquote>`, a `<q>` tag é inline level.

### Tags para layout
`<header>` Comumente compondo barra de navegação, logo, barra de pesquisa. É a seção que fica no topo do arquivo HTML.
`<
