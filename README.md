# ProyectoClientes_ServerlessDynamoDB
Proyecto Personal para la gestión de clientes implementando Serverless, Lambdas, Api Gateway y DynamoDB

</hr>

</br>   

## Instalación y Configuración de Serverless Local
* Una vez abierto el proyecto instalamos  serverless de forma Global `npm install -g serverless`
* Seguidamente creamos toda la config de serverless para nuestro proyecto(en mi caso el nombre del proyecto es `project-dynamodb`) `serverless create --template aws-nodejs --path project-dynamodb && cd project-dynamodb`
* Luego inicializamos el package.json en el proyecto `npm init -y`.
* Instalamos el plugin serverless-offline `npm i serverless-offline`
* Comprobamos versión `serverless --version`
* Salida Esperada ..
   ``` cmd
    Framework Core: 3.23.0
    Plugin: 6.2.2
    SDK: 4.3.2

   ```
* Agregamos el plugin instalado de serverless-offline al archivo `serverless.yml`
* Configuramos tipo de método y path a través de httpApi.
* Configuramos el puerto http 
* Archivo serveless.yml..
  ``` yml
  
   service: project-dynamodb

   frameworkVersion: '3'

   provider:
     name: aws
     runtime: nodejs12.x

   plugins:
     - serverless-offline 

   custom: 
     serverless-offline:
       httpPort: 4000   

   functions:
     hello:
       handler: handler.hello
       events:
         - httpApi:
             method: GET
             path: hello

  ``` 
   
  
</br>   

* Guía Oficial : https://www.serverless.com//blog/serverless-framework-v3-is-live)   
* Guía Recomendada : https://medium.com/@patricio.aranguiz/serverless-offline-aws-lambda-api-gateway-15a4dfdfbc16   
   
</br>

## Ejecución de Serverless Local
* Por defecto tenemos configurado una lambda llamada handler a través de su función .hello
* Comprobamos la config generada.
* Levantamos serverless con el comando `sls offline start` o `serverless offline start`
* Visualizamos el endpoint local que serverless nos genera..
     ``` cmd
     Starting Offline at stage dev (us-east-1)

   Offline [http for lambda] listening on http://localhost:3002
   Function names exposed for local invocation by aws-sdk:
              * hello: project-dynamodb-dev-hello
              
    GET | http://localhost:3000/hello   
    POST | http://localhost:3000/2015-03-31/functions/hello/invocations 
    
    Server ready: http://localhost:4000
  ``` 
* Nos dirigimos al `http://localhost:3000/hello`


## Archivo `serverless.yml` 
* 
   
## Instalación de DynamoDB Local
(Guía Recomendada : https://fauna.com/blog/develop-using-serverless-offline)
* Dentro del directorio del proyecto ejecutamos `npm i serverless-dynamodb-local --save`
* Comprobamos versión `serverless --version`
* Salida Esperada : 
   ``` cmd
    Framework Core: 3.23.0
    Plugin: 6.2.2
    SDK: 4.3.2

   ```
</br>   
