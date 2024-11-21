# Links para API da nossa aplicação e descrição
CAMINHOS PRESENTES NO JETTY

**Notas**:

+ ```Estamos a supor que na versão "segura":```
    +  o ```NGINX``` esta a correr como ```rerverse proxy``` e tem ```Https``` devidamente configurado

    + Pedidos direcionados para ```https://localhost/api``` são passados para ```https://localhost:8080/```

+ ```Estamos a supor que na versão não segura```

    + Não temos ```reverse proxy``` nem ```Https``` configurado pelo  ```NGINX```





## Caminhos relacionados com filmes
```(GET)```

+ https://localhost/api/movie/all -> retorna todos os filmes presentes na db no momento

+ https://localhost/api/movie/search/input_qualquer -> retorno todos os filmes que tenha presenta a substring  (exemplo:+ https://localhost/api/movie/search/the ,retorna todos os filmes que tem "the" no titulo)

```(POST)```

**(versão não segura)**

+ http://localhost:8080/movie/remove -> remove o filme com determinado id (para funcionar tens de passar o json com o seguinte formato: { "movieid" : id_filme_queremos_remover}

**(versão "segura")**

+ https://localhost/api/movie/remove?apiKey=1234567890abcdef -> igual a de cima mas segura

## Caminhos relacionados com upload de movies

```(GET)```
+ https://localhost/api/upload -> (teste de conexão)

```(POST)```

**(versão não segura)**
+ http://localhost:8080/upload/movie -> adiciona o filme (para funcionar tens de passar um form-data com os seguintes parametros : (ficheiro_mp4 , nome_filme,ano e duração) . form-data <=> Multipartformdata . 


**(versão "segura")**
+ https://localhost/api/upload/movie?apiKey=1234567890abcdef -> igual ao de cima mas usado na aplicação segura

## Caminhos relacionados com utilizadores / admins
```(GET)```

**(versão não segura)**

+ http://localhost:8080/connect/all/usr -> retorna todos os utilizadores

+ http://localhost:8080/connect/all/admin -> retorna todos os administradores

**(versão "segura")**

https://localhost/api/connect/all/usr?apiKey=1234567890abcdef

https://localhost/api/connect/all/admin?apiKey=1234567890abcdef

```(POST)``` (todos retornam objeto RespUser , classe presente no jetty)

+ https://localhost/api/connect/login/usr -> verifica o login de  um utilizador (para funcionar tens que enviar um json com seguinte formato {"login" : "Rui","password": "batatas"} (este e as credencias de um utilizador que existe na bd) . Retorna um RespUser que indica sucesso ou insucesso.

+ https://localhost/api/connect/login/admin -> igual ao de cima mas para admins

+ https://localhost/api/connect/signup/usr -> adiciona um utilizador a bd (para funcionar tens que enviar um json com o seguinte aspeto {"login" : "Rui","password": "batatas"} , neste caso devolve um RespUser que indica que já existe um utilizador com esse login).


+ https://localhost/api/connect/signup/admin -> igual ao de cima mas para admins


**(versão não segura)**

+ http://localhost:8080/connect/remove/usr  -> remove um utilizador da bd ( para funcionar tens que enviar um json com o seguinte aspeto   { "login" : "nome_utilizador"} , já agora o nome de utilizador é unico .

+ http://localhost:8080/connect/remove/admin -> igual ao de cima mas para admins

**(versão "segura")**

+ https://localhost/api/connect/remove/usr?apiKey=1234567890abcdef

+ https://localhost/api/connect/remove/admin?apiKey=1234567890abcdef


## Caminhos relacionados com ping (com possivel exemplo de ataque)

```(GET)```

+ https://localhost/api/ping/safe/www.google.com

+ https://localhost/api/ping/unsafe/www.google.com&&dir%20~