---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/rtl.md
revision: 1299b163c7526b0e6892856d87e8710bc195d7f5
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

layout: docs
title: RTL
description: |
  Aprenda como habilitar o suporte para texto da direita para a esquerda no
  Bootstrap em nosso layout, componentes e utilitários.
group: getting-started
toc: true
---

# RTL

Aprenda como habilitar o suporte para texto da direita para a esquerda no
Bootstrap em nosso _layout_, componentes e utilitários.
{: .lead }

## Familiarize-se

Recomendamos que você se familiarize com o Bootstrap primeiro lendo nossa página
[Comece a usar o Bootstrap](../comecando/introducao.md).
Depois de passar por ela, continue lendo aqui para saber como habilitar o RTL.

Você também pode querer ler sobre [o projeto RTLCSS](https://rtlcss.com/), pois
ele influencia nossa abordagem ao RTL.

**O recurso RTL do Bootstrap ainda é experimental** e evoluirá com base no
retorno fornecido pela pessoa usuária.
Viu algo ou tem uma melhoria para sugerir?
[Abra uma _issue_]({{ repo }}/issues/new/choose), adoraríamos saber o que você
tem a dizer.
{: .callout .warning }

## HTML necessário

Há dois requisitos rigorosos para habilitar RTL em páginas que usam o Bootstrap.

1. Definir `dir="rtl"` no elemento `<html>`.
2. Adicionar um atributo `lang` apropriado, como `lang="ar"`, no elemento
   `<html>`.

A partir daí, você precisará incluir uma versão RTL do nosso CSS.
Por exemplo, aqui está a folha de estilo para nosso CSS compilado e minimizado
com RTL habilitado:

```html

<link rel="stylesheet" href="{{ cdn.css_rtl }}"
      integrity="{{ cdn.css_rtl_hash }}" crossorigin="anonymous">
```

### Modelo inicial

Você pode ver os requisitos acima refletidos neste modelo inicial RTL
modificado.

```html
<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <!-- Meta tags necessárias -->
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <!-- CSS do Bootstrap -->
  <link rel="stylesheet" href="{{ cdn.css_rtl }}"
        integrity="{{ cdn.css_rtl_hash }}" crossorigin="anonymous">

  <title>مرحبًا بالعالم!</title>
</head>
<body>
<h1>مرحبًا بالعالم!</h1>

<!-- JavaScript opcional; escolha um dos dois! -->

<!-- Opção 1: Pacote Bootstrap com Popper -->
<script src="{{ cdn.js_bundle }}" integrity="{{ cdn.js_bundle_hash }}"
        crossorigin="anonymous"></script>

<!-- Opção 2: JavaScript separado do Popper e Bootstrap -->
<!--
<script src="{{ cdn.popper }}" integrity="{{ cdn.popper_hash }}" crossorigin="anonymous"></script>
<script src="{{ cdn.js }}" integrity="{{ cdn.js_hash }}" crossorigin="anonymous"></script>
-->
</body>
</html>
```

### Exemplos de RTL

Comece com um dos nossos vários [exemplos de RTL](../examples/index.md#rtl).

## Abordagem

Nossa abordagem para construir suporte a RTL no Bootstrap vem com duas decisões
importantes que impactam como escrevemos e usamos nosso CSS:

1. **Primeiro, decidimos construí-lo com o projeto
   [RTLCSS](https://rtlcss.com/).**
   Isso nos dá alguns recursos poderosos para gerenciar alterações e
   substituições ao mudar de LTR para RTL.
   Também nos permite construir duas versões do Bootstrap a partir de uma base
   de código.
2. **Segundo, renomeamos um punhado de classes direcionais para adotar uma
   abordagem de propriedades lógicas.**
   A maioria de vocês já interagiu com propriedades lógicas graças aos nossos
   utilitários _flex_ — eles substituem propriedades de direção como `left` e
   `right` em favor de `start` e `end`.
   Isso torna os nomes e valores de classe apropriados para LTR e RTL sem
   nenhuma sobrecarga.

Por exemplo, em vez de `.ml-3` para `margin-left`, use `.ms-3`.

Trabalhar com RTL, por meio de nosso arquivo fonte Sass ou CSS compilado, não
deve ser muito diferente de nosso LTR padrão.

## Personalize a partir do código-fonte

Quando se trata de [personalização](../customize/sass.md), a maneira preferida é
aproveitar variáveis, mapas e _mixins_.
Essa abordagem funciona da mesma forma para RTL, mesmo que seja pós-processado a
partir dos arquivos compilados, graças à forma
[como o RTLCSS funciona](https://rtlcss.com/learn/getting-started/why-rtlcss/).

### Valores RTL personalizados

Usando [diretivas de valor RTLCSS](https://rtlcss.com/learn/usage-guide/value-directives/),
você pode fazer uma variável gerar um valor diferente para RTL.
Por exemplo, para diminuir o peso de `$font-weight-bold` em toda a base de
código, você pode usar a sintaxe `/*rtl: {value}*/`:

```scss
$font-weight-bold: 700 #{/* rtl:600 */} !default;
```

O que geraria o seguinte para nosso CSS padrão e CSS RTL:

```css
/* bootstrap.css */
dt {
    font-weight: 700 /* rtl:600 */;
}

/* bootstrap.rtl.css */
dt {
    font-weight: 600;
}
```

### Pilha de fontes alternativas

Caso esteja usando uma fonte personalizada, esteja ciente de que nem todas as
fontes suportam o alfabeto não latino.
Para alternar da família Pan-europeia para a família Arábica, pode ser
necessário usar `/*rtl:insert: {value}*/` na sua pilha de fontes para modificar
os nomes das famílias de fontes.

Por exemplo, para alternar da fonte `Helvetica Neue` para LTR para
`Helvetica Neue Arabic` para RTL, seu código Sass poderia ser assim:

```scss
$font-family-sans-serif: Helvetica Neue #{"/* rtl:insert:Arabic */"},
  // Família de fontes genéricas multiplataforma (fonte padrão da interface da
  // pessoa usuária)
system-ui,
  // Safari para macOS e iOS (San Francisco)
-apple-system,
  // Chrome < 56 para macOS (San Francisco)
BlinkMacSystemFont,
  // Windows
"Segoe UI",
  // Android
Roboto,
  // Última alternativa básica para web
Arial,
  // Linux
"Noto Sans",
  // Última alternativa sem serifa
sans-serif,
  // Fontes de emoji
"Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji" !default;
```

### LTR e RTL ao mesmo tempo

Precisa de LTR e RTL na mesma página?
Graças aos
[Mapas de _String_ RTLCSS](https://rtlcss.com/learn/usage-guide/string-map/),
isso é bem direto.
Envolva suas regras `@import` em uma classe e defina uma regra de renomeação
personalizada para RTLCSS:

```scss
/* rtl:begin:options: {
  "autoRename": true,
  "stringMap":[ {
    "name": "ltr-rtl",
    "priority": 100,
    "search": ["ltr"],
    "replace": ["rtl"],
    "options": {
      "scope": "*",
      "ignoreCase": false
    }
  } ]
} */
.ltr {
  @import "../node_modules/bootstrap/scss/bootstrap";
}

/*rtl:end:options*/
```

Depois de executar o Sass e depois o RTLCSS, cada seletor em seus arquivos CSS
será precedido por `.ltr` e `.rtl` para arquivos RTL.
Agora você pode usar ambos os arquivos na mesma página e simplesmente usar
`.ltr` ou `.rtl` em seus encapsuladores de componentes para usar uma ou outra
direção.

**Casos extremos e limitações conhecidas** a serem consideradas ao trabalhar com
uma implementação combinada de LTR e RTL:
{: .callout .warning }

1. Ao alternar entre `.ltr` e `.rtl`, certifique-se de adicionar os atributos
   `dir` e `lang` adequadamente.
   {: .callout .warning }
2. Carregar ambos os arquivos pode ser um verdadeiro gargalo de desempenho:
   considere fazer alguma [otimização](../customize/optimize.md) e talvez tentar
   [carregar um desses arquivos de forma assíncrona](https://www.filamentgroup.com/lab/load-css-simpler/).
   {: .callout .warning }
3. Aninhar estilos dessa forma impedirá que nosso _mixin_
   `form-validation-state()` funcione como pretendido, portanto, exigirá que
   você o ajuste um pouco por conta própria.
   Veja a _issue_ [#31223](https://github.com/twbs/bootstrap/issues/31223).
   {: .callout .warning }

Você quer automatizar esse processo e abordar vários casos extremos envolvendo
ambas as direções dentro de uma única folha de estilo?
Então, considere usar o
[PostCSS RTLCSS](https://github.com/elchininet/postcss-rtlcss) como um _plugin_
[PostCSS](https://github.com/postcss/postcss) para processar seus arquivos
fonte.
O PostCSS RTLCSS usa o [RTLCSS](https://rtlcss.com) nos bastidores para
gerenciar o processo de inversão de direção, mas ele separa as declarações
invertidas em regras com um prefixo diferente para LTR e RTL, algo que permite
que você tenha ambas as direções dentro do mesmo arquivo de folha de estilo.
Ao fazer isso, você pode alternar entre as orientações LTR e RTL simplesmente
alterando o `dir` da página (ou até mesmo modificando uma classe específica se
você configurar o _plugin_ adequadamente).

**Coisas importantes a levar em conta** ao usar o PostCSS RTLCSS para construir
uma implementação combinada de LTR e RTL:
{: .callout .warning }

1. É recomendado que você adicione o atributo `dir` ao elemento `html`.
   Dessa forma, a página inteira será afetada quando você alterar a direção.
   Além disso, certifique-se de adicionar o atributo `lang` adequadamente.
   {: .callout .warning }
2. Ter um único pacote com ambas as direções aumentará o tamanho da folha de
   estilo final (em média, em 20%-30%): considere fazer alguma
   [otimização](../customize/optimize.md).
   {: .callout .warning }
3. Leve em conta que o PostCSS RTLCSS não é compatível com as diretivas
   `/* rtl:remove */` porque ele não remove nenhuma regra CSS.
   Você deve substituir suas diretivas `/* rtl:remove */`,
   `/* rtl:begin:remove */` e `/* rtl:end:remove */` pelas diretivas
   `/* rtl:ignore */`, `/* rtl:begin:ignore */` e `/* rtl:end:ignore */`,
   respectivamente.
   Essas diretivas ignorarão a regra e não criarão uma contraparte RTL (o mesmo
   resultado das diretivas `remove` no RTLCSS).
   {: .callout .warning }

## O caso do breadcrumb

O [separador do breadcrumb](../components/breadcrumb.md#dividers) é o único caso
que requer sua própria variável novinha em folha — a saber,
`$breadcrumb-divider-flipped` — cujo padrão é `$breadcrumb-divider`.

## Recursos adicionais

- [RTLCSS](https://rtlcss.com/)
- [Estilo RTL 101](https://rtlstyling.com/posts/rtl-styling)
