A tarefa 5 e 6 foram as mais complexas do desafio, tentei usar soluções disponiveis em bibliotecas do linux porem nenhuma delas funcionava com os thresholds necessários,
procurei alguns codigos no github e encontrei um que faz monitoramento de todos os itens importantes, mas ao invés de criar um log ele enviava um e-mail para alguém, como é necessário
criar logs eu fiz algumas alterações simples no código para que ele gerasse logs ao invés de enviar um email, as alterações podem ser vistas aqui: https://github.com/Jozeeeds/watchsys/commits?author=Jozeeeds

Com as alterações realizadas foi utilizado *__yum install git__* para instalar o GIT e realizar clone do repositório modificado, foi alteradas as configurações no arquivo _server.list_ para 
incluir os IPs com as portas específicas no monitoramento.

O tempo de checagem dos servidores é a cada 5 minutos e os outros itens podem ter o tempo de monitoramento trocado dependendo da necessidade 
