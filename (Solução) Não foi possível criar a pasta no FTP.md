# (Solução) Não foi possível criar a pasta no FTP

Primeiro verifique se o IP da máquina do shoutcast está bloqueado, na máquina do VPS:
Só rodar esse comando na máquina do painel, substitua 177.6.108.158 pelo ip da maquina do shoutcast:
```iptables -A INPUT -i eth0 -s 177.6.108.158 -p tcp --destination-port 3306 -j ACCEPT```

Agora siga o seguinte tutorial na máquina do painel: [https://receitasdecodigo.com.br/banco-de-dados/liberar-acesso-remoto-para-servidores-mysql]
Agora na máquina do shoutcast, rode as linhas: 
```
chkconfig pure-ftpd on
chkconfig httpd on
/etc/init.d/httpd restart
/etc/init.d/pure-ftpd restart
/etc/init.d/rsyslog restart
echo 'streaming:cia@radio#cdr' | chpasswd
sed -i '/MinUID/d' /etc/pure-ftpd/pure-ftpd.conf
sed -i '/MYSQLDefaultUID/d' /etc/pure-ftpd/pureftpd-mysql.conf
sed -i '/MYSQLDefaultGID/d' /etc/pure-ftpd/pureftpd-mysql.conf
user_stm_id=`id -u streaming`
echo "MinUID $user_stm_id" >> /etc/pure-ftpd/pure-ftpd.conf
echo "MYSQLDefaultUID $user_stm_id" >> /etc/pure-ftpd/pureftpd-mysql.conf
echo "MYSQLDefaultGID $user_stm_id" >> /etc/pure-ftpd/pureftpd-mysql.conf
/etc/init.d/pure-ftpd restart
```
