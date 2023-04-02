# (Solução) Erro Player Barra

Crie um subdominio redirecionando para a pasta /home/painel/public_html/player

Tem que ter PHP 5.6.30 ou inferior pois há uma função que não esta disponível mais no PHP novo.

Configure a conexão no arquivo /home/painel/public_html/player/inc/conecta-remoto.php

Agora edite o arquivo /etc/httpd/conf/httpd.conf e verifique se existe ao final, se não adicione, caso esteja errado edite:
```
<Directory "/home/painel/public_html/player/">
 Options Indexes FollowSymLinks
 AllowOverride All
 Order allow,deny
 Allow from all
</Directory>
<VirtualHost *:80>
 ServerName [audiobrazil.ml](http://audiobrazil.ml/)
 DocumentRoot /home/painel/public_html/
 ServerAlias [audiobrazil.ml](http://audiobrazil.ml/)
 ErrorLog /home/painel/public_html/error.log
 CustomLog /home/painel/public_html/requests.log combined
</VirtualHost>
<VirtualHost *:80>
 ServerName [player.audiobrazil.ml](http://player.audiobrazil.ml/)
 DocumentRoot /home/painel/public_html/player/
 ServerAlias [player.audiobrazil.ml](http://player.audiobrazil.ml/)
 ErrorLog /home/painel/public_html/player/error.log
 CustomLog /home/painel/public_html/player/requests.log combined
</VirtualHost>
```
Verifique se alinha NameVirtualHost *:80 está comentada, se tiver, descomente.

Obs: em audiobrazil.ml coloquem o endereço correto.
Execute o comando no terminal:
service httpd restart
É importante que crie as entradas "A" no zona dns, veja um exemplo na imagem abaixo.
![Imgur](https://i.imgur.com/RxkEVZR.jpg)


Pronto!
