# NAC DEVOPS

# Rodando a aplicação

Para rodar a aplicação é necessário primeiro efetuar um pull das imagens necessárias:

- docker pull php:7.2-apache  
- docker pull mysql:5.7

Após rodar é necessário fazer o build das imagens.

- docker build . -t backend-mysql:v1  
- docker build . -t frontend-php:v1


Após o build precisamos nos conectar no banco mysql:

- docker run -d --rm --name backend -e MYSQL_DATABASE=demo -e MYSQL_ALLOW_EMPTY_PASSWORD=yes backend-mysql

Com o banco conectado, precisamos conectar o frontend com o backend. Para isso utilizamos o comando --link:

- docker run -d --rm --name frontend -p 80:80 --link backend frontend-php
