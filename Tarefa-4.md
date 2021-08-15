# TAREFA 4

Deixei a tarefa 4 como última a ser executada pois estava com receio de adicionar as regras do iptables e acabar perdendo o acesso a máquina virtual, ao checar que o iptables estava instalado
porém o serviço não estava ativo utilizei o comando **_rpm -qa iptables-services_** para verificar se o iptables services estava instalado, então utilizei o comando **_yum isntall iptables-services_** 
para realizar a instalação.

Verifiquei novamente o conteúdo do iptables.sh que eu havia criado para ter certeza que não havia colocado alguma informação errada, para executar o iptables.sh procurei uma alternativa
que eu pudesse reverter o que havia alterado, encontrei sobre o comando _nohup_ e utilizei o seguinte comando

**_nohup /root/iptables.sh && sleep 120 && systemctl stop iptables_**

Caso eu perdesse a conexao com o ssh apos atualizar o iptables o _nohut_ continuaria executando e iria parar o serviço de iptables 2 minutos após a execução dessa linha, abri outro terminal
para acessar a maquina virtual e testar se eu iria conseguir acessar após realizar o comando.

O iptables não teve problema algum e eu não perdi o acesso a máquina virtual, entao usei o comando **_/root/iptables.sh_** para confirmar todas as mudanças e finalizar o desafio.
