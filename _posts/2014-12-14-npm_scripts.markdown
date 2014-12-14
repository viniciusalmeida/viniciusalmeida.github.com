---
layout: post
title:  "NPM scripts detonam"
date:   2014-12-14 15:42:00
categories: CoffeeScript
synopsis: "Dicas para você tirar proveito dos npm scripts ao escrever pacotes node com o CoffeeScript."
permalink: "npm_scripts_detonam"

---

# NPM scripts detonam

Se você, assim como eu, é um grande fã do [CoffeeScript](http://jashkenas.github.io/coffeeccript) e já quiz escrever algum pacote para [node](http://nodejs.org) utilizando a linguagem mas acha que versionar arquivos transpilados é idiotice eu tenho uma solução pra te apresentar.

## Os [NPM scripts](https://docs.npmjs.com/misc/scripts)

NPM scripts provêm uma série de "gatilhos" onde podemos configurar comandos de qualquer natureza. Talvez você já esteja familiarizado com o `npm test` de alguns projetos para rodar um mocha.js por exemplo.

Mas ao fazermos uso do operador `&&` nos nossos npm scripts podemos ir bem além de chamar um comando em cada um deles. Veja no exemplo o `npm test` do projeto [differenceBetweenTimes](https://github.com/viniciusalmeida/differenceBetweenTimes) onde o operador está sendo usado para rodar um segundo comando no script de testes:

```json
"scripts": {
  "test": "coffee -c ./test ./lib && mocha --reporter spec",
}
```

### Ainda em tempo: `npm install`

O `install` é disparado logo após a instalação do pacote. Considere utiliza-lo para manter seu pacote livre dos arquivos JavaScript que não são seus.

## O que ganhamos com isso?

Nesses exemplos que mencionei podemos combinar o _transpile_ e inicio dos testes com o `&&` e ainda rodar através do `install` o comando do CoffeeScript para gerar esses arquivos js que não são de nossa responsabilidade na própria máquina do usuário. Mas veja documentação linkada e use a sua imaginação.

Dá pra fazer muita coisa bacana com esse recurso!
