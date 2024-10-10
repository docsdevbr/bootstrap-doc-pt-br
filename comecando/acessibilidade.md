---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/accessibility.md
revision: cf9454caa00872899215603e5e036d9a824b1b11
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

layout: docs
title: Acessibilidade
description: |
  Uma breve visão geral dos recursos e limitações do Bootstrap para a criação de
  conteúdo acessível.
group: getting-started
toc: true
---

# Acessibilidade

O Bootstrap fornece um _framework_ fácil de usar de estilos prontos, ferramentas
de _layout_ e componentes interativos, permitindo que as pessoas desenvolvedoras
criem _sites_ e aplicações que sejam visualmente atraentes, funcionalmente ricas
e acessíveis imediatamente.

## Visão geral e limitações

A acessibilidade geral de qualquer projeto criado com o Bootstrap depende em
grande parte da marcação das pessoas autoras, estilo adicional e _script_ que
elas incluíram.
No entanto, desde que tenham sido implementados corretamente, deve ser
perfeitamente possível criar _sites_ e aplicações com o Bootstrap que atendam à
[<abbr title="Diretrizes de Acessibilidade de Conteúdo Web">WCAG</abbr> 2.2](https://www.w3.org/TR/WCAG/)
(A/AA/AAA), [Seção 508](https://www.section508.gov/) e padrões e requisitos de
acessibilidade semelhantes.

### Marcação estrutural

O estilo e o _layout_ do Bootstrap podem ser aplicados a uma ampla variedade de
estruturas de marcação.
Esta documentação tem como objetivo fornecer às pessoas desenvolvedoras exemplos
de melhores práticas para demonstrar o uso do Bootstrap em si e ilustrar a
marcação semântica apropriada, incluindo maneiras pelas quais potenciais
preocupações com acessibilidade podem ser abordadas.

### Componentes interativos

Os componentes interativos do Bootstrap — como caixas de diálogo modais, menus
suspensos e _tooltips_ personalizados — são projetados para funcionar para
pessoas usuárias de toque, mouse e teclado.
Por meio do uso de papéis e atributos
[<abbr title="Iniciativa de Acessibilidade Web">WAI</abbr>-<abbr title="Aplicações de Internet Ricas Acessíveis">ARIA</abbr>](https://www.w3.org/WAI/standards-guidelines/aria/)
relevantes, esses componentes também devem ser compreensíveis e operáveis usando
tecnologias assistivas (como leitores de tela).

Como os componentes do Bootstrap são projetados propositalmente para serem
bastante genéricos, as pessoas autoras podem precisar incluir mais papéis e
atributos <abbr title="Aplicações de Internet Ricas Acessíveis">ARIA</abbr>, bem
como comportamento JavaScript, para transmitir com mais precisão a natureza e a
funcionalidade precisas de seu componente.
Isso geralmente é observado na documentação.

### Contraste de cores

Algumas combinações de cores que atualmente compõem a paleta padrão do Bootstrap
— usadas em todo o _framework_ para coisas como variações de botões, variações
de alertas, indicadores de validação de formulários — podem levar a contrastes
de cores insuficientes (abaixo da
[proporção de contraste de cores de texto recomendada pelo WCAG 2.2 de 4,5:1](https://www.w3.org/TR/WCAG/#contrast-minimum)
e da
[proporção de contraste de cores não textuais do WCAG 2.2 de 3:1](https://www.w3.org/TR/WCAG/#non-text-contrast)),
particularmente quando usadas em um fundo claro.
As pessoas autoras são encorajadas a testar seus usos específicos de cores e,
quando necessário, modificar/estender manualmente essas cores padrão para
garantir proporções de contraste de cores adequadas.

### Conteúdo visualmente oculto

O conteúdo que deve ser visualmente oculto, mas permanecer acessível a
tecnologias assistivas, como leitores de tela, pode ser estilizado usando a
classe `.visually-hidden`.
Isso pode ser útil em situações em que informações ou dicas visuais adicionais
(como significado denotado pelo uso de cores) também precisam ser transmitidas a
pessoas usuárias não visuais.

```html
<p class="text-danger">
  <span class="visually-hidden">Perigo: </span>
  Esta ação não é reversível
</p>
```

Para controles interativos visualmente ocultos, como _links_ tradicionais de
"pular", use a classe `.visually-hidden-focusable`.
Isso garantirá que o controle se torne visível quando focado (para pessoas
usuárias de teclado com visão).
**Cuidado, comparada às classes equivalentes `.sr-only` e `.sr-only-focusable`
em versões anteriores, `.visually-hidden-focusable` do Bootstrap 5 é uma classe
que funciona sozinha e não deve ser usada em combinação com a classe
`.visually-hidden`.**

```html
<a class="visually-hidden-focusable" href="#content">Pular para o conteúdo principal</a>
```

### Movimento reduzido

O Bootstrap inclui suporte para o
[recurso de mídia `prefers-reduced-motion`](https://www.w3.org/TR/mediaqueries-5/#prefers-reduced-motion).
Em navegadores/ambientes que permitem que a perssoa usuária especifique sua
preferência por movimento reduzido, a maioria dos efeitos de transição CSS no
Bootstrap (por exemplo, quando um diálogo modal é aberto ou fechado, ou a
animação deslizante em carrosséis) serão desabilitados, e animações
significativas (como _spinners_) serão desaceleradas.

Em navegadores que suportam `prefers-reduced-motion`, e onde a pessoa usuária
_não_ sinalizou explicitamente que prefere movimento reduzido (ou seja, onde
`prefers-reduced-motion: no-preference`), o Bootstrap habilita a rolagem suave
usando a propriedade `scroll-behavior`.

## Recursos adicionais

- [Diretrizes de Acessibilidade de Conteúdo Web (WCAG) 2.2](https://www.w3.org/TR/WCAG/)
- [O Projeto A11Y](https://www.a11yproject.com/)
- [Documentação de acessibilidade da MDN](https://developer.mozilla.org/pt-BR/docs/Web/Accessibility)
- [Verificador de Acessibilidade Tenon.io](https://tenon.io/)
- [Analisador de Contraste de Cores (CCA)](https://www.tpgi.com/color-contrast-checker/)
- [Marcador "HTML Codesniffer" para identificar problemas de acessibilidade](https://github.com/squizlabs/HTML_CodeSniffer)
- [Perspectivas de Acessibilidade da Microsoft](https://accessibilityinsights.io/)
- [Ferramentas de teste Deque Axe](https://www.deque.com/axe/)
- [Introdução à Acessibilidade Web](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
