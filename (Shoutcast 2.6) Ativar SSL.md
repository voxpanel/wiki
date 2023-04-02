# (Shoutcast 2.6) Ativar SSL.md
## Painel + Shoutcast no mesmo servidor
Rode
```
wget https://dl.eff.org/certbot-auto
chmod a+x certbot-auto
mv certbot-auto /etc/certbot-auto
sudo /etc/certbot-auto --apache --agree-tos --email msaulohenrique@gmail.com -d srv01.audiobrazil.ml -d audiobrazil.ml -d player.audiobrazil.ml -d cdn.audiobrazil.ml -d www.audiobrazil.ml

```
Edite os arquivos:
* funcoes-ajax.php
* movel/funcoes-ajax.php
* admin/funcoes-ajax.php
* admin/funcoes-ajax-revenda.php

Procure pela linha:
```$config_streaming .= ";LOGS\n";```

Adicione acima:
```
$config_streaming .= "sslcertificatefile=/etc/letsencrypt/live/".$dados_config["dominio_padrao"]."/fullchain.pem\n";
$config_streaming .= "sslcertificatekeyfile=/etc/letsencrypt/live/".$dados_config["dominio_padrao"]."/privkey.pem\n";
$config_streaming .= "alternateports=443\n";
```

Obrigatório configurar o crontab em todos (crontab -e)
```0 0 13 3 * /etc/certbot-auto renew --no-self-upgrade```

Baixe o SHOUTcast Server v2.6.0.742 (x64) [sc_serv.zip](https://github.com/voxpanel/wiki/files/11133383/sc_serv.zip)
Depois de envie para /home/streaming rode:
```
cd /home/streaming
chmod a+x sc_serv
```

## Painel e Shoutcast separados servidor
### VPS Painel
Rode
```
wget https://dl.eff.org/certbot-auto
chmod a+x certbot-auto
mv certbot-auto /etc/certbot-auto
sudo /etc/certbot-auto --apache --agree-tos --email meuemail@servidor.com -d audiobrazil.ml -d player.audiobrazil.ml -d cdn.audiobrazil.ml -d www.audiobrazil.ml
```
Edite os arquivos no VPS do painel:
* funcoes-ajax.php
* movel/funcoes-ajax.php
* admin/funcoes-ajax.php
* admin/funcoes-ajax-revenda.php

Procure pela linha:
```$config_streaming .= ";LOGS\n";```

Adicione acima:
```
$config_streaming .= "sslcertificatefile=/etc/letsencrypt/live/".$dados_config["dominio_padrao"]."/fullchain.pem\n";
$config_streaming .= "sslcertificatekeyfile=/etc/letsencrypt/live/".$dados_config["dominio_padrao"]."/privkey.pem\n";
$config_streaming .= "alternateports=443\n";
```

### VPS Shoutcast
Rode
```
wget https://dl.eff.org/certbot-auto
chmod a+x certbot-auto
mv certbot-auto /etc/certbot-auto
sudo /etc/certbot-auto --apache --agree-tos --email meuemail@servidor.com -d audiobrazil.ml -d player.audiobrazil.ml -d cdn.audiobrazil.ml -d www.audiobrazil.ml
```

Obrigatório configurar o crontab em todos (crontab -e)
```0 0 13 3 * /etc/certbot-auto renew --no-self-upgrade```

Baixe o SHOUTcast Server v2.6.0.742 (x64) [sc_serv.zip](https://github.com/voxpanel/wiki/files/11133383/sc_serv.zip)
Depois de envie para /home/streaming rode:
```
cd /home/streaming
chmod a+x sc_serv
```
