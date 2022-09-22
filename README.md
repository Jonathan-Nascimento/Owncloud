# OwnCloud

# Instalação do OwnCloud


1º - Crie um diretorio "Owncloud" e entre no mesmo.

~# mkdir Owncloud

~# cd Owncloud

2º - Crie um arquivo ".yaml" com as informações abaixo.

~# vim docker-compose.yaml


    version: '3'
    services:
        mysql:
          image: mysql:5.5
          container_name: mysql
          restart: always
          volumes:
            - data_db:/var/lib/mysql
            - "/etc/localtime:/etc/localtime:ro"
          environment:
            MYSQL_ROOT_PASSWORD: Passwd
        owncloud:
           image: owncloud
           container_name: owncloud
           restart: always
           ports:
             - 80:80
           volumes:
             - config_file:/var/www/html/config
             - data_file:/var/www/html/data
             - "/etc/localtime:/etc/localtime:ro"

    volumes:
       data_db:
       config_file:
       data_file:


3º - Execute o arquivo ".yaml" para iniciar o contaienr Portainer.


~# docker-compose -f docker-compose.yaml up -d


4º - Acesse o navegador e digite a url abaixo.

http://IP-HOST:80


5º - Na tela de login crie um senha para user

Digite o login e senha do novo usuário

Selecione o banco de dados clicando em "Armaxenmaneto & banco de dados" e selecione "MySQL/MariaDB"

Preencha os dados do abanco de dados levando em conta o arquivo ".yaml".

- Usuário de banco de dados: root
- Senha de banco de dados: Passwd
- Nome do banco de dados: owncloud 
- Host do banco de dados: mysql "Nome do service do banco de dados mysql utilizado no seu arquivo .yaml"

6º - Clique em "Comcluir configuração" para finalizar a instlação e acessar a aplicação.
