---
layout: post
title:  "Sobre o jQuery.toggleModifier"
date:   2015-05-18 15:42:00
synopsis: "Apresentando o plugin jQuery que facilita a vida de quem usa BEM pra organizar o CSS."
permalink: "sobre_o_jquery_toggleModifier"

---

# Sobre o jQuery.toggleModifier

**TL&DR:** O [jQuery.toggleModifier](https://github.com/viniciusalmeida/jQuery.toggleModifier) é um plugin desenvolvido para o jQuery que facilita a vida de programadores que optam pelo uso da [metodologia BEM](https://en.bem.info/method/) para organizar seu CSS e por conta disso tem dificuldades com a manipulação dos modificadores que representam os status nas suas aplicações.

---

Quem já trabalhou com o BEM juntamente com a jQuery sabe que uma forma recorrente de se manipular modificadores no padrão do BEM com o jQuery é através do `.toggleClass()` mas  também deve reconhecer que essa abordagem não é muito elegante. Veja o exemplo adicionando um modificador ao elemento HTML `<div class="block_element"></div>`:

```javascript
.toggleClass('block__element--modifier');
```

Essa abordagem tem reflexos ruins no código. Escrevemos demais - o que nos interessa é apenas a parte final da classe, a que representa o nosso modificador - e nosso código JavaScript fica extremamente atrelado ao parentesco entre os elementos dentro do nosso bloco.

Pensando nisso tudo cheguei ao `toggleModifier()`. Uma forma de adicionar e remover modificadores que leva em consideração as classes já existentes no elemento HTML manipulado pelo método. Esse _approach_ me pareceu uma solução eficiente para abstrair a lógica necessária para a manipulação desses modificadores.

## Utilização

Para adicionarmos ao elemento HTML `<div class="block__element"></div>` o modificador `--active` basta utilizarmos a seguinte instrução:

```javascript
$('.block__element').toggleModifier('active');
```

Isso é o suficitente para remover/adicionar o modificador e ainda por cima o `.toggleModifier()`  permite que vários modificadores diferentes sejam manipulados no mesmo elemento.

Vá até o [repositório no GitHub](https://github.com/viniciusalmeida/jQuery.toggleModifier) e conheça melhor a ferramenta.
