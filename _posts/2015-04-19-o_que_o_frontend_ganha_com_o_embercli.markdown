---
layout: post
title:  "O que o front end ganha com o ember-cli"
date:   2015-04-19 15:42:00
synopsis: "Sendo bastante sincero, nunca fui fã do Ember como framework. Porém, não posso fechar os olhos para os interessantes impactos do ember-cli no workflow de desenvolvimento front end."
permalink: "o_que_o_front_end_ganha_com_o_embercli"

---

# O que o front end ganha com o ember-cli

Sendo bastante sincero, nunca fui fã do framework [Ember.js](http://emberjs.com/). Para mim ele não passa de mais um item da já demasiadamente grande e constantemente crescente lista de frameworks JavaScript.

Porém, venho o utilizando em um projeto e não posso fechar os olhos para os aspectos que estão sendo implementados através da sua ferramenta de `CLI` no workflow de desenvolvimento front end - e estavam fazendo falta.

Pra quem não conhece, o [ember-cli](http://www.ember-cli.com/) é uma ferramenta que provê asset pipeline e __convenções de estrutura__ de aplicações feitas com o framework.

## A chave de tudo são as convenções combatendo o bikeshedding

Mencionei acima as __convenções de estrutura__. Isso parece algo muito pequeno, não posso tirar a razão de quem pensa assim. Mas o que importa aqui é o significado dessa postura e o que isso pode representar.

> Queremos ter o máximo de tempo que pudermos para as tarefas desafiadoras.
>
> _-- Yehuda Katz_

Pensando da mesma forma que o Yehuda, empregar tempo discutindo aspectos triviais a respeito das nossas aplicações além de ser desgastante e custoso, é também tolice. Devemos otimizar nosso tempo para empregá-lo no que realmente importa.

Na CodeMiner, utilizamos o termo _bikesheeding_ para nomear esse fenômeno que impacta muito pouco no valor do produto final. E nós o combatemos. Como? Com convenções.

A idéia não é eliminar a discussão de aspectos dessa natureza, mas levar esse debate para um ecossistema maior do que o das nossas aplicações de forma individual.

### Convenção de tooling

Aqui fica muito clara a utilidade de um _mantra_ que aprendi ao ter contato com o Ruby on Rails: __convenções acima das configurações__.

Termos opções de tooling _build in_ no framework de nossa escolha para desenvolver nossas aplicações representa menos tempo decidindo (e acima de tudo configurando) aspectos como:

* Uma suite de testes
* Uma forma de _mockar_ as respostas esperadas de uma API
* Formas de gerenciar dados especializados para cada ambiente
* Formas de compilar nossos assets

Eliminar essas decisões do nosso workflow diário representa ganhos expressivos. Afinal, só nesses aspectos supracitados temos uma infinidade de coquetéis de ferramentas. Essa quantidade de opções nos confunde e tem efeito paralisante, a teoria do [Paradoxo da escolha](http://www.ted.com/talks/barry_schwartz_on_the_paradox_of_choice?language=pt) nos mostra que esse ambiente não é saudável. Principalmente quando falamos sobre produtividade.

## Conclusão

Minha intenção aqui foi de indicar o movimento que a comunidade do Ember está realizando para melhorar o trabalho com a ferramenta focando bastante nas convenções que eles estão adotando. Essa postura deveria ser norte para a comunidade de desenvolvimento front end em geral.

É preciso focar no valor final e melhorar o caminho até lá. Discutir caminhos alternativos infinitos para o nosso objetivo não me parece a melhor opção.

A necessidade desse movimento já foi indicada pelo Lucas Mazza [no FrontInPOA de 2013](https://youtu.be/2iA-Z_xu3DE) (através dessa palestra que conheci a citação do Yehuda e a teoria do _Paradoxo da escolha_ :P). Venho pensando sobre isso desde que fui ao evento e esse me parece ser o primeiro indício dessa mudança. Que o seja!
