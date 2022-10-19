# Docker-Atividade.pb
Este é o repositório da atividade de Docker do programa de bolsas da Compass.Uol. Este projeto está sendo realizado em dupla, Wilseny e João Vitor.

## Pré-requisitos
Primeiro vamos instalar o Docker para Windows, realizando os seguintes passos:
1. Configurar o WSL utilizando o PowerShell com permissão de administrador: "wsl --install", ou "wsl --install -d <Distribution Name>" para especificar uma distribuição Linux(Ubuntu vem por padrão).  
2. Acessar o site oficial e realizar o download: https://docs.docker.com/desktop/install/windows-install/  
3. Executar e avançar na instalção, seguindo as configurações padrão. 

## Criando nosso projeto
Vamos criar nosso diretório e arquivos necessários:
```bash
# Crie uma pasta para seu projeto
$ mkdir exemplo_docker_WP_MySQL
```
```bash
# Acesse a pasta do projeto no terminal/cmd
$ cd exemplo_docker_WP_MySQL
```
```bash
# Crie um arquivo docker compose
$ touch docker-compose.yml
```

```bash
# Crie um arquivo docker compose
$ touch docker-compose.yml
```
```bash
# Crie um arquivo .env
$ touch .env
```
```bash
# Agora vamos editar o arquivo docker-compose.yml
# "code . " abrirá a pasta atual em seu workspace
# Mas você pode usar qualquer editor de sua preferência
$ code .
```
Depois, iremos criar o banco de dados com o Mysql através do Docker Compose. Nele será realizado as seguintes configurações:
1. Versão do compose
2. A imagem será mysql:8.0.31;
3. Caso tenha algum erro com o container ele vai reiniciar automaticamente;
4. Dar nome ao container;
5. Nosso host terá acesso ao serviço pela porta 3308, que por sua vez se conectará na porta 3306 do container com MySQL;
6. Vamos especificar algumas variáveis de ambiente:
6.1 MYSQL_ROOT_PASSWORD recebe a senha para o usuário "root";
6.2 MYSQL_DATABASE recebe o da database que será criada junto com o container;
6.3 MYSQL_USER recebe o nome de usuário que terá acesso à database acima;  
6.4 MYSQL_PASSWORD recebe a senha do usuário que criamos acima;  
7. Vamos persistir os dados do container na nossa máquina local.

>**Note**
>Caso não deseje usar o aqruivo .env, basta passar os valores de cada variável de ambiente diretamente no arquivo docker-compose.yml
>>**Exemplo**
>WORDPRESS_DB_NAME: database_nome_desejado

Agora vamos criar no Docker Compose as instruções para nosso container com WordPress com os seguintes objetivos:

1. A imagem dele será wordpress:6.0.2;
2. Ele reiniciará quando der algum erro;
3. Dar nome ao container
4. Nosso host terá acesso ao serviço pela porta 8080, que por sua vez se conectará na porta 80 do container com WordPress;
5. Vamos especificar algumas variáveis de ambiente:  
5.1 WORDPRESS_DB_HOST recebe o container com um serviço de database, no caso o MySQL;  
5.2 WORDPRESS_DB_USER recebe o nome de usuário do banco de dados;  
5.3 WORDPRESS_DB_PASSWORD recebe a senha do usuário acima;  
5.4 WORDPRESS_DB_NAME recebe o nome da database que vai utlizar;  
6. Vamos persistir os dados da nossa aplicação do WordPress:
7. Definimos que para subir este container, é necessário primeiro que tudo dê certo com o container do MySQl, pois o WordPress depende dele.


Agora em nosso arquivo .env vamos passar os valores para as varáveis:

MYSQL_ROOT_PASSWORD=root_senha_desejada
...
WORDPRESS_DB_NAME=db_usado_pelo_wordpress

##Subindo nossa Aplicação
>**🔴IMPORTANT❗🔴**
>Garanta que você esteja dentro do diretório do projeto.
```bash

# Suba os containers com docker compose
$ docker-compose up -d
```
Pronto, nossa aplicação está rodando e pronta para ser utilizada!
O servidor inciará na porta:8080 - acesse `http://localhost:8080`

## Para finalizar, vamos entender a vantagem  de usar o Docker-Compose  

O Docker-Compose possui a vantagem de utilizar mais de um container de maneira organizada e antecipada, definindo as configurações, variáveis e a ordem em que os containers serão executados.
  
## Referências
1. WSL: https://learn.microsoft.com/en-us/windows/wsl/install  
2. Docker for Windows: https://docs.docker.com/desktop/install/windows-install/
3. Docker do 0 à Maestria: Contêineres Desmistificados + EXTRAS https://compassuol.udemy.com/course/docker-do-zero-a-maestria-conteinerizacao-desmistificada/learn/lecture/15140018#overview  
4. Aprenda DOCKER e contêineres de maneira simples e rápida https://compassuol.udemy.com/course/aprenda-docker-simples-e-rapido/learn/lecture/27079890#overview

