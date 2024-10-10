---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/rfs.md
revision: cf9454caa00872899215603e5e036d9a824b1b11
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

layout: docs
title: RFS
description: |
  O mecanismo de redimensionamento do Bootstrap dimensiona responsivamente
  propriedades CSS comuns para melhor utilizar o espaço disponível em janelas de
  visualização e dispositivos.
group: getting-started
toc: true
---

# RFS

O mecanismo de redimensionamento do Bootstrap dimensiona responsivamente
propriedades CSS comuns para melhor utilizar o espaço disponível em janelas de
visualização e dispositivos.
{: .lead }

## O que é RFS?

O projeto paralelo do Bootstrap,
[RFS](https://github.com/twbs/rfs/tree/{{ rfs_version }}), é um mecanismo de
redimensionamento de unidade que foi desenvolvido inicialmente para
redimensionar tamanhos de fonte (daí sua abreviação para Tamanhos de Fonte
Responsivos).
Hoje em dia, o RFS é capaz de redimensionar a maioria das propriedades CSS com
valores de unidade como `margin`, `padding`, `border-radius` ou até mesmo
`box-shadow`.

O mecanismo calcula automaticamente os valores apropriados com base nas
dimensões da janela de visualização do navegador.
Ele será compilado em funções `calc()` com uma mistura de unidades `rem` e de
janelas de visualização para habilitar o comportamento de dimensionamento
responsivo.

## Usando RFS

Os _mixins_ são incluídos no Bootstrap e ficam disponíveis quando você inclui o
`scss` do Bootstrap.
O RFS também pode ser
[instalado de forma independente](https://github.com/twbs/rfs/tree/{{ rfs_version }}#installation),
se necessário.

### Usando os _mixins_

O _mixin_ `rfs()` tem atalhos para `font-size`, `margin`, `margin-top`,
`margin-right`, `margin-bottom`, `margin-left`, `padding`, `padding-top`,
`padding-right`, `padding-bottom` e `padding-left`.
Veja o exemplo abaixo para o arquivos fonte Sass e o CSS compilado.

```scss
.title {
  @include font-size(4rem);
}
```

```css
.title {
  font-size: calc(1.525rem + 3.3vw);
}

@media (min-width: 1200px) {
  .title {
    font-size: 4rem;
  }
}
```

Qualquer outra propriedade pode ser passada para o _mixin_ `rfs()` assim:

```scss
.selector {
  @include rfs(4rem, border-radius);
}
```

`!important` também pode ser adicionado a qualquer valor que você desejar:

```scss
.selector {
  @include padding(2.5rem !important);
}
```

### Usando as funções

Quando você não quiser usar `@include`, também há duas funções:

- `rfs-value()` converte um valor em um valor `rem` se um valor `px` for
  passado, em outros casos ele retorna o mesmo resultado.
- `rfs-fluid-value()` retorna a versão fluida de um valor se a propriedade
  precisar de redimensionamento.

Neste exemplo, usamos um dos
[_mixins_ de _breakpoints_ responsivos](../layout/breakpoints.md)
integrados do Bootstrap para aplicar apenas o estilo abaixo do _breakpoint_
`lg`.

```scss
.selector {
  @include media-breakpoint-down(lg) {
    padding: rfs-fluid-value(2rem);
    font-size: rfs-fluid-value(1.125rem);
  }
}
```

```css
@media (max-width: 991.98px) {
  .selector {
    padding: calc(1.325rem + 0.9vw);
    font-size: 1.125rem; /* 1.125rem é pequeno o suficiente, então o RFS não irá redimensionar isso */
  }
}
```

## Documentação estendida

RFS é um projeto separado sob a organização Bootstrap.
Mais sobre o RFS e sua configuração podem ser encontrados em seu
[repositório GitHub](https://github.com/twbs/rfs/tree/{{ rfs_version }}).
