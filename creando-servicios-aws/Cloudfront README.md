**Amazon CloudFront** es un servicio web de **Red de Entrega de Contenido (CDN, por sus siglas en inglés)** que acelera la distribución global de contenido estático y dinámico a los usuarios finales.

---

## ⚙️ ¿Cómo Funciona?

* **Red global de servidores perimetrales (*Edge Locations*):** CloudFront utiliza una red distribuida mundialmente para acercar el contenido geográficamente a los usuarios.
* **Sistema de caché inteligente:** 
    * Si el archivo solicitado está almacenado en el servidor perimetral (*hit*), se entrega de inmediato con baja latencia.
    * Si no está en caché (*miss*), CloudFront lo recupera del servidor de origen, lo entrega al usuario y guarda una copia para futuras solicitudes.

---

## 🧩 Componentes Clave

* **Origen (*Origin*):** Es la fuente central de donde CloudFront obtiene los archivos originales. Puede ser un bucket de **Amazon S3**, instancias **EC2**, un **Application Load Balancer**, **API Gateway** o incluso servidores externos.
* **Ubicaciones de Borde (*Edge Locations*):** Nodos globales invisibles al usuario que gestionan el almacenamiento en caché y el enrutamiento del tráfico de manera totalmente automática.

---

## Trabajando con cloudfront
* la mayor ventaja de usar cloudfront es el cache , para hacer las pruebas primero crearemos un bucket con una imagen simple para que cloudfront sepa que cachear:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9db47816-2aba-43de-a6ab-dff18525492b" />

* Lo demas lo dejamos todo en default y creamos el bucket
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a46da239-1646-4962-a739-074ef9afc1d7" />

*Una vez creado su bucket recuerden ponerle una imagen
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/36289024-b7b6-4871-84c0-095e2b9941ab" />

* Ahora iremos al servicio de cloudfront y le damos a create :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e0af2983-0fd1-46a2-b057-9cefbea53e49" />

* usaremos la capa gratuita y le damos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/38c99880-093c-4baa-9aa4-b275fa87d336" />

* Le pondremos un nombre y una descripcion , eso que dice domain es para que tu url tenga un nombre especifico , por ahora no es necesario pues no somos una empresa ni nada de eso asi que le daremos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/093e636b-50ba-431d-bd25-51d9f961386b" />

* Lo mas importante , en specific origin le ponemos el s3 y  abajo buscamos el s3 creado para selecccionarlo , esto es lo que cacheara el bucket
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1a11aa78-7a5b-4825-b1d5-03cd68482087" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fea0e617-0dfb-411b-bf4e-ddf7f5106503" />

* lo de abajo siempre lo dejamos abilitado la seguridad , de caso contrario romperas seguridades y tendras que arreglarlo tu manualmente , le damos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/526259dd-69de-4161-b23e-8f296bb22a30" />

* esta parte para hacerles un resumen ( proximamente curso de seguridad en la nube ) sirve para que AWS bloquee las direcciones IP maliciosas y el tráfico sospechoso , le damos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1fc890bc-2468-4a07-be5b-c5b08f14e106" />

* ahora le damos a create distribution
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1c438711-03c4-4ced-b864-1b7e4d717ae8" />

* para ver mas informacion le damos a la opcion general y veremos los parches HTTP , el nombre ,la descripcion y los edge location q usa
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/813eea2e-62c3-49cf-8d6b-34972b28f6a9" />

* Ahora usaremos el link del cloudfront para entrar a nuestro s3
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9ec589b6-322a-4e36-a5f3-bf376c357b20" />

* y el momento de la verdaaaa.... no funciono , pero porque no? porque no le dimos permisos a nuestro s3 el s3 por defecto siempre intenta proteger nuestro archivos asi que iremos a darle permisos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/977bc99b-c0c3-4f0a-bdee-a15673b818c4" />

* volvemos al s3 , entramos a nuestro bucket y en la zona de permisos agregamos esto:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4fbf308f-59a9-4593-b07c-165ea2c2fb6c" />

* con esto le daremos permisos , le damos a aplicar y esperamos 2 minutitos q cargue
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/78b9f18d-1ab7-4945-83c6-9d92c230a767" />

* Aa y algo importante al volver al cloudfront y entrar al dominio nos seguira bloqueando , debemos ponerle el nombre del s3 al final
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/88a76fc3-88bf-4212-9c1b-01110d84670c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0334921d-43f2-4333-bd70-96387fe4ba5c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/beb11c42-d2e6-479b-aefc-82c4d842f960" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6f9b270f-4152-41c8-a542-94805d656da8" />

* finalizamos ... ahora haremos la prueba del cacheo primero entramos a la imagen desde el s3 y el otro desde el cloudfront
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/17c89571-4b9e-4b49-955c-fb5d8de17a9c" />

* le damos a inspeccionar y a la opcion de networking a las dos imagenes ,uno del s3 y otro del cloudfront
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c245c3d7-5b04-460b-9c9f-44a552aeab75" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7b5f6481-3ba0-4db7-a7c5-6ed6833b42fd" />

* les explicare lento ,en una tengo mi imagen de s3 y en otro la del cloudfront , bordee de rojo los ms que son el tiempo que demoran en traer en la imagen , si se dan cuenta el s3 tiene 396 ms PEROOO SI VAMOS AL CLOUDFRONT TENDRA 73ms , porque pasa esto? porque cuando yo entro al cloudfront le pido la imagen a el y este servicio es un intermediario que trae la imagen de
* manera mas rapida , es un edge location ,y esto hace que la imagen llegue mas rapido a mi que llendo al s3 , espero se me haya entendido..
*imagen del s3:
<img width="1920" height="1080" alt="Captura de pantalla (5895)" src="https://github.com/user-attachments/assets/2ce3c398-9bc9-42d9-94b8-3c8ac507bce5" />

* imagen del cloudfront:
<img width="1920" height="1080" alt="Captura de pantalla (5896)" src="https://github.com/user-attachments/assets/8b1847c8-cb5c-476d-9413-52d3106ef46a" />

* como dato curioso yo borre mi servicio de s3 pero el servicio de cloudfront sigue teniendo la imagen , esto se debe porque cloudfront a traves de su edge location ya guardo la imagen ( aparte del cache de mi pc)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/df59ddf3-f326-41ca-9f4d-24e2a179f5a8" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c7cc160c-3d2a-4938-b975-2f956dbf213a" />

*eso seria todo , con esto probamos que clodufront entrega imagenes o objetos de s3 de forma mas rapida , esto reduce la latencia y mejora el rendimiento de una app , NO OLVIDEN BORRAR TODO LO CREADO gracias porver
