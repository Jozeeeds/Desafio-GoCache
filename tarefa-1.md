# TAREFA 1

Como o desafio está sendo feito no CentOS comecei instalando o LAMP stack (Linux, Apache, MariaDB, PHP) que contém todos os programas necessários para realizar a tarefa,
após terminar a instalação eu inicializei o Apache e MariaDB utilizando os comandos **_systemctl start httpd mariadb_** , 
chequei se havia inicializado sem nenhum problema utilizando **_systemctl status httpd mariadb_** , 
utilizei o comando **_systemctl enable httpd mariadb_** para que o serviço ficasse ativo quando o servidor fosse reinicializado e por fim usei **_netstat -tlp | grep 'http|mysql'_**

Também foi utilizado o comando **_mysql_secure_installation_** para colocar uma senha no usuário root, que o usuário root pudesse somente conectar via localhost, no geral um comando
para garantir que o banco fique mais seguro.



