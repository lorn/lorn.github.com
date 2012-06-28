---
layout: post
title: "A Busca Pelo Deploy Contínuo - Parte 1"
date: 2011-12-02 11:23
comments: true
categories: [talk, yapc, perl, deploy]
---

<div id="litlebox">
Você está lendo a Parte 1 sobre "A Busca pelo deploy contínuo" esse post tem mais duas continuações: <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-2/">Parte 2</a> e <a href="/blog/2011/12/03/a-busca-pelo-deploy-continuo-parte-3/">Parte 3.</a>
</div>

No dia 05/11 apresentei  no [YAPC::Brasil](http://www.yapcbrasil.org.br/2011/) uma palestra com o nome
"Em busca do deploy continuo" nesse post vou tentar descrever sobre tudo o que eu falei.

<div style="width:425px" id="__ss_10173611"> <strong style="display:block;margin:12px 0 4px"><a href="http://www.slideshare.net/lornlab/a-busca-pelo-deploy-continuo" title="A busca pelo deploy continuo" target="_blank">A busca pelo deploy continuo</a></strong> <iframe src="http://www.slideshare.net/slideshow/embed_code/10173611" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> <div style="padding:5px 0 12px"> View more <a href="http://www.slideshare.net/" target="_blank">presentations</a> from <a href="http://www.slideshare.net/lornlab" target="_blank">Lindolfo Rodrigues Oliveira Neto</a> </div> </div>


## Como começar? ##

Infelizmente o principal problema do "Deploy Continuo" não é técnico e sim cultural, e mudança de cultura é muito mais difícil que mudança de Banco de Dados ou de Linguagem de Programação é enraizado nas fundações da empresa, esses são alguns exemplos culturais:

* Falta de confiança

* Processos complicado/complexos para tudo

{% blockquote %}
Processo é uma reação à estupidez incorporada antes
 - Clay Shirky
{% endblockquote %}

 Em português claro, esse seria o famoso "vai que..." :

 * Vai que alguém faz uma alteração errada e o site fica fora do ar
 * Vai que alguém cria uma tabela nova e o site fica fora do ar.

Ainda bem que esse pessoal de processo não conhece o [Efeito Borboleta](http://pt.wikipedia.org/wiki/Efeito_borboleta) se não eles iam criar coisas bem piores.

Em Startups esse tipo de coisa não acontece porque, geralmente, se tem pouco recurso e é necessário já pensar em Deploy/Integração continua desde o início, pois você precisa entregar valor para seu usuário para continuar vivo, você não tem uma receita fixa. 

Então, se você for esperar a próxima madrugada para subir a funcionalidade que já está pronta, , fica dificil pivotear talvez essa funcionalidade não seja bem vista por seus usuários, eles entenderam errado, então é necessário não só coloca-la rápida em produção como tirar rápido também :)

Imagine demorar 48h para concluir esse fluxo todo, você pode perder usuários preciosos.

O [github.com](http://github.com) que é era uma startup e agora, mesmo depois de passar dos 40 funcionários, continua com as mesmas idéias de desenvolvimento baseado em software livre e deploy contínuo.

Caso você queira conhecer como funciona o processo de desenvolvimento/trabalho no github, eu recomendo a lida desse [post do Zach Holman](http://zachholman.com/posts/how-github-works/) que é um dos funcionário mais antigos por lá e caso você não queira conhecer :)

Recentemente [ele deu uma palestra](http://zachholman.com/talk/how-github-uses-github-to-build-github) falando um pouco mais sobre isso e como se usar o github como plataforma para esse processo ser aplicado em qualquer empresa.

Mas até agora, eu sou falei de empresinhas pequenas, por mais que elas ganhem algum dinheiro não tem um nome a zelar.

{% blockquote %}
Quero ver isso funcionar em uma empresa grande!
 - Cara de processo
{% endblockquote %}

Funciona, vou te dizer dois exemplos:

* Amazon

* Etsy

A [Amazon](http://amazon.com) chegou a divulgar em um apresentação na Velocity 2011 que faz um deploy a cada 11.6 segundos e você aí feliz por ter conseguido uma janela mais cedo para fazer seu deploy né?

A [Etsy](http://etsy.com), não é muito famosa aqui no Brasil, e a conheci ela antes de me interessar sobre deploy continuo comprei um adesivo com uma frase de StarWars lá :) eles funcionam como um Mercado Livre para artesões e outras profissões "hand-made".

Eles tem a bagatela de 1 bilhão de pageview por mês!

Caso você queira entender como funciona o deploy continuo na Etsy, e como era a vida deles antes do deploy continuo veja essa palestra:

<iframe width="560" height="340" src="http://cdn.livestream.com/embed/etsy?layout=4&amp;clip=pla_adbab6e2-c629-4bfe-b1fd-21c898693282&amp;height=340&amp;width=560&amp;autoplay=false" style="border:0;outline:0" frameborder="0" scrolling="no"></iframe><div style="font-size: 11px;padding-top:10px;text-align:center;width:560px">Watch <a href="http://www.livestream.com/?utm_source=lsplayer&amp;utm_medium=embed&amp;utm_campaign=footerlinks" title="live streaming video">live streaming video</a> from <a href="http://www.livestream.com/etsy?utm_source=lsplayer&amp;utm_medium=embed&amp;utm_campaign=footerlinks" title="Watch etsy at livestream.com">etsy</a> at livestream.com</div>

Tudo isso começou na Etsy, porque um ex-flickr foi contratado para ser o CTO lá e o flickr foi bem pioneiro nesse negócio de deploy contínuo, você pode ver um pouco mais sobre isso nessa outra palestra:

<iframe src="http://blip.tv/play/AYGMoH8C.html" width="480" height="300" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#AYGMoH8C" style="display:none"></embed>
    

## Continua .. ##


<div id="litlebox">
Você está lendo a Parte 1 sobre "A Busca pelo deploy contínuo" esse post tem mais duas continuações: <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-2/">Parte 2</a> e <a href="blog/2011/12/03/a-busca-pelo-deploy-continuo-parte-3/">Parte 3.</a>
</div>

