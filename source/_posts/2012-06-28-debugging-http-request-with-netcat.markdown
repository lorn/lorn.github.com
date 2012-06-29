---
layout: post
title: "Debugging HTTP Request With Netcat"
date: 2012-06-28 20:45
comments: true
published: true
categories: [linux, dev]
---

O que fazer quando você precisa usar uma API de terceiros e tudo funciona bem quando você está fazendo seus testes com curl.

```
$ curl https://api.github.com/repos/lorn/lwp-curl/commits
```

Mas quando você vai para sua linguagem botar a mão na massa, dá erro:

```
$ curl "https://api.github.com/repos1/lorn/lwp-curl/commits1"

{
  "message": "Not Found"
}
```

é claro que nem sempre o erro será tão claro, e principalmente quando você está fazendo POST/PUT com arquivos, como debugar? porque funciona no curl e não funciona na minha linguagem preferida?

{% blockquote %}
Netcat for the rescue!
{% endblockquote %}

Netcat é o canivete suiço do mundo unix, se você nunca ouviu falar e quer aprender até a transferir arquivos via Netcat (!!) veja esse post do [pkrumins](http://www.catonmat.net/blog/unix-utilities-netcat/) nesse caso especifico, vamos usar Netcat para debugar requisições HTTP e isso ele não mostra lá ;)

Essa requisição do curl:

```
$ curl "localhost:9999/repos/lorn/lwp-curl/commits"
```

Aparece assim no Netcat

```
$ nc -l localhost 9999
GET /repos/lorn/lwp-curl/commits HTTP/1.1
User-Agent: curl/7.21.4 (universal-apple-darwin11.0) libcurl/7.21.4 OpenSSL/0.9.8r zlib/1.2.5
Host: localhost:9999
Accept: */*
```

Agora ao invés de usar o curl, manda sua aplicação fazer o POST/PUT para o Netcat ( localhost:9999 nesse exemplo ) e vê o que o curl manda o sua aplicação não manda, no meu caso eu tinha esquecido de enviar o arquivo usando [HTTP Multipart](http://www.w3.org/Protocols/rfc1341/7_2_Multipart.html).

Para usar o Netcat no Mac:

```
$ nc -l localhost 9999
```

Linux:

```
nc -l -p 9999
```

Dica do [dsouza](http://dsouza.github.com/b/)
    
