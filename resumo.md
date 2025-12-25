# Recursos para eu sempre usar

## Normalize
Usar o cdn normalize para deixar a pagina web sempre igual em qualquer browser. 
[Link aqui](https://cdnjs.com/libraries/normalize)
Para usar o Normalize basta acessar o link acima, copiar o cdn e colar na seção `<head>` do documento HTML.

## Importando fontes
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
