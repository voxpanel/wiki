# Configurando CDN

Crie um subdominio redirecionando para a pasta /home/painel/public_html/cdn

Configure a conexão no arquivo /home/painel/public_html/cdn/inc/conecta-remoto.php

Agora edite o arquivo /etc/httpd/conf/httpd.conf adicionando ao final:
```
<Directory "/home/painel/public_html/cdn/">
 Options Indexes FollowSymLinks
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>
<VirtualHost *:80>
 ServerName cdn.audiobrazil.ml
 DocumentRoot /home/painel/public_html/cdn/
 ServerAlias cdn.audiobrazil.ml
 ErrorLog /home/painel/public_html/cdn/error.log
 CustomLog /home/painel/public_html/cdn/requests.log combined
</VirtualHost>
```

Verifique se alinha NameVirtualHost *:80 está comentada, se tiver, descomente.

Obs: em audiobrazil.ml coloquem o endereço correto.

Execute o comando no terminal: `service httpd restart`

É importante que crie as entradas "A" no zona dns, veja um exemplo na imagem abaixo.
![img](https://i.imgur.com/HjO9dcg.jpeg)
Acessa administrativo do painel e no campo de configurações do CDN coloque cdn.painel.com e salve, caso queira ative. Pronto!
