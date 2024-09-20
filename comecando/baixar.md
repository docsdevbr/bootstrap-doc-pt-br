---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/introduction.md
revision: 4bf483b3b5f486b7d5dffda772d434c74ebae9b4
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

title: Baixar
description: |
  Baixe o Bootstrap para obter o CSS e o JavaScript compilados, o código-fonte
  ou inclua-o com seus gerenciadores de pacotes favoritos, como npm, RubyGems e
  mais.
---

# Baixar

Baixe o Bootstrap para obter o CSS e o JavaScript compilados, o código-fonte ou
inclua-o com seus gerenciadores de pacotes favoritos, como npm, RubyGems e mais.
{: .lead }

## CSS e JS compilados

Baixe o código compilado pronto para uso do **Bootstrap v{{ current_version }}**
para inserir facilmente em seu projeto, que inclui:

* Pacotes CSS compilados e minimizados (veja a
  [comparação de arquivos CSS](conteudo.md#arquivos-css));
* _Plug-ins_ JavaScript compilados e minimizados (veja a
  [comparação de arquivos JS](conteudo#arquivos-js)).

Isso não inclui documentação, arquivos fonte ou quaisquer dependências
JavaScript opcionais como o Popper.

<a href="{{ download.dist }}" class="btn btn-primary">Baixar</a>

## Arquivos fonte

Compile o Bootstrap com sua esteira de ativos baixando nossos arquivos fonte
Sass, JavaScript e da documentação.
Esta opção requer algumas ferramentas adicionais:

* [Compilador Sass](../getting-started/contribute.md#sass) para compilar
  arquivos fonte Sass em arquivos CSS;
* [Autoprefixer](https://github.com/postcss/autoprefixer) para prefixação de
  fornecedores CSS.

Se você precisar de nosso conjunto completo de
[ferramentas de construção](../getting-started/contribute.md#tooling-setup),
elas foram incluídas para desenvolver o Bootstrap e sua documentação, mas
provavelmente não são adequadas para seus propósitos.

<a href="{{ download.source }}" class="btn btn-primary">Baixar código-fonte</a>

## Exemplos

Se você quiser baixar e examinar nossos [exemplos](../examples/index.md), você
pode pegar os exemplos já construídos:

<a href="{{ download.dist_examples }}" class="btn btn-bd-primary">
Baixar exemplos
</a>

## CDN via jsDelivr

Pule o _download_ dos arquivos usando [jsDelivr](https://www.jsdelivr.com/) para
entregar a versão em cache do CSS e JS compilados do Bootstrap para seu projeto.

```html
<link href="{{ cdn.css }}" rel="stylesheet" integrity="{{ cdn.css_hash }}"
      crossorigin="anonymous">
<script src="{{ cdn.js_bundle }}" integrity="{{ cdn.js_bundle_hash }}"
        crossorigin="anonymous"></script>
```

Se você estiver usando nosso JavaScript compilado e preferir incluir o Popper
separadamente, adicione o Popper antes do nosso JS, de preferência por meio de
uma CDN.

```html
<script src="{{ cdn.popper }}" integrity="{{ cdn.popper_hash }}"
        crossorigin="anonymous"></script>
<script src="{{ cdn.js }}" integrity="{{ cdn.js_hash }}"
        crossorigin="anonymous"></script>
```

### CDNs alternativas

Recomendamos o [jsDelivr](https://www.jsdelivr.com/) e o usamos em nossa
documentação.
No entanto, em alguns casos, como em alguns países ou ambientes específicos,
você pode precisar usar outros provedores de CDN, como
[cdnjs](https://cdnjs.com/) ou [unpkg](https://unpkg.com/).

Você encontrará os mesmos arquivos nesses provedores de CDN, embora com URLs
diferentes.
Com o cdnjs, você pode
[usar este link direto do pacote Bootstrap](https://cdnjs.com/libraries/bootstrap)
para copiar e colar códigos HTML prontos para uso para cada arquivo de
distribuição de qualquer versão do Bootstrap.

**Se os _hashes_ SRI forem diferentes para um determinado arquivo, você não deve
usar os arquivos dessa CDN, porque isso significa que o arquivo foi modificado
por outra pessoa.**
{: .callout .warning }

Observe que você deve comparar _hashes_ de mesmo comprimento, por exemplo,
`sha384` com `sha384`, caso contrário, espera-se que sejam diferentes.
Como tal, você pode usar uma ferramenta online como o
[Gerador de Hash SRI](https://www.srihash.org/) para garantir que os _hashes_
sejam os mesmos para um determinado arquivo.
Alternativamente, supondo que você tenha o OpenSSL instalado, você pode obter o
mesmo a partir da CLI, por exemplo:

```shell
openssl dgst -sha384 -binary bootstrap.min.js | openssl base64 -A
```

## Gerenciadores de pacotes

Inclua os **arquivos fonte** do Bootstrap em praticamente qualquer projeto com
alguns dos gerenciadores de pacotes mais populares.
Não importa o gerenciador de pacotes, o Bootstrap **exigirá um
[compilador Sass](/getting-started/contribute.md#sass) e um
[Autoprefixer](https://github.com/postcss/autoprefixer)** para uma configuração
que corresponda às nossas versões oficiais compiladas.

### npm

Instale o Bootstrap em suas aplicações Node.js com o
[pacote npm](https://www.npmjs.com/package/bootstrap):

```shell
npm install bootstrap@{{ current_version }}
```

`const bootstrap = require('bootstrap')` ou `import bootstrap from 'bootstrap'`
carregará todos os _plug-ins_ do Bootstrap em um objeto `bootstrap`.
O próprio módulo `bootstrap` exporta todos os nossos _plug-ins_.
Você pode carregar manualmente os _plug-ins_ do Bootstrap individualmente
carregando os arquivos `/js/dist/*.js` no diretório raiz do pacote.

O `package.json` do Bootstrap contém alguns metadados adicionais nas seguintes
chaves:

* `sass` - caminho para o arquivo fonte [Sass](https://sass-lang.com/) principal
  do Bootstrap;
* `style` - caminho para o CSS não minificado do Bootstrap que foi compilado
  usando as configurações padrão (sem personalização).

{% include-markdown '_includes/partials/callouts/info-npm-starter.md' %}

### yarn

Instale o Bootstrap em suas aplicações Node.js com o
[pacote yarn](https://yarnpkg.com/en/package/bootstrap):

```shell
yarn add bootstrap@{{ current_version }}
```

### RubyGems

Instale o Bootstrap em suas aplicações Ruby usando
[Bundler](https://bundler.io/) (**recomendado**) e
[RubyGems](https://rubygems.org/) adicionando a seguinte linha ao seu
[`Gemfile`](https://bundler.io/guides/gemfile.html):

```ruby
gem 'bootstrap', '~> {{ current_ruby_version }}'
```

Alternativamente, se você não estiver usando o Bundler, você pode instalar a
_gem_ executando este comando:

```shell
gem install bootstrap -v {{ current_ruby_version }}
```

[Veja o README da _gem_](https://github.com/twbs/bootstrap-rubygem/blob/main/README.md)
para mais detalhes.

### Composer

Você também pode instalar e gerenciar o Sass e o JavaScript do Bootstrap usando
o [Composer](https://getcomposer.org/):

```shell
composer require twbs/bootstrap:{{ current_version }}
```

### NuGet

Se você desenvolve no Framework .NET, também pode instalar e gerenciar o
[CSS](https://www.nuget.org/packages/bootstrap/) ou
[Sass](https://www.nuget.org/packages/bootstrap.sass/) e JavaScript do Bootstrap
usando o [NuGet](https://www.nuget.org/).
Projetos mais novos devem usar
[libman](https://learn.microsoft.com/en-us/aspnet/core/client-side/libman/) ou
outro método, pois o NuGet é projetado para código compilado, não para ativos de
_front-end_.

```powershell
Install-Package bootstrap
```

```powershell
Install-Package bootstrap.sass
```
