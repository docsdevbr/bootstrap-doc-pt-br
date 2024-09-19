---
source_url: https://github.com/twbs/bootstrap/blob/v5.3.3/site/content/docs/5.3/getting-started/browsers-devices.md
revision: 9042efd0f86dd571386f62bacc8738ac975517fc
status: ready
license: https://github.com/twbs/bootstrap/blob/main/LICENSE

title: Navegadores e dispositivos
description: |
  Aprenda sobre os navegadores e dispositivos, dos modernos aos antigos, que são
  suportados pelo Bootstrap, incluindo peculiaridades e falhas conhecidos para
  cada um.
---

# Navegadores e dispositivos

Aprenda sobre os navegadores e dispositivos, dos modernos aos antigos, que são
suportados pelo Bootstrap, incluindo peculiaridades e falhas conhecidos para
cada um.
{: .lead }

## Navegadores suportados

O Bootstrap suporta as **versões mais recentes e estáveis** de todos os
principais navegadores e plataformas.

Navegadores alternativos que usam a versão mais recente do WebKit, Blink ou
Gecko, seja diretamente ou por meio da API de visualização _web_ da plataforma,
não são explicitamente suportados.
No entanto, o Bootstrap deve (na maioria dos casos) exibir e funcionar
corretamente nesses navegadores também.
Informações de suporte mais específicas são fornecidas abaixo.

Você pode encontrar nossa gama de navegadores suportados e suas versões
[em nosso arquivo `.browserslistrc`]({{ repo }}/blob/v{{ current_version }}/.browserslistrc):

```text
# https://github.com/browserslist/browserslist#readme

>= 0.5%
last 2 major versions
not dead
Chrome >= 60
Firefox >= 60
Firefox ESR
iOS >= 12
Safari >= 12
not Explorer <= 11
```

Usamos o [Autoprefixer](https://github.com/postcss/autoprefixer) para tratar do
suporte pretendido ao navegador por meio de prefixos CSS, que usa o
[Browserslist](https://github.com/browserslist/browserslist) para gerenciar
essas versões do navegador.
Consulte a documentação deles para saber como integrar essas ferramentas aos
seus projetos.

### Dispositivos móveis

De modo geral, o Bootstrap suporta as versões mais recentes dos navegadores
padrão de cada plataforma principal.
Observe que navegadores _proxy_ (como Opera Mini, modo Turbo do Opera Mobile, UC
Browser Mini, Amazon Silk) não são suportados.

|             | Chrome    | Firefox   | Safari    | Android Browser e WebView |
|-------------|-----------|-----------|-----------|---------------------------|
| **Android** | Suportado | Suportado | &mdash;   | v6.0+                     |
| **iOS**     | Suportado | Suportado | Suportado | &mdash;                   |

### Navegadores _desktop_

Da mesma forma, as versões mais recentes da maioria dos navegadores _desktop_
são suportadas.

|             | Chrome    | Firefox   | Microsoft Edge | Opera     | Safari    |
|-------------|-----------|-----------|----------------|-----------|-----------|
| **Mac**     | Suportado | Suportado | Suportado      | Suportado | Suportado |
| **Windows** | Suportado | Suportado | Suportado      | Suportado | &mdash;   |

Para o Firefox, além da versão estável normal mais recente, também oferecemos
suporte à versão
[Extended Support Release (ESR)](https://www.mozilla.org/pt-BR/firefox/enterprise/)
mais recente do Firefox.

Não oficialmente, o Bootstrap deve ter uma boa aparência e comportamento no
Chromium e no Chrome para Linux, e no Firefox para Linux, embora não sejam
oficialmente suportados.

## Internet Explorer

O Internet Explorer não é suportado.
**Se você precisar de suporte para o Internet Explorer, use o Bootstrap v4.**

## Modais e menus suspensos em dispositivos móveis

### `overflow` e rolagem

O suporte para `overflow: hidden;` no elemento `<body>` é bastante limitado no
iOS e Android.
Para esse fim, quando você rola além da parte superior ou inferior de um modal
em qualquer um dos navegadores desses dispositivos, o conteúdo de `<body>`
começará a rolar.
Veja a [falha #175502 do Chrome](https://issues.chromium.org/issues/40301599)
(corrigida no Chrome v40) e a
[falha #153852 do WebKit](https://bugs.webkit.org/show_bug.cgi?id=153852).

### Campos de texto e rolagem do iOS

A partir do iOS 9.2, enquanto um modal estiver aberto, se o toque inicial de um
gesto de rolagem estiver dentro do limite de um `<input>` textual ou de um
`<textarea>`, o conteúdo de `<body>` abaixo do modal será rolado em vez do
próprio modal.
Veja a [falha #153856 do WebKit](https://bugs.webkit.org/show_bug.cgi?id=153856).

### Menus suspensos da barra de navegação

O elemento `.dropdown-backdrop` não é usado no iOS na navegação devido à
complexidade da indexação z.
Portanto, para fechar os menus suspensos nas barras de navegação, você deve
clicar diretamente no elemento `dropdown` (ou
[qualquer outro elemento que acione um evento de clique no iOS](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event#Safari_Mobile)).

## Controle de _zoom_ do navegador

O _zoom_ da página inevitavelmente apresenta artefatos de renderização em alguns
componentes, tanto no Bootstrap quanto no resto da _web_.
Dependendo do problema, podemos consertá-lo (pesquise primeiro e depois abra uma
_issue_, se necessário).
No entanto, tendemos a ignorá-las, pois geralmente não têm solução direta além
de gambiarras.

## Validadores

Para fornecer a melhor experiência possível para navegadores antigos e com
falhas, o Bootstrap usa [_hacks_ CSS de navegador](http://browserhacks.com/) em
vários lugares para direcionar CSS especial para certas versões do navegador, a
fim de contornar falhas nos próprios navegadores.
Esses _hacks_ compreensivelmente fazem com que os validadores de CSS reclamem
que são inválidos.
Em alguns lugares, também usamos recursos CSS de ponta que ainda não estão
totalmente padronizados, mas são usados puramente para aprimoramento
progressivo.

Esses alertas de validação não importam na prática, pois a parte não hackeada do
nosso CSS valida totalmente e as partes hackeadas não interferem no
funcionamento adequado da parte não hackeada, por isso ignoramos deliberadamente
esses alertas em particular.

Nossos documentos HTML também têm alguns avisos de validação HTML triviais e
inconsequentes devido à inclusão de uma solução alternativa para
[uma determinada falha do Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=654072).
