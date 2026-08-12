# Introducción a Amazon SNS (Simple Notification Service)

Amazon SNS es un servicio de mensajería totalmente gestionado de AWS diseñado para la comunicación directa y masiva entre aplicaciones (A2A) o de aplicación a persona (A2P). Funciona bajo un modelo de **publicación/suscripción (Pub/Sub)**, lo que permite desacoplar los sistemas emisores de los receptores de forma eficiente.

## Características Clave
* **Arquitectura Push:** Entrega mensajes de forma inmediata a los suscriptores en cuanto se publican.
* **Abanico de Salida (Fan-out):** Envía un único mensaje de forma simultánea a múltiples destinos.
* **Alta Disponibilidad:** Infraestructura escalable y redundante que tolera fallos de manera automática.

## Destinos Compatibles
* **Sistemas (A2A):** Colas de Amazon SQS, funciones AWS Lambda y endpoints HTTP/S.
* **Personas (A2P):** Mensajes de texto (SMS), correos electrónicos y notificaciones push móviles.

## Trabajando en aws
* entramos a SNS en aws en la seccion de topis
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b41a70bd-4b51-4f7c-b464-8b4da5a2a9cf" />

* le damos a crear topic , lo ponemos en formato estandar y un nombre
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/aa7807ec-9f2b-4be6-804c-f5b6c49f2d87" />

* le damos a create topic y ya tenemos nuestro SNS , ahora queremos que se le envie a un correo , en ese caso usare el mio
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c46dd18b-efc4-4f6f-b8a3-3c6a7aa04a83" />

* vamos a darle a create suscriptions
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/37e0bf75-4bd3-4040-9685-f52212e884bf" />

* pondremos nuestro datos de email
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e4d40602-3958-464c-af1e-bc53f49a1181" />

* ahora seleccionaremos el topic que habiamos creado y le daremos a publish mensaje
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3cc870a8-8466-4d86-917a-53e9288a9333" />

* por ahora solo le pondremos un nombre y el contenido
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/77d48160-ec7e-4094-817b-efbc9cbba000" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4508815b-941d-492d-8d5d-9d80a605d922" />

* una vez publicado en nuestro crreo en la seccion de spam debemos habilitar para que nos llegue los mensajes
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4f924ef4-79a7-43d1-aeed-b448321723e3" />

## Problema que resolvi
* la confirmacion de que queriamos recibir mensajes de aws era ANTES DE ENVIAR UN MENSAJE por eso no salia
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/df88f1c4-d5cd-4a51-94d8-206e76c2ca53" />

* ahora envie otro mensaje esta vez con la verificacion ya hecha y si me llego el mensaje
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/157eae5c-0a57-4ab7-ab06-48ca52106808" />

* hay formas de automatizar este proceso pero lo hare proximamente
