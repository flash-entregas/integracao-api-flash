# integracao-api-flash

# Métodos
Requisições para a API devem seguir os padrões:

Método	Descrição
GET	Retorna informações de um ou mais registros.
POST	Utilizado para criar um novo registro.
PUT	Atualiza dados de um registro ou altera sua situação.
DELETE	Remove um registro do sistema.

# Respostas
Código	Descrição
200	Requisição executada com sucesso (success).
400	Erros de validação ou os campos informados não existem no sistema.
401	Dados de acesso inválidos.
404	Registro pesquisado não encontrado (Not found).
405	Método não implementado.

# ROTAS

GET
https://api.homolog.flashentregas.com.br/api-V1/estados

# Descrição
- Lista estados cadastrados

GET
https://api.homolog.flashentregas.com.br/api-V1/cidades

# Descrição
- Lista cidades cadastradas

GET
https://api.homolog.flashentregas.com.br/api-V1/cidades-estado/IDESTADO

# Descrição
- Lista cidades de um estado
*Parâmetro Requerido (IDESTADO)

GET
https://api.homolog.flashentregas.com.br/api-V1/valores-entregas-bairros/IDEMPRESA

# Descrição
- Lista os valores de entregas para os bairros cadastrados para o estabelecimento
*Parâmetro Requerido (IDEMPRESA)

GET
https://api.homolog.flashentregas.com.br/api-V1/valor-entrega-bairro/IDEMPRESA/IDBAIRRO

# Descrição
- Lista o valor de entrega para um bairro cadastrado para o estabelecimento
*Parâmetros Requeridos (IDEMPRESA, IDBAIRRO)

POST
https://api.homolog.flashentregas.com.br/api-V1/criar-entrega

# Descrição
- Criação de uma entrega para um estabelecimento para um determinado bairro. O estabelecimento precisa estar habilitado, status Ativo, para solicitar entrega. O estabelecimento não tem autonomia para escolher o entregador em nenhum momento. O estabelecimento só consegue criar entrega se estiver com saldo suficiente. Considerando o valor de cada bairro com relação ao saldo e ao saldo provisionado (valor total das entregas em andamento)

*Campos Requeridos
- cd_empresa (código da empresa)
- cd_valor_entrega (código do valor da entrega)
- cd_bairro_destino (código do bairro de destino)
- sn_retorno (Informação se possui retorno (s) ou se não (n))
- sn_pagamento_dinheiro (Informação se a forma de pagamento é em dinheiro (s) ou se não (n))
- ds_observacao (observações)
- cd_entregador (Em branco quando for enviado por estabelecimentos)

PUT
https://api.homolog.flashentregas.com.br/api-V1/atualizar-volta-entrega

# Descrição
- Atualização da informação de volta ou não de uma entrega

*Campos Requeridos
- cd_entrega (código da entrega)
- sn_retorno (Informação se possui retorno (s) ou se não (n))

GET
https://api.homolog.flashentregas.com.br/api-V1/detalhe-entrega/IDENTREGA

# Descrição
- Lista os detalhes de uma entrega
*Parâmetro Requerido (IDENTREGA)

GET
https://api.homolog.flashentregas.com.br/api-V1/listar-entregas/IDEMPRESA

# Descrição
- Lista as entregas em andamento de um estabelecimento
*Parâmetro Requerido (IDEMPRESA)

PUT
https://api.homolog.flashentregas.com.br/api-V1/finalizar-entrega

# Descrição
- Atualização da informação de entrega finalizada

*Campos Requeridos
- cd_entrega (código da entrega)
