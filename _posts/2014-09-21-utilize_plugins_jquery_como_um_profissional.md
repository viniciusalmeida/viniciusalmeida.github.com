---
layout: post
title:  "Utilize plugins jQuery como um profissional"
date: 2014-09-22 16:15:48
categories: jQuery
synopsis: "Estamos muito bem familiarizados com plugins da jQuery. Reconhecemos seus padrões de inicialização e transmissão de nossas preferências para eles. Vamos utilizar essa familiaridade a nosso favor, aplicando uma técnica de auto inicialização e elevando a qualidade do nosso código."
permalink: "utilize_plugins_jquery_como_um_profissional"
---

# Utilize plugins jQuery como um profissional

Eu sou um grande fã da jQuery. A forma que escrevemos plugins para a biblioteca me deixa bastante satisfeito quanto a modularização dos componentes/plugins necessários em nossas páginas.

Já estamos todos muito bem familiarizados com esses plugins, sejam eles desenvolvidos por nós mesmos ou por terceiros. Reconhecemos também uma certa convenção na maneira que os inicializamos e também de como transmitimos nossas preferências a eles.

Porém, a aplicação dos mesmos tende a ser repetitiva e também muito específica para cada caso, o que acaba engessando nosso código.

## O problema

Trechos como esse são muito comuns na aplicação de alguns desses componentes/plugins:

```javascript
$(function() {
  $('#any-selector').hypotheticPlugin({
    firstProperty: '...',
    anotherProperty: '...'
  });
});
```

Se precisarmos inicializar mais um plugin no contexto citado acima, ou até o mesmo plugin em um elemento diferente, nosso código de inicialização começa a ficar grande, feio e desajeitado. Essa estratégia de implementação simplesmente não escala. Na medida que seu site ou aplicação cresce, essa situação começa a gerar cada vez mais código ruim. Você deve concordar comigo quando afirmo que isso é um problema.

## Vamos resolver essa situação

Temos muitas formas de solucionar isto. Vou me apoiar em recursos da própria jQuery para propôr um padrão bastante simples de auto inicialização desses plugins para manter o código enxuto e escalável. Tudo isso baseado nos padrões observados e mencionados acima. Para isso vamos fazer uso de [_custom data attributes_](http://www.w3.org/TR/2011/WD-html5-20110525/elements.html#custom-data-attribute) mantendo a responsabilidade de guardar as informações referentes ao plugin e seu uso no próprio elemento onde o mesmo será aplicado.

### Método `.data()` do jQuery

A jQuery implementa esse método que se responsabiliza de serializar os _data attributes_ dos elementos. Ele nos retorna um objeto com todas as informações que armazenamos nesses atributos.

Levando em consideração essa abordagem, a marcação de um elemento onde o plugin hipotético do exemplo acima será aplicado ficaria assim: `<div data-jquery-plugin="hypotheticPlugin" data-first-property="..." data-another-property="...">`.

Ao utilizarmos o `.data()` para serializar os _data attributes_ da marcação acima, temos o seguinte retorno:

```javascript
{
  jqueryPlugin: "hypotheticPlugin",
  firstProperty: "...",
  anotherProperty: "..."
}
```

A semelhança entre o objeto retornado e o objeto de preferências transmitido para o plugin ao ser iniciado da forma padrão é inegável. Então vamos fazer uso disso. Agora nos basta iterar os elementos que terão algum plugin aplicado e utilizar esse objeto que já possui todas as propriedades que precisamos:

```javascript
$(function() {
  var elementsToApplyPlugins = $('[data-jquery-plugin]');
  $.each(elementsToApplyPlugins, function(__index, element) {
    var currentElement = $(element);
    var options        = currentElement.data();
    currentElement[options.jqueryPlugin](options);
  });
});
```

## O que ganhamos com tudo isso

Ao utilizarmos esse padrão para a inicialização dos plugins de nossas páginas tornamos esse processo - vou bater de novo nessa tecla - escalável. Não mais teremos que fazer código JS tão específico quanto o mencionado na seção onde descrevemos o problema que estamos solucionando.

Toda a informação necessária para o funcionamento do plugin está agora no elemento onde o mesmo será aplicado. Se o aplicarmos no mesmo contexto de página em dois elementos, porém necessitando de propriedades distintas em cada um deles, basta distinguirmos isso na marcação de ambos. Não precisamos mais manipular objetos onde setamos as preferências para cada um desses casos e os plugins serão inicializados automaticamente.

Na medida que seu site ou aplicação for crescendo. Essa solução (ou qualquer outra similar que você tenha adotado) vai se mostrar cada vez mais importante.
