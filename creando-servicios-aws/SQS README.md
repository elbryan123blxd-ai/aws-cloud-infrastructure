# Introducción a AWS SQS (Simple Queue Service)

AWS SQS es un servicio de colas de mensajes totalmente gestionado que permite desacoplar y escalar microservicios, sistemas distribuidos y aplicaciones sin servidor.

## ¿Cómo funciona?

[Productor] ---> ( Enviar Mensaje ) ---> [ Cola SQS ] ---> ( Recibir Mensaje ) ---> [ Consumidor ]

## Trabajando en AWS
* vamos a AWS sqs y le damos a create queues
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/93ec8ada-b467-4c8d-b996-4d8954b7b559" />

* la configuracion de los SQS:
<img width="1920" height="1080" alt="Captura de pantalla (6276)" src="https://github.com/user-attachments/assets/e05ce155-cfa4-481a-8072-85152a61d60b" />

* le daremos a next y se creara nuestra queue , ahora iremos a send and receive mensajes para ver la cola
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/37269b98-f1ea-4ffd-bc68-51c4ad614bd9" />

* podemos enviar varios mensajes
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a2c82baf-7931-4269-b98f-5bfc8badec3a" />

* bajamos y le damos a poll for mensajes
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/776aced4-2324-4525-af1a-6e12e9214eac" />

* vemos los 4 mensajes que cree y salen en el orden
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d9df16ad-009c-4bce-bc41-73c6aad90cf6" />

* a diferencia de un SNS este es mensaje que va dirigido a un script , un microservicio o funcion lambda , NO ES UN MENSAJE DE TEXTO , PARA ESO SIRVE SNS BESTIA
