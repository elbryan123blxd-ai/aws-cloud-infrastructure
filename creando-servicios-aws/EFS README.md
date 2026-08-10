## 🚀 ¿Qué es EFS?

**Amazon Elastic File System (EFS)** es un servicio de almacenamiento de archivos simple, sin servidor (*serverless*) y elástico diseñado para utilizarse con servicios de AWS y recursos locales. Está pensado para escalar bajo demanda sin interrumpir las aplicaciones, creciendo y reduciéndose automáticamente a medida que se agregan y eliminan archivos.

---

## ⚡ Características Principales

* **Elástico y Escalable:** Crece desde gigabytes hasta petabytes de forma automática sin necesidad de aprovisionar almacenamiento por adelantado.
* **Acceso Concurrente:** Permite que miles de instancias de Amazon EC2, contenedores y servidores locales accedan a los datos simultáneamente mediante el protocolo **NFSv4**.
* **Alta Disponibilidad y Durabilidad:** Los datos se replican de manera automática en múltiples Zonas de Disponibilidad (AZs).
* **Optimización de Costos:** Cuenta con clases de almacenamiento inteligentes (*Infrequent Access* y *Archive*) que mueven los datos inactivos a niveles más económicos.
* **Seguridad Integrada:** Soporta cifrado en tránsito y en reposo mediante AWS KMS, además de un control de acceso detallado con políticas de IAM y permisos POSIX.

---
## Traabajando en AWS
* primero crearemos un EFS , le ponemos nuestro nombre y verificamos que tengamos una VPC default y le damos a create
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ff27ba61-c9de-439b-a6aa-90ab39965dd4" />

* Cuidado, les puede pasar como yo que elimine mi vpc default pensando que era un servicio XD , para eso vamos a la seccion VPC y le damos a create default vpc :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0a39f066-1e05-431a-8745-26815dd2bc3b" />

* Volvemos con los EFS como pueden observar ya las tenemos :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/16a618ee-78e7-41d1-815b-d894e15a4193" />

* Como comente en la introduccion el EFS es como un HUB donde se conectan todos , ahora crearemos ec2 y las vincularemos con el EFS
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b4b1ed96-4f01-47e1-b2d9-4e3f9d4826ea" />

* bajamos hasta la seccion de netwroking donde lo dejaremos asi , esto sirve para que sepa donde esta el EFS en resumen
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d3445b12-ff55-401a-9ef8-fad42f8fda1b" />

*bajamos hasta la seccion de EFS , Le damos a efs y luego a add shared sistem
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/293da73d-3982-4ce5-9ce7-8c023061e4d2" />

* Si bajamos hata el ultimo nos saldra un sript que se monto automaticamente , esto sirve para configurar y montar a la instancia ( son como instrucciones ), le damos a create
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/17d0310e-0302-49a8-acc6-5811847fb869" />

* ya tenemos nuestras 2 instancias creadas
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/70d27021-9e67-4a1b-82a1-ca5f49400f93" />

* entramos a cada instancia y le damos a connect :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4ff0d792-7c5d-45e2-9f0b-567bc2f8c16d" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f0d8752b-356e-48bf-95a1-dde4b2361873" />

* Ahora estamos dentro de las 2 ec2:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3c81a79f-9e03-453f-b1ef-56911ad52356" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/927578aa-f212-4758-9205-cc652b00b496" />

* Vamos a crear un archivo txt en una instancia y DEBERIA SALIR en la otra instancia

*Entre a una carpeta y cree mi archivo txt
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dc186dbf-4dc2-477e-8b94-e3103fb77780" />
* Ahora deberia salir en la ontra instancia :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bf2f7d00-f03f-4ab9-ac4e-86be50a86aa0" />

* como veran las dos si estan vinculadas pues me salen los mismos archivos y podemos hacer mas cosas como modificar los txt para ver si contenido en el otro , NUNCA SE OLVIDEN ELIMINE EL EFS Y LOS EC2 , NO HAGAN COMO YO QUE DEJE PRENDIDO EN OTRA REGION Y ME LO OLVIDE UN MES Y ME QUEDE POBRE 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/91df8629-1cdb-4d13-afa1-69d33710dd0e" />
* proximamente estudiare e investigare mas para subir clases sobre economia en la nube y como apagar bien tus cosas







