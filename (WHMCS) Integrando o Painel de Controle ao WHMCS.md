# (WHMCS) Integrando o Painel de Controle ao WHMCS
### Recursos:
Criar: cria a conta de rádio

Suspender: Bloqueia a rádio e deixa ela offline

Reativar: Desbloqueia a rádio e deixa ela online

Finalizar: Exclui totalmente a rádio

Alterar Pacote: Altera o pacote. Ex: de Plano Bronze para Plano Prata

Alterar Senha: Renova a senha da rádio no banco de dados

Desbloquear IP: Limpa os erros de login da porta e desbloqueia o IP de seu cliente.

Sincronizar: Atualiza todos os dados de uma porta/rádio no WHMCS

Ligar: Liga o servidor da rádio

Desligar: Desliga o servidor

Reiniciar: Reinicia o servidor + Auto Dj(caso este estiver ligado)

Reset Config: Reseta as configurações do streaming para os padrões

Recarregar Auto Dj: Recarrega as músicas e atualizações do Auto Dj

Ativar Site: Libera o site para seu cliente

Desativar Site: Bloqueia o site

Update Module: Verifica as versões disponíveis desse Módulo WHMCS


#### Primeiro envie o arquivo para sua hospedagem

1° Baixe o módulo através do link:

[stmaac](stmaac)

2° Envie a pasta chamada: "stmaac" para o diretório:

/public_html/seu-whmcs/modules/servers/
 


#### Instalação e Configuração do Módulo no admin do WHMCS


1 - Acesse seu WHMCS e clique no menu Opções > Produtos/Serviços > Servidores como na imagem abaixo:
 

2 - Na próxima tela você terá a opção de adicionar um novo servidor, clique nela.

3 - No formulário de cadastro de servidores, preencha os seguintes campos:

Nome: somente para identificação deste servidor

Servidor: http://ipstm.net

Endereço IP: Sua chave API disponível no painel de revenda

4 - Preencha os demais campos com os dados desejados como custo do servidor, limite de streamings etc… 

5 - No menu suspenso, selecione: StmAAC, preencha Usuário e Senha com os dados de acesso ao Paineld e Revenda e SALVE AS ALTERAÇÕES

#### Configurando o Produto/Serviço

1 - Agora adicione os produtos(planos) de streaming e na aba Module Settings selecione a opção Stmaac e preencha com os dados do plano(ouvintes, espaço autodj e bitrate).

2 - Na aba Custom Fields/Campos Adicionais adicione um novo campo com o nome exato de Porta (com primeira letra maiúscula) e salve.

Pronto! Seu WHCMS está instegrado ao nosso painel de controle de streaming.

Obs: stmaac_php_70.zip é para php 7 em diante, o outro arquivo é para versões de php anteriores.


Nota: O campo adicional que você criou será usado para identificar o streaming do cliente. Quando você ativar o streaming em seu WHMCS, o nosso sistema irá informar ao WHMCS a porta criada para o streaming e ela ficará gravada no produto do cliente assim como o IP do servidor de streaming e FTP.
