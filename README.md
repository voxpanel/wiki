# BANCO DE SOLUÇÕES

## Recomenda-se instalar o painel em uma vps e o servidor shoutcast em outro.
* Arquivos que enviam dados para Advancehost devem ser alterados de imediato.
```
bash_profile
app-android.php
robots/monitor-capacidade.php
admin/admin-streamings.php
admin/admin-configura-streaming.php 
admin/admin-configura-servidor.php  
admin/funcoes-ajax.php
admin/login-autentica.php
admin/revenda-app-android.php
admin/inc/funcoes.php
web/index.php
```
* Configure a conexão nos arquivos
```
admin/inc/conecta.php
player/inc/conecta-remoto.php 
robots/inc/conecta-remoto.php
cdn/inc/conecta-remoto.php
```
* Dê permissão 777 aos diretórios, isso resolve a maioria dos problemas:
```
/home/painel/public_html/temp 
/home/painel/public_html/cache 
/home/painel/public_html/player/cache 
/home/painel/public_html/app_android/* 
/home/streaming/* 
```


#### Abaixo estão alguns zips que podem completar nos estudos dos painéis de audio e vídeo:

[video-audio-recursos.zip](https://github.com/voxpanel/wiki/files/11133403/video-audio-recursos.zip)
