# Docker-Atividade.pb
Este é o repositório da atividade de Docker do programa de bolsas da Compass.Uol. Este projeto está sendo realizado em dupla, Wilseny e João Vitor.

## Primeiro vamos instalar o Docker para Windows, realizando os seguintes passos:
1. Configurar o WSL utilizando o PowerShell com permissão de administrador: "wsl --install", ou "wsl --install -d <Distribution Name>" para especificar uma distribuição Linux(Ubuntu vem por padrão).  
2. Acessar o site oficial e realizar o download: https://docs.docker.com/desktop/install/windows-install/  
3. Executar e avançar na instalção, seguindo as configurações padrão. 


## Depois, iremos criar o banco de dados com o Mysql através do Docker Compose. Nele será realizado as seguintes configurações:

1. A imagem será mysql:latest;
2. Caso tenha algum erro com o container ele vai reiniciar automaticamente;
3. Nosso host terá acesso ao serviço pela porta 3308, que por sua vez se conectará na porta 3306 do container com MySQL;
4. Vamos especificar algumas variáveis de ambiente:  
4.1 MYSQL_ROOT_PASSWORD recebe a senha para o usuário "root";  
4.2 MYSQL_DATABASE recebe o da database que será criada junto com o container;  
4.3 MYSQL_USER recebe o nome de usuário que terá acesso à database acima;  
4.4 MYSQL_PASSWORD recebe a senha do usuário que criamos acima;  
5. Vamos persistir os dados do container na nossa máquina local.

## Agora vamos criar no Docker Compose as instruções para nosso container com WordPress com os seguintes objetivos:

1. A imagem dele será wordpress:latest;
2. Ele reiniciará quando der algum erro;
3. Nosso host terá acesso ao serviço pela porta 8080, que por sua vez se conectará na porta 80 do container com WordPress;
4. Vamos especificar algumas variáveis de ambiente:  
4.1 WORDPRESS_DB_HOST recebe o container com um serviço de database, no caso o MySQL;  
4.2 WORDPRESS_DB_USER recebe o nome de usuário do banco de dados;  
4.3 WORDPRESS_DB_PASSWORD recebe a senha do usuário acima;  
4.4 WORDPRESS_DB_NAME recebe o nome da database que vai utlizar;  
5. Vamos persistir os dados da nossa aplicação do WordPress:  
5.1 Guardamos as configs de uploads.  
5.2 Guardamos os arquivos necessários para a construção do site.  
6. Definimos que para subir este container, é necessário primeiro que tudo dê certo com o container do MySQl, pois o WordPress depende dele.

## Para finalizar, vamos rodar a aplicação utilizando o Docker-Compose  

1. Utilizando o PowerShell, vamos entrar no diretório do nosso arquivo .yml com o comando: cd <Diretório>.  
2. Inserir o comando "docker-compose up".  
2. Pronto, nossa aplicação está rodando e pronta para ser utilizada!
  
## Referências
1. WSL: https://learn.microsoft.com/en-us/windows/wsl/install  
2. Docker for Windows: https://docs.docker.com/desktop/install/windows-install/
