# 42_born2beroot

| Comando                               | Descrição                                                                 |
|---------------------------------------|---------------------------------------------------------------------------|
| ss -tuln                              | Lista todas as conexões de rede TCP e UDP em execução no sistema           |
| ls /usr/bin/*session                   | Verifica se não há nenhuma interface gráfica em uso                       |
| sudo ufw status                       | Verifica o status do serviço UFW (firewall)                               |
| sudo ufw status numbered              | Lista as regras numeradas do UFW                                           |
| sudo ufw allow 8080                   | Permite o tráfego na porta 8080 através do UFW                            |
| sudo ufw delete num_rule              | Remove a regra especificada pelo número no UFW                             |
| sudo service ufw status               | Verifica o status do serviço UFW (firewall)                               |
| sudo service ssh status               | Verifica o status do serviço SSH                                          |
| uname -v                              | Exibe informações sobre a versão do sistema operacional                    |
| groups luide-so                       | Verifica os grupos aos quais um utilizador pertence                           |
| sudo adduser name_user                | Cria um novo utilizador no sistema                                           |
| sudo addgroup evaluating              | Cria um novo grupo no sistema                                             |
| sudo groupdel nome_do_grupo           | Remove um grupo do sistema                                                |
| sudo adduser name_user evaluating     | Adiciona um utilizador a um grupo específico                                 |
| sudo adduser name_user sudo           | Adiciona um utilizador ao grupo "sudo" (privilégios de superutilizador)       |
| hostname                              | Exibe ou define o nome do host (nome do computador)                       |
| sudo nano /etc/hostname               | Edita o arquivo de configuração do nome do host                           |
| sudo nano /etc/hosts                  | Edita o arquivo de configuração do sistema de resolução de nomes (DNS)     |
| hostnamectl set-hostname \<novo nome\>  | Altera o nome do hostname                                                  |
| which sudo                            | Exibe o caminho completo para o executável do comando "sudo"               |
| dpkg -s sudo                          | Verifica o status da instalação do pacote "sudo"                          |
| dpkg -s ufw                           | Verifica o status da instalação do pacote "ufw"                           |
| nano /etc/sudoers.d/sudo_config       | Edita as configurações do sudo                                             |
| sudo visudo                           | Edita o arquivo sudoers com segurança                                     |
| sudo nano /etc/pam.d/common-password  | Edita as configurações de senha comuns do PAM (Módulo de Autenticação Pluggable) |
| sudo nano /etc/login.defs             | Edita as configurações de senha                                             |
| ssh newuser@localhost -p 4242         | Conecta-se a "localhost" como "newuser" usando a porta 4242 via SSH        |
| crontab -e                            | Abre o editor para editar as tarefas cron                                 |
| sudo systemctl enable cron            | Habilita o serviço cron para iniciar no boot                              |
| sudo systemctl disable cron           | Desabilita o serviço cron para                                             |
| chage -l <nome_do_utilizador>           | Exibe informações sobre o utilizador                              |
### Comparar a assinatura
- Criar a assinatura
`shasum born2beroot.vdi`
- Colocar a assinatura no test.txt
`diff signature.txt test.txt`
