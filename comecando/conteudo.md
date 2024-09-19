---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/contents.md
revision: cf9454caa00872899215603e5e036d9a824b1b11
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

title: Conteúdo
description: |
  Descubra o que está incluído no Bootstrap, incluindo nossos sabores de
  código-fonte e compilados.
---

# Conteúdo

Descubra o que está incluído no Bootstrap, incluindo nossos sabores de
código-fonte e compilados.
{: .lead }

## Bootstrap compilado

Depois de baixado, descompacte a pasta compactada e você verá algo assim:

```text
bootstrap/
├── css/
│   ├── bootstrap-grid.css
│   ├── bootstrap-grid.css.map
│   ├── bootstrap-grid.min.css
│   ├── bootstrap-grid.min.css.map
│   ├── bootstrap-grid.rtl.css
│   ├── bootstrap-grid.rtl.css.map
│   ├── bootstrap-grid.rtl.min.css
│   ├── bootstrap-grid.rtl.min.css.map
│   ├── bootstrap-reboot.css
│   ├── bootstrap-reboot.css.map
│   ├── bootstrap-reboot.min.css
│   ├── bootstrap-reboot.min.css.map
│   ├── bootstrap-reboot.rtl.css
│   ├── bootstrap-reboot.rtl.css.map
│   ├── bootstrap-reboot.rtl.min.css
│   ├── bootstrap-reboot.rtl.min.css.map
│   ├── bootstrap-utilities.css
│   ├── bootstrap-utilities.css.map
│   ├── bootstrap-utilities.min.css
│   ├── bootstrap-utilities.min.css.map
│   ├── bootstrap-utilities.rtl.css
│   ├── bootstrap-utilities.rtl.css.map
│   ├── bootstrap-utilities.rtl.min.css
│   ├── bootstrap-utilities.rtl.min.css.map
│   ├── bootstrap.css
│   ├── bootstrap.css.map
│   ├── bootstrap.min.css
│   ├── bootstrap.min.css.map
│   ├── bootstrap.rtl.css
│   ├── bootstrap.rtl.css.map
│   ├── bootstrap.rtl.min.css
│   └── bootstrap.rtl.min.css.map
└── js/
    ├── bootstrap.bundle.js
    ├── bootstrap.bundle.js.map
    ├── bootstrap.bundle.min.js
    ├── bootstrap.bundle.min.js.map
    ├── bootstrap.esm.js
    ├── bootstrap.esm.js.map
    ├── bootstrap.esm.min.js
    ├── bootstrap.esm.min.js.map
    ├── bootstrap.js
    ├── bootstrap.js.map
    ├── bootstrap.min.js
    └── bootstrap.min.js.map
```

Esta é a forma mais básica do Bootstrap: arquivos compilados para uso rápido em
praticamente qualquer projeto _web_.
Fornecemos CSS e JS compilados (`bootstrap.*`), bem como CSS e JS compilados e
minificados (`bootstrap.min.*`).
[Mapas de fontes](https://web.dev/articles/source-maps) (`bootstrap.*.map`)
estão disponíveis para uso com as ferramentas de pessoa desenvolvedora de
determinados navegadores.
Arquivos JS agrupados (`bootstrap.bundle.js` e `bootstrap.bundle.min.js`
minificado) incluem o [Popper](https://popper.js.org/docs/v2/).

### Arquivos CSS

O Bootstrap inclui um punhado de opções para incluir alguns ou todos os nossos
CSS compilados.

| Arquivos CSS                                                                                                                        | Layout                                | Conteúdo                            | Componentes | Utilities                                   |
|-------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------|-------------------------------------|-------------|---------------------------------------------|
| `bootstrap.css`<br> `bootstrap.min.css`<br> `bootstrap.rtl.css`<br> `bootstrap.rtl.min.css`                                         | Included                              | Included                            | Included    | Included                                    |
| `bootstrap-grid.css`<br> `bootstrap-grid.rtl.css`<br> `bootstrap-grid.min.css`<br> `bootstrap-grid.rtl.min.css`                     | [Only grid system](../layout/grid.md) | —                                   | —           | [Only flex utilities](../utilities/flex.md) |
| `bootstrap-utilities.css`<br> `bootstrap-utilities.rtl.css`<br> `bootstrap-utilities.min.css`<br> `bootstrap-utilities.rtl.min.css` | —                                     | —                                   | —           | Included                                    |
| `bootstrap-reboot.css`<br> `bootstrap-reboot.rtl.css`<br> `bootstrap-reboot.min.css`<br> `bootstrap-reboot.rtl.min.css`             | —                                     | [Only Reboot](../content/reboot.md) | —           | —                                           |

### Arquivos JS

Da mesma forma, temos opções para incluir uma parte ou todo o nosso JavaScript
compilado.

| Arquivos JS                                             | Popper   |
|---------------------------------------------------------|----------|
| `bootstrap.bundle.js`<br> `bootstrap.bundle.min.js`<br> | Included |
| `bootstrap.js`<br> `bootstrap.min.js`<br>               | –        |

## Código-fonte do Bootstrap

O _download_ do código-fonte do Bootstrap inclui os ativos CSS e JavaScript
compilados, juntamente com os arquivos fonte Sass, JavaScript e a documentação.
Mais especificamente, ele inclui o seguinte e mais:

```text
bootstrap/
├── dist/
│   ├── css/
│   └── js/
├── site/
│   └──content/
│      └── docs/
│          └── {{ docs_version }}/
│              └── examples/
├── js/
└── scss/
```

O `scss/` e o `js/` são o código-fonte para nosso CSS e JavaScript.
A pasta `dist/` inclui tudo listado na seção de download compilado acima.
A pasta `site/content/docs/` inclui o código-fonte para nossa documentação
hospedada, incluindo nossos exemplos dinâmicos de uso do Bootstrap.

Além disso, qualquer outro arquivo incluído fornece suporte para pacotes,
informações de licença e desenvolvimento.
