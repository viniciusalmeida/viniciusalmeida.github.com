---
layout: post
title:  "Fat arrow functions em classes do CoffeeScript"
date: 2014-10-07 16:15:48
categories: CoffeeScript
synopsis: "Nesse post falo um pouco sobre a facilidade proporcionada pelas fat arrow functions e também sobre o seu funcionamento."
permalink: "fat_arrow_functions_no_coffeescript"
---

# Fat arrow functions em classes do CoffeeScript

Tive meu primeiro contato com o [CoffeeScript](http://coffeescript.org) quando entrei para o time da [CodeMiner](http://www.codeminer42.com/). Antes disso não tive nenhum interesse na linguagem, a idéia de ter um intermediário antes de chegar no JavaScript final do meu projeto e o fato de não entender o real controle que eu teria sobre o resultado final do _transpile_ me deixavam com receio quanto ao uso.

A partir do meu contato com a linguagem cada um desses assuntos que me preocupavam iam sendo esclarecidos e hoje minha preferência é pelo Coffee, de longe. Apesar de eu sempre aconselhar qualquer iniciante a estudar o JavaScript primeiro para entender que o Coffee é mais do que uma ferramenta pra escrever código para o front de uma forma hipster. Ele de fato nos ajuda a resolver problemas.

Vez por outra me pego transpilando trechos de código para entender como o Coffee resolve determinados problemas, e me deparo com coisas bem interessantes. Nesse post compartilho minhas deduções de como funcionam as _fat arrow functions_ nas classes que escrevemos em CoffeeScript.

O propósito do post não é de converter alguém para o CoffeeScript, mas expõe uma maneira de tratar o problema que esse recurso da linguagem resolve.

## O `this` no JavaScript

Este certamente é um dos assuntos mais emblemáticos para quem está tendo seu primeiro contato com a linguagem. Em resumo, por padrão, o `this` sempre é referente ao contexto da função. Enquanto modularizamos nosso JavaScript é comum termos problemas para acessar o contexto esperado quando trabalhamos com callbacks, por exemplo. Uma solução é a utilização de closures para oferecer uma referência ao contexto desejado - o já conhecido `var that = this` ou equivalente.

Podemos utilizar também alguns recursos da linguagem para poder forçar esse contexto, mas eu não considero prático. Isso eleva a complexibilidade do código escrito e nos faz sujar nossas mãos com a aplicação dessa solução em escala. Além disso, essa solução fica ainda menos necessária quando sabemos que temos ferramentas como o CoffeeScript que abstrai isso com maestria.

Apesar de termos a opção de utilização do `call`, estamos falando do `apply`. Um recurso do JavaScript para invocarmos uma função forçando seu contexto.

### Como esse tal `apply` functiona?

O `apply` é um método do objeto `Function`. Para invocarmos uma função através dele e forçarmos o contexto para a mesma precisamos transmitir dois parâmetros pra ele: o objeto que desejamos que seja o contexto da função e um array que será convertido em argumentos para a mesma.

```javascript
myFunction.apply(myContext, ['my', 'arguments']);
```

A linha acima invoca `myFunction(['my', 'arguments'])`, sendo que o contexto da execução dessa função será `myContext`.

## Como as _fat arrow functions_ tiram proveito de `apply`

A especificação ES6 trouxe do CoffeeScript as _arrow functions_. Mas meu aspecto preferido da linguagem são as _fat arrow functions_. São elas que nos são servidas para resolver esse problema de complexibilidade dos escopos fazendo uso do `apply`.

Dando uma olhadinha no JavaScript gerado pelo Coffee podemos observar que ao utilizarmos as _fat arrows_ ele cria uma função denominada `__bind` que retorna uma função que aplica o contexto da nossa classe ao método passado no primeiro parâmetro. Vejamos:

```javascript
__bind = function(fn, me) {
  return function() {
    return fn.apply(me, arguments);
  };
};
```

No construtor do nosso objeto ele invoca o `__bind` e sobrescreve o método fazendo uso de closure para manter a referência à função retornada:

```javascript
this.yourFunction = __bind(this.yourFunction, this);
```

Observando essa linha podemos verificar que o CoffeeScript fez o trabalho sujo de manipular o contexto da função para nós. Mesmo que a estratégia para a solução seja bastante simples, não seremos obrigados a escrever esse código.

## Conclusão

O ganho real da utilização desse recurso é em quesitos como legibilidade e estilo de código. Assuntos bastante subjetivos, onde o gosto pessoal de cada desenvolvedor acaba contando.

Gosto muito da forma como a utilização de `=>` na definição de um método pode abstrair todo esse código e nos livra do tratamento desses aspectos do JavaScript. Mas volto a bater na tecla: precisamos conhecer JavaScript o suficiente para compreendermos o valor do CoffeeScript, ou qualquer outra linguagem que transpile para a inguagem.

Se você não é adepto ao CoffeeScript e sempre ficou incomodado com a utilização de `var that = this` igual a mim. Apenas conhecer a forma como o a linguagem contorna o problema pode te inspirar em achar uma solução baseada nisso tudo para aplicar nos seus projetos.
