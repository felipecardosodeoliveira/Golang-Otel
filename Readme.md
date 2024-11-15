## Golang-Otel
Um sistema de consulta de temperatura por CEP.

Como usar
Clone o repositório:

```bash

git clone git@github.com:felipecardosodeoliveira/Golang-Otel.git
cd Golang-Otel

Dentro da pasta raiz, execute o comando para iniciar os serviços com Docker Compose:
docker compose up

Serviços
Serviço A: Recebe um CEP e encaminha a solicitação para o Serviço B.

Serviço B: Recebe o CEP, encontra a localização, recupera a temperatura e retorna a resposta formatada.

Endpoints
Serviço A
Aceita um corpo JSON com o campo cep (uma string de 8 dígitos). Retorna informações sobre a cidade e a temperatura.

Exemplo de requisição:
 
POST http://localhost:8080/cep HTTP/1.1
Host: localhost:8080
Content-Type: application/json

{
    "cep":"81490420"
}


Serviço B
GET /cep/{zipcode}
Aceita um parâmetro de rota zipcode (uma string de 8 dígitos) e encontra a cidade e a temperatura, retornando os dados formatados.

Exemplo de requisição:

GET /cep/01001000
Exemplo de resposta:

HTTP/1.1 200 OK
Content-Type: application/json
Date: Fri, 15 Nov 2024 17:27:08 GMT
Content-Length: 68

{
  "city": "Curitiba",
  "temp_C": "22.4",
  "temp_F": "72.3",
  "temp_K": "295.4"
}


Rastreamento
Este projeto utiliza OpenTelemetry e Zipkin para rastreamento distribuído. 

http://localhost:9411

