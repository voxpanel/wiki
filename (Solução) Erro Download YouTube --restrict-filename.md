# (Solução) Erro Download YouTube --restrict-filename

Edite o arquivo /home/streaming/web/youtube.php no servidor shoutcast, procure pela linha 53:
```
liveExecuteCommand("/usr/local/bin/youtube-dl --no-cache-dir --output '/home/streaming/".$_GET["porta"]."/".$_GET["pasta"]."/".$arquivo.".mp4' --ffmpeg-location /usr/local/bin/ffmpeg -x --audio-format mp3 --audio-quality 128K https://www.youtube.com/watch?v=".$_GET["video"]."");
```

Altere para:
```
liveExecuteCommand("LC_ALL=en_US.UTF-8 /usr/local/bin/youtube-dl --no-cache-dir --output '/home/streaming/".$_GET["porta"]."/".$_GET["pasta"]."/".$arquivo.".mp4' --ffmpeg-location /usr/local/bin/ffmpeg -x --audio-format mp3 --audio-quality 128K https://www.youtube.com/watch?v=".$_GET["video"]."");
```
Veja que só foi adicionado `LC_ALL=en_US.UTF-8`. Caso apareça outro problema, que está impedindo de baixar a música, verifique se as pastas da porta e de música estão com permissão 777.
