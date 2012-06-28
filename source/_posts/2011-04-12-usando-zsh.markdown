---
layout: post
title: "Usando ZSH"
date: 2011-04-12 13:31
comments: true
categories: [zsh, dev, workspace]
---
Esses dias re-descobri o zsh, já havia testado a um tempo atrás mas agora foi pra valer :)

E vou dizer, não há shell melhor :) muito melhor que o Bash

* O historico do ZSH é compartilhado por *TODAS* sessões dele, diferente do bash que cada sessão tem seu histórico 
( e você tem que ficar procurando onde foi que digitou aquele comando para recuperar ele do histórico ).

* ZSH tem autocomplete para tudo, ok bash também, mas o ZSH é bem mágico ele tem autocomplete para o kill, listando os 
processos que estão rolando e você digita o nome ele já tras o pid para você, ps -aux? nunca mais.

* Autocomplete do ssh baseado no seu ~/.ssh/know_hosts ou seja, acessou a maquina, ssh ma<tab> autocomplete :D

* Continuando o autocomplete, no MacOSX temos um instalado de pacote chamado brew para instalar pacotes nele é
 mais ou menos como no apt-get, busca e depois install então: brew seach xyz, brew install xyz. Com o zsh ele irá fazer
 a busca no install então brew install x<tab> pronto, já mostra para você todos os pacotes que casam com aquela string.

* E bem compativell com o bash, eu não tive nenhum problema em fazer: cat ~/.bashrc >> ~/.zshrc e tudo que eu tinha configurado no bash funciona no zsh

Comece usando agora é só seguir a receita de bolo desse repositorio [https://github.com/robbyrussell/oh-my-zsh/](https://github.com/robbyrussell/oh-my-zsh/) ele deixou
 o zsh bem bonito, com suporte a temas e plugins ( e você verá como é facil fazer temas e plugins ) o meu fork desse repositorio você acha aqui.

Esse são os motivos básicos, caso eu lembro de mais algum matador eu coloco aqui. Mas fica a dica, use zsh e [filtro solar](http://www.youtube.com/watch?v=3oB2rMaY0ho&feature=related).
