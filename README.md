# Docker-Atividade.pb
Este é o repositório da atividade de Docker do programa de bolsas da Compass.Uol. Este projeto está sendo realizado em dupla, Wilseny e João Vitor.

Primeiro iremos criar o banco de dados com o mysql através do docker compose. Nele será realizado as seguintes configurações:

1. A imagem será mysql:latest;
2. Caso tem algum erro com o container ele vai reiniciar automaticamente;
3. Nosso host terá acesso ao serviço pela porta 3308, que por sua vez se conectará na porta 3306 do container com MySQL;
4. Vamos especificar algumas variáveis de ambiente:  
4.1 MYSQL_ROOT_PASSWORD recebe a senha para o usuário "root";  
4.2 MYSQL_DATABASE recebe o da database que será criada junto com o container;  
4.3 MYSQL_USER recebe o nome de usuário que terá acesso à database acima;  
4.4 MYSQL_PASSWORD recebe a senha do usuário que criamos acima;  
5. Vamos persistir os dados do container na nossa máquina local.

Agora vamos criar no docker compose as instruções para nosso container com WordPress com os seguintes objetivos:

1. A imagem dele será wordpress:latest;
2. Ele reiniciar quando der algum erro;
3. Nosso host terá acesso ao serviço pela porta 8080, que por sua vez se conectará na porta 80 do container com WordPress;
4. Vamos especificar algumas variáveis de ambiente:  
4.1 WORDPRESS_DB_HOST recebe o container um serviço de database, no caso o MySQL;  
4.2 WORDPRESS_DB_USER recebe o nome de usuário do banco de dados;  
4.3 WORDPRESS_DB_PASSWORD recebe a senha do usuário acima;  
4.4 WORDPRESS_DB_NAME recebe o nome da database que vai utlizar;  
5. Vamos persistir os dados da nossa aplicação do WordPress:  
5.1 guardamos as configs de uploads  
5.2 guardamos os arquivos necessários para a construção do site.  
6. Definimos que para subir este container, é necessário primeiro que tudo dê certo com o container do MySQl, pois o WordPress depende dele.
