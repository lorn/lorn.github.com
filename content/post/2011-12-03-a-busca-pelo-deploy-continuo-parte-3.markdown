---
title: "A Busca Pelo Deploy Contínuo - Parte 3"
date: 2011-12-03T10:03:00-03:00
categories: [talk, yapc, perl, deploy]
---

<div id="litlebox">
Você está lendo a Parte 3 sobre "A Busca pelo deploy contínuo" eu recomendo você a começar pela <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-1/">Parte 1</a> e depois ler a <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-2/">Parte 2</a> se você já o fez, continue ;)
</div>


Agora um exemplo de arquitetura para facilitar o uso do deploy continuo usando um [Load Balancer](http://en.wikipedia.org/wiki/Load_balancing_(computing)).

Você não precisa de applicances milionários para fazer isso [o github](http://www.anchor.com.au/blog/2009/10/load-balancing-at-github-why-ldirectord/), serve 2500 conexões TCP por **SEGUNDO** usando o [ldirectord](http://horms.net/projects/ldirectord/) em uma máquina Xen com 128mb.

Com um Load Balance, você consegue testar funcionalidades novas no site para uma pequena porção dos usuários do site e usar os gráficos ( que você já tem lógico ) para ver se ela é boa ou não.

Como fazer isso? faça o deploy para apenas 1 das 'n' máquinas que você tem atrás do Load Balancer e redirecione, 5% ~ 10% das suas conexões dos seus usuários para essa máquina, o resto os gráficos que você preparou da sua aplicação irão te dizer ;)

Falando um pouco mais de arquitetura, e especificamente de Perl, eu gosto bastante de usar o Nginx + Starman a comunicação é feita via Unix Socket o Starman foi baseado no Unicorn do Ruby, ele funciona muito bem e...

<iframe width="420" height="315" src="https://www.youtube.com/embed/dFUlAQZB9Ng" frameborder="0" allowfullscreen></iframe>

"It's a unix system I known this!" arquiteturas unix, forks, sockets e afins funcionam muito bem :)

O seu deploy consistiria em copiar os arquivos novos e mandar um sinal de reset para o pid do Starman:

{% codeblock %}
$ kill -s USR2 1337
{% endcodeblock %}

Ele vai recarregar o código, e vai reiniciar todos os seus fork assim que eles forem ficando sem conexões ou seja para seus usuários a percepção de downtime será **ZERO!**

Abaixo uma conf de exemplo para se usar no Nginx para se conectar a um socket gerado pelo Starman:

{% gist 1126172 %}

Bom, basicamente é isso se tiver alguma duvida pergunte nos comentários :)

## Bibliografia ##

Alguns slides foram copiados dessa palestra da etsy:

<div style="width:425px" id="__ss_8727786"> <strong style="display:block;margin:12px 0 4px"><a href="https://www.slideshare.net/OReillyOSCON/put-a-button-on-it-removing-barriers-to-going-fast" title="Put a Button on It: Removing Barriers to Going Fast" target="_blank">Put a Button on It: Removing Barriers to Going Fast</a></strong> <iframe src="https://www.slideshare.net/slideshow/embed_code/8727786" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> <div style="padding:5px 0 12px"> View more presentations from <a href="https://www.slideshare.net/OReillyOSCON" target="_blank">OSCON </a> </div> </div>

E outros foram copiados dessa palestra da AOE Media

<div style="width:425px" id="__ss_5345889"> <strong style="display:block;margin:12px 0 4px"><a href="https://www.slideshare.net/typo3media/continuous-deployment-5345889" title="Continuous deployment" target="_blank">Continuous deployment</a></strong> <iframe src="https://www.slideshare.net/slideshow/embed_code/5345889" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe> <div style="padding:5px 0 12px"> View more <a href="https://www.slideshare.net/" target="_blank">presentations</a> from <a href="https://www.slideshare.net/typo3media" target="_blank">Daniel</a> </div> </div>

Obrigado :) qualquer dúvida estou a disposição nos comentários.
