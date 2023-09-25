# Documentação Kube API 

Essa documentação é parte do desafio [Crie um cliente HTTP para uma API REST da Devgym](https://app.devgym.com.br/challenges/9bcad7c4-a809-4ef5-929d-a000aede5b25). 

## Endpoints 


### 1️⃣ POST /deployments 

##### Request 

Esperado

* Header Content-Type=application/json
* Corpo abaixo  

```json
{
    "id" : "08f807b7-87f2-4990-bc61-56d69627147e",
    "replicas" : 1,
    "image" : "golang",
    "labels":  {
        "monitor-label": "service-y",
        "deployment-tag": "xpto"
    },
    "ports" : [
        {
            "name":"http",
            "port" : 65
        }
    ]
}
```


##### Response 

* Status Code 201 - Sucesso.
```json
{
    "id": "08f807b7-87f2-4990-bc61-56d69627147e",
    "labels":  {
        "monitor-label": "service-y",
        "deployment-tag": "xpto"
    },
    "replicas": 1,
    "image": "golang",
    "name": "",
    "ports": [
        {
            "name": "http",
            "port": 65
        }
    ],
    "createAt": "2023-09-30T00:00:00Z"
}
```

* Status code 409 - Erro de conflito, outro deployment ja criado com esse ID.
* Status code 5xx - Erro interno da API.  



### 2️⃣ DELETE /deployments/:id 

##### Request 
Requisição sem corpo.

##### Response 

* Status Code 204 - Sucesso.
* Status Code 404 - Deployment não encontrado.
* Status code 5xx - Erro interno da API 

### 3️⃣ GET /deployments/:id

##### Request 
Requisição sem corpo.

##### Response 

* Status Code 200 - Sucesso com o mesmo corpo do POST endpoint.
* Status Code 404 - Deployment não encontrado.
* Status code 5xx - Erro interno da API 

## Como rodar a API

Você vai precisar de ter o Docker instalado na sua máquina assim como uma conta autenticado no registry padrão dockerhub. 
Depois disso, você pode simplesmente subir um container com docker run 

```bash
# a api estará disponível em localhost:3000
docker pull -p 3000:8080 devgymbr/dg-kubeapi:9777542381a884289d28b36e0580c84816850dd5
```

Ou criar um arquivo `docker-compose.yaml` na pasta do seu projeto e rodar `docker-compose up`. O arquivo yaml teria a seguinte configuração 

```yaml
version: '3'
services:
  api:
    image: 'devgymbr/dg-kubeapi:9777542381a884289d28b36e0580c84816850dd5'
    ports:
      - '3000:8080'
```  

⚠️ No dockerhub temos docker images para as arquiteturas `linux/amd64` e `linux/arm64`, se precisar compilar e rodar o projeto em outra arquitetura, sinta-se livre em criar sua própria imagem usando o código fonte da API https://github.com/devgymbr/dg-kubeapi. 
