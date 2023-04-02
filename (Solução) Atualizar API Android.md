Rode os comandos para atualizar e configurar os requisitos da api 26.
```
cd /home/painel/public_html/
wget https://github.com/voxpanel/wiki/raw/main/novo-app-painel.zip
unzip -o novo-app-painel.zip
replace '250' '300' -- /home/painel/public_html/app-android.php
replace '250' '300' -- /home/painel/public_html/admin/revenda-app-android.php
chmod 0777 /home/painel/public_html/app_android/ -Rfv
replace '235x235' '300x300' -- /home/painel/public_html/inc/lang-*
replace '235x235' '300x300' -- /home/painel/public_html/admin/inc/lang-*
cd /opt/
./android-sdk-linux/tools/android update sdk --no-ui
mkdir ~/glibc_install; cd ~/glibc_install
wget http://ftp.gnu.org/gnu/glibc/glibc-2.14.tar.gz
tar zxvf glibc-2.14.tar.gz
cd glibc-2.14

mkdir build

cd build

../configure --prefix=/opt/glibc-2.14

make -j4

sudo make install

export LD_LIBRARY_PATH=/opt/glibc-2.14/lib

cp /opt/glibc-2.14/lib/libc.so.6 /opt/android-sdk-linux/build-tools/28.0.3/lib64/
```

Você pode excluir os diretórios source1, source2 e source3 em /home/painel/public_html/app_android, pois eles são inúteis.

Observe que o comando `./android-sdk-linux/tools/android update sdk --no-ui` é repetido várias vezes, isso é para verificar se há alguma atualização de SDK, para manter o seu mais recente.
O comando cp /opt/glibc-2.14/lib/libc.so.6 /opt/android-sdk-linux/build-tools/28.0.3/lib64/ copia o arquivo libc.so para o direiorio do SDK, caso dê erro verifique o diretório mais recente em /opt/android-sdk-linux/build-tools/ e altere o comando para /opt/glibc-2.14/lib/libc.so.6 /opt/android-sdk-linux/build-tools/diretorio-mais-recente/lib64/, caso não tenha identificado o diretório, rode o comando ls /opt/glibc-2.14/lib/libc.so.6 /opt/android-sdk-linux/build-tools/, exibir todas os diretórios, pego o mais recente e substitua as informações no comando. Ex: a pasta mais recente de todas exibidas é a 28.0.6, então o comando que irei rodar cp /opt/glibc-2.14/lib/libc.so.6 /opt/android-sdk-linux/build-tools/28.0.6/lib64/.


