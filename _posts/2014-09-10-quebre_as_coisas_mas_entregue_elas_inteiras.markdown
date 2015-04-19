---
layout: post
title:  "Quebre as coisas, mas entregue elas inteiras"
date:   2014-09-10 16:15:48
categories: desenvolvimento
synopsis: "No desenvolvimento web precisamos mudar o comportamento padrão de algumas coisas mas algo que não pode ser deixado de lado é a semântica. Vamos falar um pouco sobre isso?"
permalink: "quebre_as_coisas_mas_entregue_elas_inteiras"
---

# Quebre as coisas, mas entregue elas inteiras

Hoje em dia no desenvolvimento web é comum precisarmos alterar o comportamento padrão de algumas coisas. Lendo isso você pode lembrar de uma situação ruim que passou com algum requisito maluco para o comportamento de uma página. Mas as vezes essa mudança é algo bom e de fato agrega valor ao produto final.

Eu normalmente assumo essas necessidades como uma oportunidade. Poder pegar algo existente, alterar e entregar algo novo é inspirador. Porém, atualmente não vejo o comprometimento dos desenvolvedores com a entrega coerente dessas alterações.

## É tudo uma questão de postura protecionista aos padrões

Um exemplo muito claro desse tipo de situação é o já tradicional ScrollTo. A aplicação disso é muito simples. Consiste em animar o comportamento das âncoras. Nada demais, até que a funcionalidade das âncoras é deixada de lado. Prover a experiência de animação da rolagem da página e deixar toda a experiência provida pela âncora morrer em um `preventDefault()` é burrice.

Seguindo nesse exemplo de ScrollTo desenvolvi um plugin chamado [jQuery.semanticScrollTo](https://github.com/viniciusalmeida/jQuery.semanticScrollTo) que entrega essa experiência de uma forma que julgo correta. Possibilitando ao usuário ter referência dentro da página (para usar como um link, por exemplo). Que é a mesma experiência provida pelo uso de âncoras na sua forma mais rústica.

E aqui é que fica minha mensagem: cabe ao desenvolvedor refletir sobre essas funcionalidades e linkar isso tudo com o que já existe no contexto - é bem possível que algumas pessoas não vinculem o ScrollTo com âncoras, acredite. Fazer todo o possível para proteger a integridade da web é nossa obrigação.

## Conclusão

Minha solução para o problema não expressa nenhuma virtuosidade técnica na sua aplicação. Porém, o ponto não é esse. Na verdade é exatamente o oposto disso.

A palavra chave disso tudo está no nome do plugin mencionado acima. A semântica, junto com a funcionalidade, precisa ser considerada e muito bem ponderada quando desenvolvemos algo para a internet. Um ambiente que apesar de livre, tem seus padrões e convenções. E eles tem seus motivos para estarem lá.
