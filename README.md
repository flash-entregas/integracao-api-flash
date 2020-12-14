# Integração API Flash Entregas
Integração para empresas com o sistema FLASH
Função do Franqueado, pré integração:
O franqueado precisa realizar essas etapas no sistema FLASH.
1. Cadastro dos BAIRROS
2. Cálculo das TAXAS
3. Cadastro das EMPRESAS(Ativação)
4. Cálculo dos VALORES DE BAIRROS
5. Cadastro dos ENTREGADORES (Ativação)

Para que os testes de integração sejam realizados, é necessário ter todos os cadastros realizados no Flash.
Os desenvolvedores receberão a documentação das rotas do webservice da Flash, para teste em homologação.
Juntamente, receberão os dados necessários para realização das chamadas à API:
- Autenticação à API (usuário e senha);
- Código da empresa;

## Métodos
Requisições para a API devem seguir os padrões:

| Método |	Descrição|
|:------:|:---------:|
|GET	   | Retorna informações de um ou mais registros|
|POST	 | Utilizado para criar um novo registro|
|PUT	   | Atualiza dados de um registro ou altera sua situação|

## Respostas
Código	Descrição
200	Requisição executada com sucesso (success).
400	Erros de validação ou os campos informados não existem no sistema.
401	Dados de acesso inválidos.
404	Registro pesquisado não encontrado (Not found).
405	Método não implementado.

## ROTAS


### Lista de valores de entregas
- Lista os valores de entregas para os bairros cadastrados para o estabelecimento
*Parâmetro Requerido (IDEMPRESA)
GET
### https://api.homolog.flashentregas.com.br/index.php/api-v1/valores-entregas-bairros/IDEMPRESA


### Lista valor de entrega de um bairro
- Lista o valor de entrega para um bairro cadastrado para o estabelecimento
*Parâmetros Requeridos (IDEMPRESA, IDBAIRRO)
GET
### https://api.homolog.flashentregas.com.br/index.php/api-v1/valor-entrega-bairro/IDEMPRESA/IDBAIRRO

### Criar entrega
- Criação de uma entrega para um estabelecimento para um determinado bairro. O estabelecimento precisa estar habilitado, status Ativo, para solicitar entrega. O estabelecimento não tem autonomia para escolher o entregador em nenhum momento. O estabelecimento só consegue criar entrega se estiver com saldo suficiente. Considerando o valor de cada bairro com relação ao saldo e ao saldo provisionado (valor total das entregas em andamento)
POST
### https://api.homolog.flashentregas.com.br/index.php/api-v1/criar-entrega

*Campos Requeridos
- cd_empresa (código da empresa)
- cd_valor_entrega (código do valor da entrega)
- cd_bairro_destino (código do bairro de destino)
- sn_retorno (Informação se possui retorno (s) ou se não (n))
- sn_pagamento_dinheiro (Informação se a forma de pagamento é em dinheiro (s) ou se não (n))
- ds_observacao (observações)
- cd_entregador (Em branco quando for enviado por estabelecimentos)

### Atualizar entrega
- Atualização da informação de volta ou não de uma entrega
PUT
### https://api.homolog.flashentregas.com.br/index.php/api-v1/atualizar-volta-entrega

*Campos Requeridos
- cd_entrega (código da entrega)
- sn_retorno (Informação se possui retorno (s) ou se não (n))

### Visualizar uma entrega
- Lista os detalhes de uma entrega
*Parâmetro Requerido (IDENTREGA)
GET
### https://api.homolog.flashentregas.com.br/index.php/api-v1/detalhe-entrega/IDENTREGA


### Listar entregas
- Lista as entregas em andamento de um estabelecimento
*Parâmetro Requerido (IDEMPRESA)
GET
### https://api.homolog.flashentregas.com.br/index.php/api-v1/listar-entregas/IDEMPRESA

### Finalizar entrega
- Atualização da informação de que determinada entrega foi finalizada
PUT
### https://api.homolog.flashentregas.com.br/index.php/api-v1/finalizar-entrega

*Campos Requeridos
- cd_entrega (código da entrega)
