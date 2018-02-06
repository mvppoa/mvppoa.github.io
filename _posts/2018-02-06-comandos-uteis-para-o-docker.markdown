---
layout: post
title:  "Comandos úteis para o Docker"
date:   2018-02-06 15:11:35 -0200
categories: docker comandos
---

Comecei a trabalhar com o Docker recentemente e, para centralizar o conhecimento
e ter fácil acesso aos comandos, criei uma lista para facilitar o uso. 

Tem alguma sugestão ou truque? Entre em contato comigo que ficarei feliz em atualizar a lista.

# Listar todas imagens Docker

{% highlight docker %}

docker images -a

{% endhighlight docker %}

# Listar todos os containers Docker que estão rodando

{% highlight docker %}

docker ps

{% endhighlight docker %}

# Listar todos os containers Docker

{% highlight docker %}

docker ps -a

{% endhighlight docker %}

# Iniciar um container Docker

{% highlight docker %}

docker start <container name>

{% endhighlight docker %}

# Parar um container Docker

{% highlight docker %}

docker stop <container name>

{% endhighlight docker %}

# Matar todos os containers que estão rodando

{% highlight docker %}

docker kill $(docker ps -q)

{% endhighlight docker %}

# Ver os logs de um container que está rodando

{% highlight docker %}

docker logs <container name>

{% endhighlight docker %}

# Deletar todos os containers que estão parados
Use a opção -f para deletar todos os containers.

{% highlight docker %}

docker rm $(docker ps -a -q)

{% endhighlight docker %}

# Remover uma imagem docker

{% highlight docker %}

docker rmi <image name>

{% endhighlight docker %}

# Deletar todas as imagens docker

{% highlight docker %}

docker rmi $(docker images -q)

{% endhighlight docker %}

# Deletar todas as imagens docker sem tags

{% highlight docker %}

docker rmi $(docker images -q -f dangling=true)

{% endhighlight docker %}

# Deletar todas as imagens

{% highlight docker %}

docker rmi $(docker images -q)

{% endhighlight docker %}

# Deletar todos os volumes pendurados

{% highlight docker %}

docker volume rm -f $(docker volume ls -f dangling=true -q)

{% endhighlight docker %}

# SSH em um container Docker que está rodando
Usado para ter acesso à linha de comando do container (geralmente linux).

{% highlight docker %}

sudo docker exec -it <container name> bash

{% endhighlight docker %}

# Usar o Docker Compose para construir containers
Rodar no diretório do seu arquivo docker-compose.yml.

{% highlight docker %}

docker-compose build

{% endhighlight docker %}

# Usar o Docker para iniciar um grupo de containers
Rodar no diretório do seu arquivo docker-compose.yml.

{% highlight docker %}

docker-compose up -d

{% endhighlight docker %}


Este comando vai dizer ao Docker pegar a versão mais recente do container de um 
repositório e não usar a que está no cache local.

{% highlight docker %}

docker-compose up -d --force-recreate

{% endhighlight docker %}


# Parar containers docker e reconstruir

{% highlight docker %}

docker-compose stop -t 1
docker-compose rm -f
docker-compose pull
docker-compose build
docker-compose up -d

{% endhighlight docker %}

# Seguir os logs de containers Docker com o compose

{% highlight docker %}

docker-compose logs -f

{% endhighlight docker %}

# Salvar um container que está rodando como uma imagem

{% highlight docker %}

docker commit <image name> <name for image>

{% endhighlight docker %}

# Seguir os dados de um container rodando pelo Docker Compose

{% highlight docker %}

docker-compose logs pump <name>

{% endhighlight docker %}
