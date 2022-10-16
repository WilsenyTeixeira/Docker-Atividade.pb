# Docker-Atividade.pb
Este é o repositório da atividade de Docker do programa de bolsas da Compass.Uol. Este projeto está sendo realizado em dupla, Wilseny e João Vitor.

Primeiro iremos criar o banco de dados com o mysql atravez do docker compose. Nele será realizado as seguintes configurações:
1. A imagem será mysql:latest;
2. Caso tem algum erro com o container ele vai reiniciar automaticamente;
3. Nosso host terá acesso ao serviço pela porta 3308, que por sua vez se conectará na porta 3306 do container com mysql;
4. Vamos especificar algumas variáveis de ambiente:
4.1 MYSQL_ROOT_PASSWORD recebe a senha para o usuário "root";
4.2 MYSQL_DATABASE recebe o da database que será criada junto com o container;
4.3 MYSQL_USER recebe o nome de usuário que terá acesso à database acima;
4.4 MYSQL_PASSWORD recebe a senha do usuário que criamos acima;
5. Vamos persistir os dados do container na nossa máquina local.

