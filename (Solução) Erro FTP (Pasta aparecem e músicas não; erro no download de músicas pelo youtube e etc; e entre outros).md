# (Solução) Erro FTP (Pasta aparecem e músicas não; erro no download de músicas pelo youtube e etc; e entre outros)

Solução 1: Configure a conexão no arquivo /home/painel/public_html/player/inc/conecta-remoto.php

Solução 2: Verifique o acesso remoto ao mysql da maquina está liberado.

Solução 3: Verifique se não há processos ftp atrapalhando um ao outro.

Solução 4: No servidor shoutcast verifique se o php está instalado e o apache também, logo, edite o arquivo /etc/httpd/conf/httpd.conf:

E procure pela linha Listen 80 e adicione abaixo dela Listen 555, ao final do arquivo adicione: 
```
<VirtualHost *:555>
 DocumentRoot /home/streaming/web/
 <Directory />
 Options FollowSymLinks
 AllowOverride None
 </Directory>
</VirtualHost>
```

e por fim reinicie o apache:
```
service httpd restart

```

Acesse http://servidorshoutcast:555, devera exibir um pagina igual a essa: 
![img](https://i.imgur.com/LtS9e9K.png)
