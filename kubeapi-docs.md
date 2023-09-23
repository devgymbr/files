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
    "labels":  ["equipe-x", "projeto-y"],
    "ports" : [
        {
            "name":"http",
            "port" : 65
        }
    ]
}
```


##### Response 


### 2️⃣ DELETE /deployments/:id 

### 3️⃣ GET /deployments/:id


## Como rodar a API

Você pode rodar o container simplesmente com docker run 

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
