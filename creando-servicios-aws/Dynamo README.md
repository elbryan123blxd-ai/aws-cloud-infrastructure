# 🚀 Introducción a Amazon DynamoDB

> Una base de datos NoSQL clave-valor y de documentos totalmente administrada que ofrece un rendimiento de milisegundos de un solo dígito a cualquier escala.

---

## 📋 ¿Qué es DynamoDB?

**Amazon DynamoDB** es un servicio de base de datos NoSQL sin servidor (*serverless*) proporcionado por AWS. Está diseñada para ejecutar aplicaciones de alto rendimiento que requieren una baja latencia constante a cualquier escala. Al ser un servicio totalmente administrado, abstrae la complejidad de aprovisionar, parchear o administrar servidores físicos, clasterización o mantenimiento de infraestructura.

---

## ✨ Características Principales

* **⚡ Rendimiento a escala:** Ofrece latencias consistentes de lectura y escritura de milisegundos de un solo dígito.
* **📈 Escalabilidad automática:** Escala la capacidad de almacenamiento y rendimiento (throughput) hacia arriba y hacia abajo de forma automática según la demanda de la aplicación.
* **☁️ Sin servidor (Serverless):** Cero administración de servidores. Pagas únicamente por los recursos que consumes (modo bajo demanda o aprovisionado).
* **🔄 Replicación Global (Global Tables):** Permite replicar datos de manera activa y global en múltiples regiones de AWS con escrituras de baja latencia.
* **🛡️ Seguridad y Cumplimiento:** Cifrado en reposo con AWS KMS, control de acceso detallado mediante políticas de AWS IAM y auditoría integrada.
* **📡 DynamoDB Streams:** Captura los cambios a nivel de elementos en orden cronológico, facilitando la integración con AWS Lambda para arquitecturas orientadas a eventos.

---

## 🏗️ Conceptos Fundamentales

A diferencia de las bases de datos relacionales tradicionales (RDBMS), DynamoDB maneja una estructura flexible:

| Componente | Descripción |
| :--- | :--- |
| **Tablas (Tables)** | Colecciones de datos (equivalente a una tabla SQL, pero con un esquema flexible). |
| **Elementos (Items)** | Unidades individuales de datos compuestas por atributos (equivalente a una fila o registro). |
| **Atributos (Attributes)** | Un par fundamental de clave-valor que representa un dato específico (equivalente a una columna). |
| **Clave Primaria (Primary Key)** | Identificador único para cada elemento. Puede ser: <br>• **Simple:** Clave de partición (*Partition Key*).<br>• **Compuesta:** Clave de partición + Clave de ordenamiento (*Sort Key*). |

---
# Trabajando con dynamo DB
* entramos a nuestra cuenta de amazon y vamos a Dynamo DB
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9dc3a5f3-4f01-4137-973e-6342bedb2e74" />

* entramos a la seccion de tables y le damos a create table
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cbbf9b95-61c5-4edf-813a-74afd5cc5958" />

* Una imagen vale mas que mil palabras , a continuacion indicamos cada componente de la tabla y como funcionan
<img width="1920" height="1080" alt="Captura de pantalla (5725)" src="https://github.com/user-attachments/assets/c3d790ad-4953-4769-8e5e-01dde00f6bb2" />

*Dejaremos lo demas en default y le damos a continuar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8b781474-276d-4a15-821f-ed256e9f2387" />

* Entramos a nuestra tabla y observaremos que no tenemos datos todavia , los vamos a crear dandole click a create item:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/94a3d46c-6c61-41ad-9ff5-cf74749941b2" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/778784bb-ef60-4a3e-9b8d-213468a0c39d" />

* Al entrar aqui veremos los valores que tendran los datos , a continuacion empezaremos a llenar esa daatabase
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fd240449-32ac-4211-a0a8-8cef9a5a5006" />
*podemos observar que tambien podemos agregar mas tablas como querramos , en mi caso una tabla donde salga si alcanzaron vacante

* Si le damos a create veremos como se creo una base de datos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7801ecd8-a08a-4dff-8356-cf54347b1443" />

*Una ventaja de dinamo DB es que puede ser flexible pues podemos ponerle datos a un usuario que a los demas no queremos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/131e7447-29f0-4a1e-a55c-12f87a187b99" />

* Ahora entraremos a nuestro vs code para ver nuestros datos automatizadamente
* para no hacerles un cuento grande , cree una interfaz de vs code y cree un archivo .py  , luego conecte mis credenciales de aws , puse un codigo especifico , instale en la terminal python boto3 y finalmente se observaron mis datos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9a1042fe-6607-4c40-b684-dfd2ac9e2bce" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5f78ef35-f9ad-4bf1-baed-b088585f9f1b" />

*esto nos ayuda para evitar darle clicks a nuestro aws a cada rato
*finalizaremos eliminando los objetos creados , gracias por ver , #contratenme

* como dato curioso si nuestro dynamo fallo , o lo eliminaron , o le paso algo nos saldra este mensaje en vs code al querer conectarnos nuevamente
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/41fe51c5-8cd4-4bb3-b0c8-cf2451891937" />
