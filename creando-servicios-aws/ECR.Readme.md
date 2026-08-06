<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d591ba08-2701-4341-945b-617296dc05a3" /><img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bd6e9a0e-e80c-473f-9961-3059a17beba7" /># Guía de Contenedores AWS: Amazon ECR & Amazon ECS

Resumen técnico y conceptual sobre **Amazon ECR** (Elastic Container Registry) y **Amazon ECS** (Elastic Container Service), los servicios clave de AWS para la gestión y orquestación de contenedores Docker.

---

## 📋 Tabla de Contenidos
1. [Amazon ECR (Elastic Container Registry)](#-1-amazon-ecr-elastic-container-registry)
2. [Amazon ECS (Elastic Container Service)](#-2-amazon-ecs-elastic-container-service)
3. [Flujo de Trabajo: ¿Cómo se relacionan?](#-3-flujo-de-trabajo-cómo-se-relacionan)

---

## 🐳 1. Amazon ECR (Elastic Container Registry)

Es un registro de contenedores Docker privado y totalmente administrado por AWS (similar a Docker Hub pero integrado con la seguridad de AWS).

### ¿Para qué sirve?
Permite almacenar, administrar y desplegar imágenes de contenedores de forma segura y centralizada.

### Características Clave:
*   **Seguridad e Integración IAM:** Control de acceso detallado mediante políticas de AWS Identity and Access Management para definir quién puede hacer *push* o *pull*.
*   **Escaneo de Vulnerabilidades (`scanOnPush`):** Analiza automáticamente las imágenes en busca de fallas de seguridad en el sistema operativo o dependencias al subirlas.
*   **Alta Disponibilidad:** Respaldado por el almacenamiento duradero de Amazon S3.

---

## ⚙️ 2. Amazon ECS (Elastic Container Service)

Es un orquestador de contenedores de alta escalabilidad y alto rendimiento que te permite ejecutar y administrar aplicaciones contenerizadas en la nube.

### ¿Para qué sirve?
Automatiza el despliegue, la gestión de recursos, el balanceo de carga y el escalado de contenedores sin la complejidad de otros sistemas.

### Modos de Ejecución (Compute Engines):
1.  **AWS Fargate (Serverless):** 
    *   No requiere gestionar servidores ni máquinas virtuales.
    *   AWS se encarga del aprovisionamiento y escalado de la infraestructura. Pagas estrictamente por los recursos de CPU y Memoria utilizados.
2.  **Amazon EC2:**
    *   Tú administras las instancias de servidores virtuales que conforman el clúster.
    *   Proporciona control total y personalización a nivel de sistema operativo y hardware.

### Componentes Principales:
*   **Task Definition (Definición de Tarea):** Un archivo JSON (plano o plantilla) que describe los parámetros de tus contenedores (imagen de ECR a utilizar, puertos, variables de entorno, CPU y memoria requerida).
*   **Service (Servicio):** Mantiene un número constante y deseado de réplicas de tus tareas ejecutándose de forma simultánea (ideal para APIs o servicios web que deben estar siempre activos).

---

## 🔄 3. Flujo de Trabajo: ¿Cómo se relacionan?

El ciclo de vida básico para desplegar una aplicación utilizando ambos servicios consta de los siguientes pasos:

1.  **Construcción y Subida:** Creas tu imagen localmente con Docker y la subes (**Push**) a tu repositorio privado en **Amazon ECR**.
2.  **Definición:** Creas una *Task Definition* en **Amazon ECS** configurando la URI de la imagen almacenada en ECR.
3.  **Ejecución:** Desplegaste el servicio en ECS (usando Fargate o EC2), el cual descargará (**Pull**) la imagen desde ECR de forma segura y mantendrá tu aplicación corriendo en la nube.


### Trabajando con los servicios

* primero crearemos un ambiente en vs code local con los siguientes comandos( son simples pero son para una demo)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/faf453d2-60f4-4d8e-8524-2b57760e00bc" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/26dfa93e-af03-4d7f-903f-f5ba654a8f6e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a09cb00a-3556-4ac9-8356-071605e8db8f" />

* En mi caso usare un usuario IAM para esta practica , ponemos el comando aws configure y ponemos sus credenciales , por motimos obvios no pondre mi credencial, recuerden usar el comando aws configure
<img width="1920" height="1080" alt="Captura de pantalla (5471)" src="https://github.com/user-attachments/assets/3aec1199-cd22-4258-a16c-0d577a2e62df" />

* Usamos el comando pip install flask  , para ppoder descargar librerias
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5812967b-a056-4396-9342-8c1fa6012f6f" />

* Si quieremos construir una imagen no nos dejara pues no tenemos docker deskop abierto , siemre mantenerlo abierto
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/67149cc5-7e98-4c72-bea2-894622167b23" />

*Ahora si si le damos a docker build -t (nombre) .    , docker leera tus archivos y como en el ejemplo descargara la imagen python
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b878a66c-de2e-465e-8444-f207241f975c" />

*Ignoren las imagenes de arriba , eran imagenes q ocupaban espacio y tuve q borrarlas , pero al escribir docker images te mostrara tu imagen que creaste:   , si sale tu imagen significa que esta bien 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dd8a59e4-9025-46a1-9d72-181a5d895a67" />

* Ahora creamos un repositorio en  Amazon ECR
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a9757326-185c-47fa-8f85-4c853a370b8b" />

* Le ponemos un nombre y le damos a crear el ECR
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a8051793-ca7c-494a-8a7c-c0909e9daf08" />

*Ahora ya tenemos un repositorio de ECR y entrmoas al repositorio , ahi le damos para view push commands , para ver todos los comandos que debemos poner en nuestro repositorio de vs code para que se puedan vincular
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/24a20516-eff8-48d0-bc01-bfc6373a4e01" />

*Ponemos estos comandos en vs code para que se vinculen:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dc5089f3-2be7-4bc8-b74a-4c4b327e665b" />

*Si miramos nuestro repo de ECR veremos que se subio la imagn principal con sus piezas internas
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e3dfa1ad-f573-4630-8909-9f44918c9bb8" />

*Ahora entramos a ECS para que finalmente lanzemos nuestra imagen a la nube , recuerden , el ECR es como el almacen y el ECS es como el motor que descargara la imagen y la subira a la  nube, a continuacion crearemos un cluster para desplegar nuestras tareas
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f1476d03-ffc2-4438-a260-ed76be7746cb" />

*Le ponemos un nombre y dejamos la configuracion fargate only para evitar manejar ec2 x ahora que son mas complicadas , le damos a create
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a1f1e8c6-3161-4f66-aa30-735874c0188b" />

* A continuacion crearemos una task definition ,es como el plano de arquitectura o la receta que le dice a AWS exactamente cómo debe ejecutarse tu contenedor sino no sabria como correr la imagen
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7846b444-c583-40ff-b7da-6a4fd0d8ae5d" />

*Le ponemos una  nombre, la potencia y el sistema operativo (dejarlo asi esta muy bien)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/08578018-0b2b-4c17-ab24-1a15df0cbfea" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/972632bd-1ace-4fed-acca-6ba6a9b440e8" />

*Esta es la parte mas importante pues vincularemos los serviciosque creamos en ECS , le ponemos esta configuracion , el link lo saque de la imagen latest nginx que creamos antes
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1de0f832-04b2-4a89-b5d5-8ee5fcd68b83" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b20119ce-217b-4c1a-8eb1-bde9c0bab8db" />

*Ahora tenemos nuestro task definition
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/53942baa-e11c-47d8-af99-8ca8a389f856" />

* volvemos a nuestro cluster de ecs ,entramos a el y le damos a crear servicio , su funcion es mantener el container  vivo y controlar las copias que queremos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/15fcf9f2-17c5-46d1-ba0b-acd8e5cc27ae" />

* A continuacion escogemos el task definition que creamos , le ponemos un nombre  y le damos a create
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a142be2a-2158-4b9e-86a7-2fa0fec16227" />

*Listo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/897b7ab5-9222-40fa-8e41-df36c59e238e" />

*SI etramos a nuestro cluster veremos la ip pero no nos deja entrar,  es porque algo bloquea el trafico
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/440b6cf0-e50e-4616-9980-6c48cc354930" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/248a5baa-e89b-46a3-9e9e-723056cd7954" />

* debemos configurar la entrada de puertos IP
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e2ab5983-08f2-4c56-975f-98a1cae58123" />

* AHORA LE PUSE ESTOS PUERTOS
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a29b5cac-033d-4cce-ac0d-d39e6042b43f" />

*Ahora si volvemos a entrar podremos ver el contenido porque esta habilitado
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/48a2aa54-0ba5-4d94-b4aa-7b1a135ef68f" />


*asi es el ciclo de container , desde tu local en vs code hasta en la nube con ecs
