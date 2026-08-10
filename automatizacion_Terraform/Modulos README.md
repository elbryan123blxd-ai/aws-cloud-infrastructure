<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/509ca479-be6b-4e80-b6b7-f28053f029d7" /># Módulos en Terraform 🚀

Bienvenido a este repositorio. Aquí encontrarás la estructura base y los ejemplos necesarios para comprender y utilizar **módulos de Terraform**, permitiendo gestionar infraestructura en la nube de manera modular, limpia y reutilizable.

---

## ¿Qué es un Módulo?

Un módulo es un contenedor o paquete que agrupa múltiples recursos de infraestructura relacionados entre sí (como servidores, redes, bases de datos o reglas de seguridad) bajo una misma lógica de código. 

En lugar de duplicar código cada vez que necesitas levantar una arquitectura similar, los módulos actúan como **plantillas o moldes prefabricados** que puedes invocar cuantas veces quieras.

---

## ¿Para qué sirven?

* **Reutilización:** Escribe tu arquitectura una sola vez y despliégala en múltiples entornos (por ejemplo, `dev`, `qa`, `prod`) cambiando únicamente los parámetros necesarios.
* **Estandarización:** Asegura que todos los componentes de la empresa se desplieguen bajo los mismos estándares y buenas prácticas de seguridad.
* **Organización:** Divide proyectos complejos y masivos en componentes pequeños, legibles y fáciles de mantener.
* **Centralización:** Si necesitas actualizar una configuración técnica en el futuro, solo modificas el código dentro del módulo una vez y se propaga de forma controlada.

---

### Trabajando con modulos
* vamos a mover nuestros outpods a nginx_server_module , este sera nuestro modulo ahora y estamos moviendo todo ahi
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e2a26ee0-bcea-467d-b405-76df6f8fb36e" />

* vamos a crear un archivo main y tenemos aca esta invocando a nuestro modulo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/933d10fe-ab53-432d-8008-a82e5a6b61ca" />

* Importante , por cada modulo que usemos siempre pondremos terraform init
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a5aa692-938c-470f-bb21-00c37602d026" />

* Pero fallo nuestro archivo ,porque?
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/67d155ec-75b3-422c-9c8c-1dbd07ee97f1" />

* Resulta que al crear el nuevo main ahora se llama nginx-server-dev pero nuestra keey pub tiene un nombre antiguo , debemos arreglar eso para que terraform sepa que archivo aplicar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bd4c9abe-4732-4597-86d6-84c71f423732" />

* a verdad y tmb borrar este tfvars pues no usaremos esas variables por ahora
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/348ec64f-bf48-4d22-8a69-b296588fed24" />

*si quiero ver los dns y el ip le asignamos este codigo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0e224045-03a3-469a-88d5-12264cfc7551" />

* La razon por la que tengo dos outpods pues uno de esos outpods expone los modulos hacia afuera porque vive en una carpeta interna , el otro outpot que pusimos en el main simplemento es el receptor y el que hace que se vea en la terminal
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/63c81d17-5e78-42b4-8797-45b9112067cf" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9a1cbd7c-f5ea-44e4-9bc9-1cb9c4c816f6" />

* Ahora veremos su dns y el ip desde la terminal
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/335bf34a-efb5-40ca-b539-35aa8e40f279" />

* a continuacion usaremos todo el mismo molde que usamos de nginx_Server_module parra crear otra instancia por separado , asi que ponemos el comando ssh-keygen -t rsa -b 2048 -f "nginx-server-qa.key" para generar un par de llaves key , no debemos generarle una pasword para que tf se comunique
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3c35cc80-9a22-4fbd-8d9c-20fa30217afb" />

* ahora el siguiente paso es aprovechar esa llave para levantar tu segundo servidor
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3a800ccd-3916-49ff-b5df-bb1ece9a2827" />

* ahora tambien le agregamos nuestro propio outpot para ver sus IPS y DNS
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/587d9ee7-7234-4c89-982f-801775dc4d7d" />

* recuerden siempre darle a tf init cuando creemos un nuevo modulo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7327b281-dae0-463b-8ea0-7f0aa2f3cd80" />

* podemos guardar el plan en un archivo para usarlo despues , esto hace que no estemos asignando otro plan , usamos el comando : terraform plan -out server_qa.tfplan
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7fccccf1-10a7-4727-a285-ef962d94ba6d" />

*ahora nos guardo un comando de tf apply ahora podremos usarlo y evitar sorpresar al aplicar cosas que no queriamos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ee4dc399-b5b3-4864-92cc-0a4c5ffc4d03" />

* Como veran se crearon mis dos ec2 totalmente independientes
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/298e0033-c0ed-401b-964a-5fa96e82836c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6edcfb40-07e8-4c18-ac33-fea9543f2da7" />

* vayamoos a la siguiente clase donde explicare que es el tfstate ( o intentare estudiarlo rapido)
