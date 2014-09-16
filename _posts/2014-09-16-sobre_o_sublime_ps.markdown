---
layout: post
title:  "Sobre o sublime_ps"
date:   2014-09-16 16:15:48
categories: opensource
synopsis: "Apresentando a command line application desenvolvida para facilitar a troca de presets de configuração no SublimeText"
permalink: "sobre_o_sublime_ps"
---

# Sobre o sublime_ps

O [sublime_ps](https://github.com/viniciusalmeida/sublime_ps) é uma rubygem que injeta configurações pontuais no arquivo de preferências do SublimeText.

Essas configurações pontuais são informadas em pequenos arquivos de preferências (ou presets) localizados em `~/.sublime_ps`. Este é o exemplo de um desses arquivos:

```
$ touch ~/.sublime_ps/light.json

{
  "theme": "Spacegray Light.sublime-theme",
  "color_scheme": "Packages/Base16 Color Schemes/base16-solarized.light.tmTheme"
}
```

Após a configuração nos basta rodar o comando:

```
$ sublime_ps ap light
```

Nesse momento as configurações contidas em `~/.sublime_ps/light.json` serão injetadas no arquivo de preferências do SublimeText e surtirão efeito imediatamente.
