<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e1055b6d-e7cf-4e1b-a63e-06dc0b1bad47" /><img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8d451be5-7d12-408d-a73b-5e822d0e5b24" /># ¿Qué es Amazon RDS?
Es un servicio gestionado que permite ejecutar motores de bases de datos populares sin la necesidad de gestionar la infraestructura subyacente. RDS automatiza tareas como:
* **Provisionamiento:** Configuración de instancias y almacenamiento.
* **Mantenimiento:** Aplicación de parches de seguridad y actualizaciones de software.
* **Resiliencia:** Copias de seguridad automáticas (backups) y recuperación ante desastres.
* **Alta Disponibilidad:** Replicación multizona (Multi-AZ) para tolerancia a fallos.

## Motores de Base de Datos Soportados
RDS ofrece flexibilidad al soportar una amplia variedad de motores estándar y optimizados:
* **Motores Estándar:** MySQL, PostgreSQL, MariaDB, Oracle, SQL Server e IBM Db2.
* **Amazon Aurora:** Un motor de base de datos de alto rendimiento desarrollado por AWS, totalmente compatible con MySQL y PostgreSQL, diseñado para ofrecer velocidad y disponibilidad a nivel empresarial.

## ¿Por qué utilizar Amazon RDS?
1. **Administración simplificada:** Reduce drásticamente la carga operativa al manejar tareas rutinarias automáticamente.
2. **Escalabilidad:** Permite aumentar la capacidad de cómputo y almacenamiento con pocos clics o mediante políticas automáticas.
3. **Seguridad:** Proporciona aislamiento de red (mediante VPC), cifrado de datos en reposo y en tránsito, y control de acceso robusto (IAM).
4. **Rendimiento:** Ofrece opciones optimizadas tanto para almacenamiento como para cómputo, adaptándose a diversas cargas de trabajo.

# Trabajando con AWS RDS
*Entramos a RDS y vamos a la seccion de databases y le damos a full configuration
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9527cee0-9b6c-40d6-a765-f2ba566e8525" />

* Escogemos el Postgres SQL y full configuration
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a51a49cf-804f-4684-9f29-94c60e8caa35" />

* Tenemos 3 tipos de disponibilidad , las zonas de disponibilidad son como copias de respaldo que hacen que tu app sea mas resilente a caidas, mientras mas copias mas seguridad tienes,a continuacion cada una:

*single-AZ DB: es para pruebas y desarrollos , pues solo tiene una zona de disponibilidad

*Multi-AZ DB instance deployment (2 instances):para producciones mayores, es el estandar para empresas medianas

*Multi-AZ DB cluster deployment (3 instances): La mas cara y fuerte de todos ,  para empresas que no pueden permitir caidas

*En nuestro caso usaremos la economica , solo haremos test de pruebas
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/93ce5810-80d9-40e8-953f-f88dccf6bd7e" />

* dejamos la version postgres en default y le agregamos nombres
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/93b1ef0f-fc0f-46af-8a5c-af439ce62b00" />

* lo configuramos asi y creamos un password
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fda7ce44-68d3-4efd-a59f-b69bdf2d27ca" />

* Ponemos esta configuracion y escogemos el motor mas chiquito , el mas piolin para evitar gastos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c7761531-a34e-43ee-a42e-528b906c0116" />

* el general propouse es una tecnologia de discos y caracteristicas de rendimiento , dejarlo asi , el 20gib es para el espacio reservado para exclusivamente base de datos, y el numero 1000 indica que tus base de datos pueden agrandarselo si necesitan , con una capacidad maxima de hasta 1000gib
 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d464d9b-e874-48bf-82b6-b3fcc02e0690" />

 *Lo demas lo deamos en default y el acceso publico(solo para el test, en prod no hacer esto)
 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/aea1f683-835f-4900-8010-ee93da8a8487" />

* La region le configuramos donde estamos ahora
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/40a58410-4d85-4e73-949a-0e86320d5bf5" />

* Lo demas dejamos en defalt y creamos el database y esperamos a que cargue
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3fc6bcba-e733-4bff-87e9-f14ea424a99c" />

### Ingresando a nuestro database
* a continuacion ingresaremos a nuestro database mediante el cloudshell y crear unas tablas

* le damos click a nuestro database y seleccionamos la opcion cloudshell , luego le daremos a launch cloudhsel
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8b0cf17d-941a-480d-bc22-21cd9fadd61d" />

*le ponemos un nombre y se estara creando un ambiente , luego nos pedira contraseña 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/57dff3d5-7c3f-44d1-9ab6-9e70c18d1eee" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/397818b8-67f5-40b9-bb1b-6ea403fb5cf5" />
 
*para crear tablas usaremos este comando: CREATE TABLE usuarios (id SERIAL PRIMARY KEY, nombre VARCHAR(50));      luego le daremos a \d    , asi es como tenemos nuestras tablas
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d123e5b2-7df7-4032-8c6c-0cd66f8f3ac5" />

*tambien podemos crear replicas de nuestros databases, para tener mejor rendimiento y dividir el trabajo de los database  , le daremos click a create red replica
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6fa7e89f-1d10-426b-a1f1-a423522e92b1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6f85c617-c28d-48fc-b050-a7ebb904bbf0" />

*cuando tenga mas conocimiento dare una clase de AWS nivel avanzado

