Como as opções podem ser passadas por meio de atributos de dados ou JavaScript,
você pode anexar um nome de opção a `data-bs-`, como em
`data-bs-animation="{valor}"`.
Certifique-se de alterar o formato do nome da opção de "camelCase" para
"kebab-case" ao passar as opções por meio de atributos de dados.
Por exemplo, use `data-bs-custom-class="beautifier"` em vez de
`data-bs-customClass="beautifier"`.

A partir do Bootstrap 5.2.0, todos os componentes oferecem suporte a um atributo
de dados reservado **experimental** `data-bs-config` que pode abrigar uma
configuração de componente simples como uma string JSON.
Quando um elemento tem os atributos `data-bs-config='{"delay":0, "title":123}'`
e `data-bs-title="456"`, o valor final de `title` será `456` e os atributos de
dados separados substituirão os valores fornecidos em `data-bs-config`.
Além disso, os atributos de dados existentes são capazes de abrigar valores JSON
como `data-bs-delay='{"show":0,"hide":150}'`.

O objeto de configuração final é o resultado da união de `data-bs-config`,
`data-bs-` e `js object`, onde o último valor-chave fornecido substitui os
outros.
