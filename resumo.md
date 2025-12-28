# Recursos para eu sempre usar

## CSS
### Normalize
Usar o cdn normalize para deixar a pagina web sempre igual em qualquer browser. 
[Link aqui](https://cdnjs.com/libraries/normalize)
Para usar o Normalize basta acessar o link acima, copiar o cdn e colar na seção `<head>` do documento HTML.

### Importando fontes
Para performance, use <link> no <head> para fontes externas. Para fontes locais, use @font-face no CSS. Evite @import no topo do CSS por questões de performance, embora seja uma opção de organização. 
- Usando `<link>`
```
<head>
  <link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="fonts.googleapis.com" rel="stylesheet">

  <style>
    body {
      font-family: 'Inter', 'sans-serif';
    }
</head>
```

- Usando `@font-face`
```
@font-face {
  font-family: 'Minha Fonte';
  src: url('minha-fonte.woff2') format('woff2'),
       url('minha-fonte.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}

body {
  font-family: 'Minha Fonte', sans-serif;
}
```
Obs: Usar aspas nos nomes das fontes por convenção

## Requisicao HTTP
Eh preciso de um IP: `https://link.com`; e um Path: `/api/v2/algo`.
Tem tambem o tipo de requisicao: GET | POST | PUT | DELETE | PATCH.
Entao funciona da seguinte forma: eu vou dizer o ip onde vou fazer a solicitacao, o caminho especifico do ip e o metodo que eu estou requisitando

## Optimizar fotos
Sempre buscar optimizar as fotos para que a pagina fique bem mais leve, sempre que for usar uma imagem, optimizar antes.
(Use este link)[https://tinypng.com/]
