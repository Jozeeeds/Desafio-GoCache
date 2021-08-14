# TAREFA 2

Pesquisei sobre o funcionamento do Let's Encrypt e comecei baixando os arquivos necessários para adquirir o certificado SSL, o primeiro comando utilizado foi **_yum install python-certbot-apache_**,
pois dessa forma o processo de adquisicao do certificado é automatizado e mais fácil, no final utilizei o comando **_grep DocumentRoot /etc/httpd/conf.d/ssl.conf**_ para localizar onde os arquivos do wordpress iriam ficar.

## Adquirindo o certificado

Utilizei o comando **_certbot certonly --webroot -w /var/www/html/ --renew-by-default --email jose.vendr@gmail.com --text --agree-tos  -d jperlin.gocdn.com.br_**,
o meu email para aceitar os termos de servicos e o _jperlin.gocdn.com.br_ para mostrar qual endereco da web estava recebendo o certificado, após esse processo era necessário 
verificar se os certificados e chaves estava no local correto, utilizei o comando **_ls /etc/letsencrypt/live/jperlin.gocdn.com.br/_** para verificar e o resultado foi:

- SSLCertificateFile /etc/letsencrypt/live/jperlin.gocdn.com.br/cert.pem
- SSLCertificateKeyFile /etc/letsencrypt/live/jperlin.gocdn.com.br/privkey.pem
- SSLCertificateChainFile /etc/letsencrypt/live/jperlin.gocdn.com.br/fullchain.pem

todas as chaves estavam corretas e funcionando entao o que faltava era criar uma forma de atualizar essas chaves automaticamente, utilizei o comando **_crontab -e**_ para agendar um
comando que renovasse semanalmente, o comando usado foi:

**0 0 * * 0 /usr/bin/certbot renew >> /var/log/certbot-renew-lets.log**

seria as **0** minutos, **0** horas (meia noite), * todos os dias do mes, * todos os meses do ano, **0** são domingos, entao o certbot irá renovar **todos os domingos a meia noite em ponto**

A próxima etapa foi trocar os certificados padrão do apache pelos novos certificados gerados, um processo simples que era somente abrir e comentar as linhas com os certificados antigos, copiar
e substituir com os novos certificados, era só uma questao de verificar se a syntaxe estava correta utilizando **_apachectl -t_**, reiniciar o apache utilizando **_systemctl restart httpd_** e 
após esses processos o site já estava redirecionando pro HTTPS
