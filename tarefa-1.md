# TAREFA 1

Como o desafio está sendo feito no CentOS comecei instalando o LAMP stack (Linux, Apache, MariaDB, PHP) que contém todos os programas necessários para realizar a tarefa,
após terminar a instalação eu inicializei o Apache e MariaDB utilizando os comandos ****systemctl start httpd mariadb*** , chequei se havia inicializado sem nenhum problema utilizando ***systemctl status httpd mariadb*** , utilizei o comando ***systemctl enable httpd mariadb*** para que o serviço ficasse ativo quando o servidor fosse reinicializado e por fim usei ***netstat -tlp | grep 'http|mysql'*** para verificar se as portas e a conexão do apache e do BD estivessem ok.

Também foi utilizado o comando ***mysql_secure_installation*** para colocar uma senha no usuário root e que pudesse ser conectado somente via localhost, Precauções para garantir que o banco fique mais seguro.

## instalação do wordpress

Antes de comecar a instalação era necessário ter um banco de dados para o wordpress, entao criei a base utilizando o comando ***mysql -u root -p***,
dentro do MariaDB os seguintes comandos foram utilizados:

- CREATE DATABASE wordpress  
- GRANT ALL ON wordpress.* TO jose@localhost IDENTIFIED BY "senha";  
- FLUSH PRIVILEGES;  

Com o BD finalizado eu poderia iniciar a instalação do wordpress, para isso utilizei _wget_

**wget para conseguir baixar o wordpress**  
>yum install wget  

**baixar o wordpress compactado**
>wget http://wordpress.org/latest.tar.gz

**descompactar o wordpress**
>tar xfz latest.tar.gz

**copiar os arquivos para a pasta do meu site**               
>cp -rf wordpress/* /var/www/html/ 

**verificar se os arquivos haviam sido copiados corretamente**       
>ls /var/www/html/ 

                         

Após instalar fui verificar no navegador se estava tudo correto e não aparecia nada, verifiquei o elemento da página e estava vazio como se o wordpress não havia sido instalado, entao fui até a pagina do PHP verificar os logs e constava _parse error syntax_, após pesquisar descobri que era necessário a versao mais recente do PHP pois a instalada na VM era a 5.4, entao foi necessário remover o PHP com o comando _yum remove "php*" -y_, fazer a atualização do remi repository com ***yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm*** e baixei a nova versão do php utilizando ***yum --enablerepo=remi-php74 install php php-pdo php-fpm php-gd php-mbstring php-mysql php-curl php-mcrypt php-json -y***

Com esses contratempos no passado acessei o wordpress pelo navegador e editei o arquivo ***wp-config.php*** para inserir as configurações necessárias e o processo de configuração seguiu sem mais problemas 

