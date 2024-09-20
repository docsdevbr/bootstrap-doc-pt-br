---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/javascript.md
revision: 0fe3dd93f26187cf7f6fd8df38fc3e9348ca2fd0
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

title: JavaScript
description: |
  Dê vida ao Bootstrap com nossos _plug-ins_ JavaScript opcionais. Aprenda sobre
  cada _plug-in_, nossas opções de API programática e de dados e muito mais.
---

# JavaScript

Dê vida ao Bootstrap com nossos _plug-ins_ JavaScript opcionais. Aprenda sobre
cada _plug-in_, nossas opções de API programática e de dados e muito mais.
{: .lead }

## Individual ou compilado

Plugins podem ser incluídos individualmente (usando os arquivos individuais
`js/dist/*.js` do Bootstrap), ou todos de uma vez usando `bootstrap.js` ou o
`bootstrap.min.js` minificado (não inclua ambos).

Se você usar um empacotador (Webpack, Parcel, Vite...), você pode usar arquivos
`/js/dist/*.js` que são prontos para UMD.

## Uso com _frameworks_ JavaScript

Embora o CSS Bootstrap possa ser usado com qualquer _framework_, **o JavaScript
Bootstrap não é totalmente compatível com _frameworks_ JavaScript como React,
Vue e Angular**, que assumem conhecimento total do DOM.
Tanto o Bootstrap quanto o _framework_ podem tentar modificar o mesmo elemento
DOM, resultando em falhas como menus suspensos que ficam presos na posição
"aberto".

Uma alternativa melhor para aqueles que usam esse tipo de _framework_ é usar um
pacote específico do _framework_ **em vez do** JavaScript Bootstrap.
Aqui estão algumas das opções mais populares:

