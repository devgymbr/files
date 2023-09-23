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
