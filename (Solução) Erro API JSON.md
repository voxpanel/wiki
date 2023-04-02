# (Solução) Erro API JSON

Alterar o domínio no arquivo api-json.php 

Edite o arquivo trocando o dominio na função

```$api_xml = @simplexml_load_file("http://audiocast.ml/api/".query_string('1')."");```


Para 

```$api_xml = @simplexml_load_file("http://SEU-DOMINIO-AQUI/api/".query_string('1')."");```
