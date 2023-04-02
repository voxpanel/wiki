# (WHMCS) Modelo de E-mail para Envio de Dados do Streaming automaticamente ao cliente

No WHMCS, você pode cadastrar um novo template de e-mai:

1) Siga até Opções --> Modelos de E-mails.

2) Crie um novo modelo: 

Type: Produtos

Nome Único: Streaming VoxStream 

[Opcional - Esse nome será apenas para que voce poder identificar o e-mail e o título não será mostrado ao cliente]

3) Dê um título para o e-mail que será enviado


COPIE O EXEMPLO ABAIXO E COLE NO CAMPO ONDE VOCÊ DEVERÁ INSERIR O CONTEÚDO DO E-MAIL:

```
Olá {$client_name},

Informações da conta

Plano: {$service_product_name} http://{$service_dedicated_ip}:{$service_username}

Valor do primeiro pagamento: {$service_first_payment_amount}
Recorrente: {$service_recurring_amount}
Ciclo de pagamento: {$service_billing_cycle}
Próximo vencimento: {$service_next_due_date}


Painel de controle: http://ipstm.net

Usuário: {$service_username}

Senha: {$service_password}

 

FTP (upload de músicas)

IP: {$service_dedicated_ip}

Usuário: {$service_username}

Senha: {$service_password}


 
{$signature}
```

3) Após cadastrar o novo modelo, clique para editar o produto/serviço e selecione o novo e-mail como sendo o E-mail de boas vindas do serviço.