* React: [React Bootstrap](https://react-bootstrap.github.io/)
    * **Faça um teste!** Baixe o código-fonte e a demonstração funcional de uso do
      Bootstrap com React, Next.js e React Bootstrap do
      [repositório twbs/examples](https://github.com/twbs/examples/tree/main/react-nextjs).
      Você também pode
      [abrir o exemplo no StackBlitz](https://stackblitz.com/github/twbs/examples/tree/main/react-nextjs?file=src%2Fpages%2Findex.tsx).
      {: .callout .info }
* Vue: [BootstrapVue](https://bootstrap-vue.org/) (Bootstrap 4)
* Vue 3:
  [BootstrapVueNext](https://bootstrap-vue-next.github.io/bootstrap-vue-next/)
  (Bootstrap 5, atualmente em _alpha_)
* Angular: [ng-bootstrap](https://ng-bootstrap.github.io/)

## Usando Bootstrap como um módulo

**Faça um teste!** Baixe o código-fonte e a demonstração funcional de uso do
Bootstrap como um módulo ES do
[repositório twbs/examples](https://github.com/twbs/examples/tree/main/sass-js-esm).
Você também pode
[abrir o exemplo no StackBlitz](https://stackblitz.com/github/twbs/examples/tree/main/sass-js-esm?file=index.html).
{: .callout .info }

Nós fornecemos uma versão do Bootstrap construída como ESM (`bootstrap.esm.js`
e `bootstrap.esm.min.js`) que permite que você use o Bootstrap como um módulo no
navegador, se os
[navegadores alvos o suportarem](https://caniuse.com/es6-module).

```html
<script type="module">
  import { Toast } from 'bootstrap.esm.min.js'

  Array.from(document.querySelectorAll('.toast'))
    .forEach(toastNode => new Toast(toastNode))
</script>
```

Comparado aos empacotadores JS, usar ESM no navegador requer que você use o
caminho completo e o nome do arquivo em vez do nome do módulo.
[Leia mais sobre módulos JS no navegador.](https://v8.dev/features/modules#specifiers)
É por isso que usamos `'bootstrap.esm.min.js'` em vez de `'bootstrap'` acima.
No entanto, isso é ainda mais complicado por nossa dependência Popper, que
importa Popper para nosso JavaScript assim:

```javascript
import * as Popper from "@popperjs/core"
```

Se você tentar fazer isso do jeito que está, verá um erro no console como o
seguinte:

```text
Uncaught TypeError: Failed to resolve module specifier "@popperjs/core". Relative references must start with either "/", "./", or "../".
```

Para corrigir isso, você pode usar um `importmap` para resolver os nomes de
módulos arbitrários para caminhos completos.
Se seus navegadores alvos não suportam `importmap`, você precisará usar o
projeto [es-module-shims](https://github.com/guybedford/es-module-shims).
Veja como funciona para Bootstrap e Popper:

```html
<!doctype html>
<html lang="pt-br">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="{{ cdn.css }}" rel="stylesheet" integrity="{{ cdn.css_hash }}"
        crossorigin="anonymous">
  <title>Olá, modularidade!</title>
</head>
<body>
<h1>Olá, modularidade!</h1>
<button id="popoverButton" type="button" class="btn btn-primary btn-lg"
        data-bs-toggle="popover" title="ESM no navegador"
        data-bs-content="Bang!">
  Popover personalizado
</button>

<script async
        src="https://cdn.jsdelivr.net/npm/es-module-shims@1/dist/es-module-shims.min.js"
        crossorigin="anonymous"></script>
<script type="importmap">
  {
    "imports": {
      "@popperjs/core": "{{ cdn.popper_esm }}",
      "bootstrap": "https://cdn.jsdelivr.net/npm/bootstrap@{{ current_version }}/dist/js/bootstrap.esm.min.js"
    }
  }
</script>
<script type="module">
  import * as bootstrap from 'bootstrap'

  new bootstrap.Popover(document.getElementById('popoverButton'))
</script>
</body>
</html>
```

## Dependências

Alguns _plug-ins_ e componentes CSS dependem de outros _plug-ins_.
Se você incluir _plug-ins_ individualmente, certifique-se de verificar essas
dependências na documentação.

Nossos menus suspensos, _popovers_ e _tooltips_ também dependem do
[Popper](https://popper.js.org/docs/v2/).

## Atributos de dados

Quase todos os _plug-ins_ Bootstrap podem ser habilitados e configurados apenas
com HTML com atributos de dados (nossa maneira preferida de usar a
funcionalidade JavaScript).
Certifique-se de **usar apenas um conjunto de atributos de dados em um único
elemento** (por exemplo, você não pode acionar uma _tooltip_ e um modal do mesmo
botão).

{% include-markdown '_includes/partials/js-data-attributes.md' %}

## Seletores

Usamos os métodos nativos `querySelector` e `querySelectorAll` para consultar
elementos DOM por motivos de desempenho, então você deve usar
[seletores válidos](https://www.w3.org/TR/CSS21/syndata.html#value-def-identifier).
Se você usar seletores especiais como `collapse:Exemplo`, certifique-se de
escapá-los.

## Eventos

O Bootstrap fornece eventos personalizados para a maioria das ações exclusivas
dos _plug-ins_.
Geralmente, eles vêm em uma forma infinitiva e particípio passado - onde o
infinitivo (ex. `show`) é acionado no início de um evento, e sua forma
particípio passado (ex. `shown`) é acionada na conclusão de uma ação.

Todos os eventos infinitivos fornecem a funcionalidade
[`preventDefault()`](https://developer.mozilla.org/pt-BR/docs/Web/API/Event/preventDefault).
Isso fornece a capacidade de interromper a execução de uma ação antes que ela
comece.
Retornar `false` de um manipulador de eventos também chamará `preventDefault()`
automaticamente.

```javascript
const myModal = document.querySelector('#myModal')

myModal.addEventListener('show.bs.modal', event => {
    return event.preventDefault() // impede que o modal seja exibido
})
```

## API programática

Todos os construtores aceitam um objeto opcional de opções ou nada (o que inicia
um _plug-in_ com seu comportamento padrão):

```javascript
const myModalEl = document.querySelector('#myModal')
const modal = new bootstrap.Modal(myModalEl) // inicializado com padrões

const configObject = { keyboard: false }
const modal1 = new bootstrap.Modal(myModalEl, configObject) // inicializado sem teclado
```

Se você quiser obter uma instância de _plug-in_ específica, cada _plug-in_ expõe
um método `getInstance`.
Por exemplo, para recuperar uma instância diretamente de um elemento:

```javascript
bootstrap.Popover.getInstance(myPopoverEl)
```

Este método retornará `null` se uma instância não for inicializada através do
elemento solicitado.

Alternativamente, `getOrCreateInstance` pode ser usado para obter a instância
associada a um elemento DOM, ou criar uma nova caso ela não tenha sido
inicializada.

```javascript
bootstrap.Popover.getOrCreateInstance(myPopoverEl, configObject)
```

Caso uma instância não tenha sido inicializada, ela pode aceitar e usar um
objeto de configuração opcional como segundo argumento.

### Seletores CSS em construtores

Além dos métodos `getInstance` e `getOrCreateInstance`, todos os construtores de
_plug-in_ podem aceitar um elemento DOM ou um [seletor CSS](#seletores) válido
como o primeiro argumento.
Elementos de _plug-in_ são encontrados com o método `querySelector`, já que
nossos _plug-ins_ suportam apenas um único elemento.

```javascript
const modal = new bootstrap.Modal('#myModal')
const dropdown = new bootstrap.Dropdown('[data-bs-toggle="dropdown"]')
const offcanvas = bootstrap.Offcanvas.getInstance('#myOffcanvas')
const alert = bootstrap.Alert.getOrCreateInstance('#myAlert')
```

### Funções e transições assíncronas

Todos os métodos de API programática são **assíncronos** e retornam ao chamador
assim que a transição é iniciada, mas **antes de terminar**.
Para executar uma ação assim que a transição for concluída, você pode ouvir o
evento correspondente.

```javascript
const myCollapseEl = document.querySelector('#myCollapse')

myCollapseEl.addEventListener('shown.bs.collapse', event => {
  // Ação a ser executada quando a área recolhível for expandida
})
```

Além disso, uma chamada de método em um **componente em transição será
ignorada**.

```javascript
const myCarouselEl = document.querySelector('#myCarousel')
const carousel = bootstrap.Carousel.getInstance(myCarouselEl) // Recupera uma instância de Carousel

myCarouselEl.addEventListener('slid.bs.carousel', event => {
  carousel.to('2') // Deslizará para o slide 2 assim que a transição para o slide 1 for concluída
})

carousel.to('1') // Começará a deslizar para o slide 1 e retornará para o chamador
carousel.to('2') // !! Será ignorado, pois a transição para o slide 1 não foi concluída !!
```

#### Método `dispose`

Embora possa parecer correto usar o método `dispose` imediatamente após
`hide()`, isso levará a resultados incorretos.
Aqui está um exemplo de uso problemático:

```javascript
const myModal = document.querySelector('#myModal')
myModal.hide() // é assíncrono

myModal.addEventListener('shown.bs.hidden', event => {
  myModal.dispose()
})
```

### Configurações padrão

Você pode alterar as configurações padrão de um _plug-in_ modificando o objeto
`Constructor.Default` do _plug-in_:

```javascript
// altera o padrão para a opção `keyboard` do plug-in modal para false
bootstrap.Modal.Default.keyboard = false
```

## Métodos e propriedades

Cada _plug-in_ Bootstrap expõe os seguintes métodos e propriedades estáticas.

| Método                | Descrição                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `dispose`             | Destrói o modal de um elemento. (Remove os dados armazenados no elemento DOM).                                                            |
| `getInstance`         | Método _estático_ que permite obter a instância modal associada a um elemento DOM.                                                        |
| `getOrCreateInstance` | Método _estático_ que permite obter a instância modal associada a um elemento DOM ou criar uma nova caso ela não tenha sido inicializada. |

| Propriedade estática | Descrição                                                                                                                                                            |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`               | Retorna o nome do _plug-in_. (Exemplo: `bootstrap.Tooltip.NAME`)                                                                                                     |
| `VERSION`            | A versão de cada um dos _plug-ins_ do Bootstrap pode ser acessada através da propriedade `VERSION` do construtor do _plug-in_ (Exemplo: `bootstrap.Tooltip.VERSION`) |

## Sanitizador

Tooltips e Popovers usam nosso sanitizador integrado para sanitizar opções que
aceitam HTML.

O valor padrão de `allowList` é o seguinte:

```javascript
// {{ repo }}/blob/v{{ current_version }}/js/src/util/sanitizer.js

const ARIA_ATTRIBUTE_PATTERN = /^aria-[\w-]*$/i

export const DefaultAllowlist = {
  // Atributos globais permitidos em qualquer elemento fornecido abaixo.
  '*': ['class', 'dir', 'id', 'lang', 'role', ARIA_ATTRIBUTE_PATTERN],
  a: ['target', 'href', 'title', 'rel'],
  area: [],
  b: [],
  br: [],
  col: [],
  code: [],
  dd: [],
  div: [],
  dl: [],
  dt: [],
  em: [],
  hr: [],
  h1: [],
  h2: [],
  h3: [],
  h4: [],
  h5: [],
  h6: [],
  i: [],
  img: ['src', 'srcset', 'alt', 'title', 'width', 'height'],
  li: [],
  ol: [],
  p: [],
  pre: [],
  s: [],
  small: [],
  span: [],
  sub: [],
  sup: [],
  strong: [],
  u: [],
  ul: []
}
```

Se você quiser adicionar novos valores a esta `allowList` padrão, você pode
fazer o seguinte:

```javascript
const myDefaultAllowList = bootstrap.Tooltip.Default.allowList

// Para permitir elementos de tabela
myDefaultAllowList.table = []

// Para permitir elementos td e atributos data-bs-option em elementos td
myDefaultAllowList.td = ['data-bs-option']

// Você pode enviar sua expressão regular personalizada para validar seus
// atributos.
// Tenha cuidado com suas expressões regulares sendo muito frouxas.
const myCustomRegex = /^data-my-app-[\w-]+/
myDefaultAllowList['*'].push(myCustomRegex)
```

Se você quiser ignorar nosso sanitizador porque prefere usar uma biblioteca
dedicada, por exemplo, [DOMPurify](https://www.npmjs.com/package/dompurify),
você deve fazer o seguinte:

```javascript
const yourTooltipEl = document.querySelector('#yourTooltip')
const tooltip = new bootstrap.Tooltip(yourTooltipEl, {
  sanitizeFn(content) {
    return DOMPurify.sanitize(content)
  }
})
```

## Usando jQuery opcionalmente

**Você não precisa do jQuery no Bootstrap 5**, mas ainda é possível usar nossos
componentes com o jQuery.
Se o Bootstrap detectar `jQuery` no objeto `window`, ele adicionará todos os
nossos componentes no sistema de _plug-ins_ do jQuery.
Isso permite que você faça o seguinte:

```javascript
// para habilitar tooltips com a configuração padrão
$('[data-bs-toggle="tooltip"]').tooltip()

// para inicializar tooltips com a configuração fornecida
$('[data-bs-toggle="tooltip"]').tooltip({
  boundary: 'clippingParents',
  customClass: 'myClass'
})

// para acionar o método `show`
$('#myTooltip').tooltip('show')
```

O mesmo vale para nossos outros componentes.

### Sem conflitos

Às vezes é necessário usar _plug-ins_ Bootstrap com outras estruturas de UI.
Nessas circunstâncias, colisões de _namespace_ podem ocorrer ocasionalmente.
Se isso acontecer, você pode chamar `.noConflict` no _plug-in_ cujo valor deseja
reverter.

```javascript
const bootstrapButton = $.fn.button.noConflict() // retorna $.fn.button ao valor atribuído anteriormente
$.fn.bootstrapBtn = bootstrapButton // dá a $().bootstrapBtn a funcionalidade Bootstrap
```

O Bootstrap não suporta oficialmente bibliotecas JavaScript de terceiros como
Prototype ou jQuery UI.
Apesar do `.noConflict` e dos eventos com _namespaces_, pode haver problemas de
compatibilidade que você precisa corrigir por conta própria.

### Eventos jQuery

O Bootstrap detectará o jQuery se `jQuery` estiver presente no objeto `window` e
não houver atributo `data-bs-no-jquery` definido em `<body>`.
Se o jQuery for encontrado, o Bootstrap emitirá eventos graças ao sistema de
eventos do jQuery.
Então, se você quiser ouvir os eventos do Bootstrap, terá que usar os métodos
jQuery (`.on`, `.one`) em vez de `addEventListener`.

```javascript
$('#myTab a').on('shown.bs.tab', () => {
  // faça alguma coisa...
})
```

## JavaScript desabilitado

Os _plug-ins_ do Bootstrap não têm uma última alternativa especial quando o
JavaScript está desabilitado.
Se você se importa com a experiência da pessoa usuária neste caso, use
[`<noscript>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/noscript)
para explicar a situação (e como reabilitar o JavaScript) para suas pessoas
usuárias e/ou adicione suas últimas alternativas personalizadas.
