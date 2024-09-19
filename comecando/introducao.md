---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/introduction.md
revision: 4bf483b3b5f486b7d5dffda772d434c74ebae9b4
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

title: Comece a usar o Bootstrap
description: Bootstrap é um poderoso conjunto de ferramentas de frontend repleto de recursos. Construa qualquer coisa — do protótipo à produção — em minutos.
---

# Comece a usar o Bootstrap

Bootstrap é um poderoso conjunto de ferramentas de _front-end_ repleto de
recursos.
Construa qualquer coisa — do protótipo à produção — em minutos.
{: .lead }

## Início rápido

Comece incluindo o CSS e o JavaScript prontos para produção do Bootstrap via CDN
sem a necessidade de nenhuma etapa de construção.
Veja na prática com esta
[demonstração do CodePen do Bootstrap](https://codepen.io/team/bootstrap/pen/qBamdLj).

1. **Crie um novo arquivo `index.html` na raiz do seu projeto.**
   Inclua também a _tag_ `<meta name="viewport">` para um
   [comportamento responsivo adequado](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag)
   em dispositivos móveis.

    ```html
    <!doctype html>
    <html lang="pt-br">
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <title>Demonstração do Bootstrap</title>
    </head>
    <body>
      <h1>Olá, mundo!</h1>
    </body>
    </html>
    ```

2. **Inclua o CSS e o JS do Bootstrap.** Coloque a _tag_ `<link>` no `<head>`
   para nosso CSS, e a _tag_ `<script>` para nosso pacote JavaScript (incluindo
   Popper para posicionar menus suspensos, _popovers_ e _tooltips_) antes do
   fechamento `</body>`.
   Saiba mais sobre nossos [_links_ de CDN](#links-de-cdn).
    ```html
    <!doctype html>
    <html lang="pt-br">
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <title>Demonstração do Bootstrap</title>
      <link href="{{ cdn.css }}" rel="stylesheet" integrity="{{ cdn.css_hash }}" crossorigin="anonymous">
    </head>
    <body>
      <h1>Olá, mundo!</h1>
      <script src="{{ cdn.js_bundle }}" integrity="{{ cdn.js_bundle_hash }}" crossorigin="anonymous"></script>
    </body>
    </html>
    ```
   Você também pode incluir o [Popper](https://popper.js.org/docs/v2/) e nosso
   JS separadamente.
   Se você não planeja usar menus suspensos, _popovers_ ou _tooltips_, economize
   alguns _kilobytes_ não incluindo o Popper.
    ```html
    <script src="{{ cdn.popper }}" integrity="{{ cdn.popper_hash }}" crossorigin="anonymous"></script>
    <script src="{{ cdn.js }}" integrity="{{ cdn.js_hash }}" crossorigin="anonymous"></script>
    ```

4. **Olá, mundo!** Abra a página no seu navegador de escolha para ver sua página
   com Bootstrap.
   Agora você pode começar a construir com Bootstrap criando seu próprio
   [_layout_](../layout/grid.md), adicionando dezenas de
   [componentes](../components/buttons.md) e utilizando
   [nossos exemplos oficiais](../examples/index.md).

## _Links_ de CDN

Como referência, aqui estão nossos principais _links_ de CDN.

| Descrição | URL                   |
|-----------|-----------------------|
| CSS       | `{{ cdn.css }}`       |
| JS        | `{{ cdn.js_bundle }}` |

Você também pode usar a CDN para obter qualquer uma das nossas
[compilações adicionais listadas na página Conteúdo](conteudo.md).

## Próximos passos

* Leia um pouco mais sobre algumas
  [configurações importantes do ambiente global](#globais-importantes) que o
  Bootstrap utiliza.
* Leia sobre o que está incluído no Bootstrap em nossa
  [seção Conteúdo](conteudo.md) e a lista de
  [componentes que exigem JavaScript](#componentes-js) abaixo.
* Precisa de um pouco mais de capacidade? Considere construir com o Bootstrap
  [incluindo os arquivos fonte usando o gerenciador de pacotes](../comecando/baixar.md#gerenciadores-de-pacotes).
* Procurando usar o Bootstrap como um módulo com `<script type="module">`?
  Consulte nossa seção [Usando o Bootstrap como um módulo](../getting-started/javascript.md#using-bootstrap-as-a-module).

## Componentes JS

Quer saber quais componentes exigem explicitamente nosso JavaScript e Popper?
Se você não tiver certeza sobre a estrutura geral da página, continue lendo para
um modelo de página de exemplo.

* Acordeões para estender nosso _plug-in_ Collapse;
* Alertas para dispensar;
* Botões para alternar estados e funcionalidade de caixa de seleção/rádio;
* Carrossel para todos os comportamentos de _slides_, controles e indicadores;
* Collapse para alternar a visibilidade do conteúdo;
* Menus suspensos para exibição e posicionamento (também requer
  [Popper](https://popper.js.org/docs/v2/));
* Modais para exibição, posicionamento e comportamento de rolagem;
* Barra de navegação para estender nossos _plug-ins_ Collapse e Offcanvas para
  implementar comportamentos responsivos;
* Barras de navegação com o _plug-in_ Tab para alternar painéis de conteúdo;
* _Offcanvases_ para exibição, posicionamento e comportamento de rolagem;
* _Scrollspy_ para comportamento de rolagem e atualizações de navegação;
* _Toasts_ para exibição e dispensa;
* _Tooltips_ e _popovers_ para exibição e posicionamento (também requer
  [Popper](https://popper.js.org/docs/v2/)).

## Globais importantes

O Bootstrap emprega um punhado de estilos e configurações globais importantes,
todos os quais são quase exclusivamente voltados para a normalização de estilos
entre navegadores.
Vamos nos aprofundar.

### _Doctype_ HTML5

O Bootstrap requer o uso do _doctype_ HTML5.
Sem ele, você verá alguns estilos estranhos e incompletos.

```html
<!doctype html>
<html lang="pt-br">
...
</html>
```

### Meta `viewport`

O Bootstrap é desenvolvido com foco em dispositivos móveis, uma estratégia na
qual otimizamos o código para dispositivos móveis primeiro e, em seguida,
aumentamos a escala dos componentes conforme necessário usando consultas de
mídia CSS.
Para garantir a renderização adequada e o controle de _zoom_ por toque para
todos os dispositivos, adicione a meta _tag_ responsiva `viewport` ao seu
`<head>`.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Você pode ver um exemplo disso em ação na seção [Início rápido](#inicio-rapido).

### `box-sizing`

Para um dimensionamento mais direto em CSS, trocamos o valor global `box-sizing`
de `content-box` para `border-box`.
Isso garante que o `padding` não afete a largura final calculada de um elemento,
mas pode causar problemas com alguns programas de terceiros, como o Google Maps
e o Google Custom Search Engine.

Na rara ocasião em que você precisar substituí-lo, use algo como o seguinte:

```css
.seletor-para-algum-componente {
    box-sizing: content-box;
}
```

Com o código acima, elementos aninhados — incluindo conteúdo gerado via
`::before` e `::after` — herdarão o `box-sizing` especificado para esse
`.seletor-para-algum-componente`.

Saiba mais sobre o
[modelo de caixa e dimensionamento no CSS Tricks](https://css-tricks.com/box-sizing/).

### Reboot

Para renderização aprimorada entre navegadores, usamos o
[Reboot](../content/reboot.md) para corrigir inconsistências em navegadores e
dispositivos, ao mesmo tempo em que fornecemos redefinições um pouco mais
opinativas para elementos HTML comuns.

## Comunidade

Acompanhe o desenvolvimento do Bootstrap e entre em contato com a comunidade com
esses recursos úteis.

* Leia e assine o [Blog Oficial do Bootstrap]({{ blog }});
* Faça perguntas e explore
  [nossas Discussões no GitHub](https://github.com/twbs/bootstrap/discussions);
* Discuta, faça perguntas e muito mais no
  [Discord da comunidade](https://discord.gg/bZUvakRU3M) ou no
  [subreddit do Bootstrap](https://www.reddit.com/r/bootstrap/);
* Converse com colegas Bootstrappers no IRC no servidor `irc.libera.chat`, no
  canal `#bootstrap`;
* A ajuda para implementação pode ser encontrada no Stack Overflow (marcada como
  [`bootstrap-5`](https://stackoverflow.com/questions/tagged/bootstrap-5));
* As pessoas desenvolvedoras devem usar a palavra-chave `bootstrap` em pacotes
  que modificam ou adicionam funcionalidades do Bootstrap ao distribuir por meio
  do [npm](https://www.npmjs.com/search?q=keywords:bootstrap) ou mecanismos de
  distribuição semelhantes para máximo alcance.

Você também pode seguir
[@getbootstrap no Twitter](https://twitter.com/{{  twitter }}) para as últimas
fofocas e vídeos musicais incríveis.
