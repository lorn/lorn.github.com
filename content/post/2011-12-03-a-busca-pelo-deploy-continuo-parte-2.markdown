---
title: "A Busca Pelo Deploy Contínuo - Parte 2"
date: 2011-12-02T11:23:00-03:00
categories: [talk, yapc, perl, deploy]
---
<div id="litlebox">
Você está lendo a Parte 2 sobre "A Busca pelo deploy contínuo" eu recomendo você a começar pela <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-1/">Parte 1</a> mas se já leu as duas partes, leia a <a href="/blog/2011/12/03/a-busca-pelo-deploy-continuo-parte-3/">Parte 3</a>.
</div>

Agora que você já está convencido que precisa disso, ou não, vou começar a falar de algumas ferramentas/técnicas que você pode usar para te ajudar no processo:

* SCM - Software Configuration Management  

  Também conhecido como VCS ( Version Control System ), você precisa disso, se você não tem **há algo muito errado** e se você está usando Subversion, isso não é tão ruim, mas comece a usar git a partir de hoje, sério.
  
* Testes
  
  Se você acha que teste é besteira, então deploy continuo é besteira para você também. É impossível ter um deploy contínuo confiável sem testes
  
* Continuos Integration Software

  Esse tipo de software tem um papel simples, porem eficaz, ele fica fazendo "pooling" no seu SCM, a cada commit seu ele vai rodar o seu processo de "build" para ver se ele continua funcionando depois do código que você acabou de comitar, um processo de build pode conter:

  * Gerar pacotes
  * Verificar códigos/dependências
  * Testes Unitários
  * Testes de Integração
  * Testes de Segurança
  * Testes funcionais
  
  E caso algum teste tenha parado de funcionar, ele vai te enviar um email avisando que o build está quebrado.

  Eu uso e gosto bastante do [Jenkins](http://jenkins-ci.org/), conhecido antes como Hudson. Mas há muitos outros por ai, você só precisa escolher um.
  
* Script de Deploy/Rollback para você começar, depois de ter todas essas coisas acima, você já pode a pensar em automatizar seu processo de deploy/rollback.

  * ./deploy.sh    # faz o deploy
  * ./rollback.sh  # faz o rollback do ultimo deploy
  
  Simples assim, mas tem que ser um script só que faz todo o trabalho, copiar arquivos, reinciar webserver etc
  
  Na Etsy quando o script ficou avançado eles evoluiram para um software web, que inclusive é opensource mais detalhes aqui: [Deploynator Etsy](http://codeascraft.etsy.com/2010/05/20/quantum-of-deployment/)
  
* Puppet/Chef - eu não sei qual o nome dessa categoria de software, o que você faz com eles é escrever "receitas" de máquinas, imagine que a empresa está crescendo e você precisa montar 10 novos webservers que incluem:

  * Instalar SO
  * Configurar SO
  * Configurar Firewall
  * Configurar Webserver
  * Configurar seu sistema
  * Colocar ela no pool de webservers
  
  Tirando a instalação do Linux, todo o resto você pode automatizar com puppet ou chef você cria receitas nele dizendo como ele vai configurar seu Webserver, seu sistema e depois é só executar essa receita na máquina ele vai instalar o pacote e fazer todo o trabalho pra você.
  
  E você vai precisar fazer isso UMA vez para 'n' maquinas, e quando precisar mudar algo e só alterar na receita ele mantém as maquinas sincronizadas com sua receitas, nada de sair editando o mesmo arquivo em várias máquinas.
  
* Monitoramento

  * Sistema Base/Nagios 
  
    Você precisa monitorar o estado do seu sistema, vê se o Apache tá de pé se o disco tá cheio isso é bem comum, no minímo você já ouviu falar.
    
  * Seu negócio
  
    Você precisa também monitorar o seu negócio, você precisa saber que horas que acontecem mais vendas e precisa saber agora, nada de rodar aquela query no banco de dados **faça gráfico de toda informação que você puder monitorar**.
    
    Além desses gráficos ajudar o pessoal de Marketing/Vendas vai te ajudar quando entrar alguma funcionalidade nova no site, porque sempre tem um espertão na empresa, e muitas vezes esse espertão é o dono, que vai dizer:
    
    {% blockquote %}
    Acho que depois que você colocou aquela funcionalidade no site, o site está vendendo menos, estou com esse pressentimento.
     - Espertão
    {% endblockquote %}
    
    A Etsy liberou recentemente a ferramente que eles fizeram para fazer gráficos, vale a pena dar uma olhada [Measure Anything, Measure Everything](http://codeascraft.etsy.com/2011/02/15/measure-anything-measure-everything/) eles contam bastante expêriencia deles com geração de gráfico para tudo, até para a quantidade de café na cozinha!
    
    Então tenha gráficos de tudo e mostre para ele no melhor sentido [Opa chefe! tranquilo chefe!](https://twitter.com/opachefe).

## Continua .. ##

<div id="litlebox">
Você está lendo a Parte 2 sobre "A Busca pelo deploy contínuo" eu recomendo você a começar pela <a href="/blog/2011/12/02/a-busca-pelo-deploy-continuo-parte-1/">Parte 1</a> mas se já leu as duas partes, leia a <a href="/blog/2011/12/03/a-busca-pelo-deploy-continuo-parte-3/">Parte 3</a>.
</div>
