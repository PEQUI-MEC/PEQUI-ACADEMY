![](https://github.com/PEQUI-MEC/PEQUI-ACADEMY/blob/master/Pequi%20Academy.jpg)

# Pequi Academy

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/PEQUI-MEC/PEQUI-ACADEMY/blob/master/docs/LICENSE)
 
Olá! Esse é o repositório onde desenvolvemos nosso sistema e nossas cenas para nossas transmissões ao vivo do Pequi Academy. Utilizamos o ![Open Broadcaster Software](https://obsproject.com) como nossa plataforma de streaming em conjunto com outras ferramentas instanciadas em um container ![Docker](https://www.docker.com).

Nosso repositório é aberto pois entendemos que nosso maior trabalho é agregar nossas pesquisas e conhecimentos ao mundo acadêmico e comercial.

Estamos abertos a responder qualquer dúvida e sugestão através do nosso email contato@pequimecanico.com. Mais informações em nosso [SITE](https://pequimecanico.com/).

# Como utilizar o OBS

# Como a usar o servidor de streaming

Primeiro deve-se ter o Docker instalado no seu computador. O mesmo pode ser instalado utilizando uma das formas descritas no próprio ![link](https://docs.docker.com/install). 

## Status e progresso

Os serviços de streaming podem ser verificados inserindo diretamente ao browser http://<ip_do_servidor>:8080/stat. 

## Stream local
Pode-se utilizar diretamente o comando abaixo ou caso deseje é possivel utilizar o Dockerfile e o script start.sh baixando o mesmo do repositório.

```
docker run          \
    -it             \
    -p 1935:1935    \
    -p 8080:8080    \
    rafallis/nginx-rtmp-server
```

Este comando iniciará a stream localmente. 

## Multiplas streams
Caso deseje inicializar várias streams deve-se utilizar o seguinte comando

```
docker run          \
    -it             \
    -p 1935:1935    \
    -p 8080:8080    \
    -e RTMP_STREAM_NAMES=live1, live2, live3 \
    rafallis/nginx-rtmp-server
```
RTMP_STREAM_NAMES receberá o nome das streams 

## Enviando streams para YouTube / Twitch

Caso deseje enviar a stream para alguma plataforma de vídeos como YouTube e Twitch, basta executar o comando abaixo substituindo as respectivas streamkeys

```
docker run          \
    -it             \
    -p 1935:1935    \
    -p 8080:8080    \
    -e RTMP_PUSH_URLS=rtmp://live.youtube.com/<my_name>/<streamkey>, rtmp:live.twitch.tv/app/<streamkey> \
    rafallis/nginx-rtmp-server
```

## Configurando o OBS

Para utilizar o **OBS** como stream app, basta acessar:
```
Configurations > Stream
```
Alterar o parâmetro Stream Type para Custom Streaming Server. No campo URL preencher com

```
rtmp://<server_ip>/live
```

e em Stream Key com a chave de acesso da stream local.

![](https://github.com/PEQUI-MEC/PEQUI-ACADEMY/blob/master/docs/assets/obs_custom_server_config.png)

# Blog

# Wiki

Nossa [Wiki](https://github.com/PEQUI-MEC/VSSS-INF/wiki) pode conter informações relevantes para seu melhor entendimento de como trabalhamos e como você pode contribuir com nosso trabalho.

# Redes Sociais

Nossas atividades e eventos estão sempre em atualização através de nossos canais sociais. Fique por dentro de nossas atividades e se encante com o mundo da robótica.

- [INSTAGRAM](https://www.instagram.com/pequimecanico/)
- [FACEBOOK](https://www.facebook.com/NucleoPMec)
