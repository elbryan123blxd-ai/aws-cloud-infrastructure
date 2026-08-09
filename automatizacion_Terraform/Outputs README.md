# AWS Outposts
es un servicio totalmente administrado que extiende la infraestructura, las API, los servicios y las herramientas de Amazon Web Services (AWS) directamente a tus centros de datos, espacios de coucolocation o instalaciones locales (*on-premises*).

Esta solución permite a las organizaciones ejecutar cargas de trabajo de manera local manteniendo una experiencia técnica consistente con la nube pública de AWS.

---

## 🚀 Características Clave

* **Consistencia Operativa:** Utiliza las mismas herramientas de aprovisionamiento (como **Terraform** o CloudFormation), API y consola que ya conoces en la nube.
* **Baja Latencia:** Ideal para aplicaciones que requieren procesamiento de datos en tiempo real y ultrarrápido cerca del origen de la información.
* **Residencia de Datos:** Permite cumplir con normativas legales y de seguridad que exigen que los datos permanezcan en instalaciones físicas específicas bajo tu control.
* **Administración Completa:** AWS se encarga del mantenimiento físico, las actualizaciones y el monitoreo del hardware.

---

## 🛠️ Integración con Terraform
* agregue unos codigos mas , con esta imagen estoy explicando que son , en resumen son codigos que hacen que nos den el codigo IP y el DNS de nuestras maquinas virtuales
<img width="1920" height="1080" alt="Captura de pantalla (5752)" src="https://github.com/user-attachments/assets/f2de6197-3807-4132-a5f5-f50622d4f7fd" />

*A no me dejaba crear el tf porque no tenia una vpc predeterminada , procedemos a crear y asignar una VPC default muy importante eso
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a1295471-e373-42f0-898c-f5ee7e7b6192" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5b08a22a-459f-40a5-817e-2a1708b0b6df" />

* Ahora si deberia funcionar  , como pueden observar sale el ip y su dns en la terminal mismo , eso evitar andar buscandolo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8aa1ba6b-b11f-42fd-911e-36480d9d48bf" />

* Tambien podemos entrar ahi usando curl http://(ip de la instancia)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/34f4c2ae-7e01-40ab-be32-4e6502c5fd8a" />

* O desde el internet
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e80369b7-36ff-430b-bd4a-36f6c3668201" />

* Y no solo eso , en vez de usar la terminal de amazon y conectarse ahi , podemos hacerlo desde nuestra pc con el codigo  ssh ec2-user@34.207.80.28 -i ./nginx-server.key     , como veran fijense en el nombre , sale que entramos al ec2-user felicidadees entramos desde nuestro vs code
* <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1f3fd7c3-b114-47af-aef6-9b4cd5831bcc" />
