# 🛡️ AWS IAM (Identity and Access Management) - Resumen Completo

Este repositorio contiene un resumen detallado sobre **AWS IAM** basado en los conceptos clave de un nivel **AWS Certified Cloud Practitioner**, abarcando autenticación, autorización, gestión de usuarios, políticas, credenciales y buenas prácticas de seguridad en la nube.

---

## 📋 Tabla de Contenidos
1. [¿Qué es AWS IAM?](#qué-es-aws-iam)
2. [Componentes Principales: Users, Groups & Policies](#componentes-principales-users-groups--policies)
3. [Claves de Acceso (AWS Access Keys)](#claves-de-acceso-aws-access-keys)
4. [Autenticación Multifactor (MFA)](#autenticación-multifactor-mfa)
5. [Roles de IAM (IAM Roles)](#roles-de-iam-iam-roles)
6. [IAM Identity Center](#iam-identity-center)

# Servicios de AWS

## 1. ¿Qué es AWS IAM?

**AWS Identity and Access Management (IAM)** es un servicio web que te ayuda a controlar de forma segura el acceso a los recursos de AWS

* **Control Centralizado:** Permite gestionar de manera centralizada los permisos para controlar a qué recursos de AWS pueden acceder los usuarios
* **Autenticación y Autorización:** Se utiliza para controlar **quién está autenticado** (ha iniciado sesión correctamente) y **quién está autorizado** (tiene los permisos necesarios) para utilizar los recursos


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2dcddfed-9ba7-456a-8636-6d5384be3a57" />

* podemos ver cosas como los roles , usuarios , los IAM users o IAM users groups
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4df344cb-9add-41b1-8715-27ed133e94fe" />


* Vamos a crear un usuario, pero para que sirve? ,mas que nada para crear cuentas donde puedan entrar trabajadores para que creen EC2 servicios lambda S3 etc
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f085d954-145e-4c46-a9cd-d222bb7cb60f" />


*estando aqui le damos a create user
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7f145088-3270-4062-92a7-45df02d21657" />


*le agregamos un nombre y le damos a NEXT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/408ddd63-de96-4c17-832b-45d503e03461" />


*Lo dejamos todo asi predeterminado y le damos siguiente
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/439dd57a-29b0-4131-b63e-5c730eab7eac" />


* Le das a create USER
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/634b97c6-9400-45df-8f85-4d33513b13d1" />

* Ya tenemos nuestro USER (ignoren el eks-admin , es de otro trabajo)  pero el objetivo de tener un user es darselo a un trabajador para que entre a la consola de AWS perooo.... como lo hacemos?
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7c3ba41d-7fa3-46b7-9a20-76d1f7f35d52" />


* Le damos click al usuario creado y entramos a security credentials
<img width="1920" height="1080" alt="Captura de pantalla (4985)" src="https://github.com/user-attachments/assets/b3bb4682-32d2-4372-844c-67c6dca05b43" />


*le das a Enable console access
<img width="1920" height="1080" alt="Captura de pantalla (4986)" src="https://github.com/user-attachments/assets/5787314d-f415-472e-98ff-c8f81bc99071" />


*seleccionamos la opcion de custom pasword
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c2cf88a4-d1f6-40bd-a04d-55872498d264" />

*Creas tu propia contraseña y le daras a enable console access
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cd7353bf-0f8d-47da-aa64-c504119c97c8" />


* Saldran los  datos del usuario que creaste , el objetivo esque el trabajador entre con esas credenciales e ingrese para que trabaje , tambien le puedes dar a descargar el CSV para pasarle las credenciales a tu usuario y el link , RECUERDA ANOTAR LOS DATOS , una vez le des a close no podras ver los datos nuevamente , anotalos
<img width="1920" height="1080" alt="Captura de pantalla (4990)" src="https://github.com/user-attachments/assets/0b20a8ec-0366-43c8-9276-77c0d84d810b" />

*Ahora entraremos a modo incognito y simularemos que somos otra persona , rellenamos los datos , entramos y ahora si podemos empezar
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/137e9d3e-eaa7-4609-8c86-bdaa8578d260" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f90afdd8-f98a-41c6-ab1f-0f29979dc7ca" />

* perooo... hay un problema , si queremos crear una EC2 con nuestro user creado no nos dejara
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/83904efc-5974-48b8-a594-41ab98f4f1a5" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1504139d-4150-4de0-9588-19b7279c799c" />

*al parecer no tengo acceso , y para eso debemos asignarle los ROLES , son como los permisos que le damos al usuario para hacer cosas, por ejemplo le daremos permisos para que entre a EC2

* volvemos a nuestra cuenta y entramos a nuestro usuario , si se dan cuenta en la seccion de permisos todo esto esta vacio , y es porque no le dimos permisos , asi que le daremos a add permissions
<img width="1920" height="1080" alt="Captura de pantalla (4996)" src="https://github.com/user-attachments/assets/62bca627-a5db-4642-8c42-294d86cbe143" />


*le damos a attach polices directly 
<img width="1920" height="1080" alt="Captura de pantalla (4997)" src="https://github.com/user-attachments/assets/634aad7f-fd7a-496a-8635-8218476f963e" />

*Ahora debemos entrar a nuestro usuario que creamos
*Escribimos EC2FullAccess , para que solo pueda modificar cosas en las EC2 y le damos a next y continuar
<img width="1920" height="1080" alt="Captura de pantalla (4998)" src="https://github.com/user-attachments/assets/550deb8a-ff5b-4a6a-bb86-d296d75b65ab" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fd993e9b-6217-4be6-9ec9-8f12cf9d4e35" />


* Ahora si podemos lanzar nuestra instancia ( dale a lanchar de frente solo para verificar que funciona)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0ebcdb1c-c3c3-4a37-a7b9-4b06298ccd3f" />
*le damos a no recomendado
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bda9dba6-912f-4ad2-b008-771ed8dd1556" />


* Como veran se logro crear una instancia

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7d9d998e-cf1e-465c-b552-90a0381ab149" />

* Recuerden eliminar los usuarios siempre y las instancias creadas para evitar gastos


* Ahora imagina este escenario , tienes 20 trabajadores de aws pero quieres que esos 20 solo trabajen con servicios de S3 , seria tedioso agregarle los permisos a cada usuario no? para eso creamos un IAM GROUP
* El iam grupo es como un lugar donde tu defines los permisos y solo agregas a usuarios ahi



*Primero vamos a crear varios usuarios de prueba (solo agregale un nombre y deja la configuracion predeterminada
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2ab35c8c-8b73-4754-b309-f69365acd9e2" />

*una vez terminado eso creamos nuestro grupo
* Entramos a la seccion de IAM user groups y le damos a crear grupo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/12f50ac9-7e86-4cd5-85f5-e91779d721f1" />

* Le ponemos un nombre , ejm: chambeadores-S3
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/89b8a6a7-ae73-447c-93b2-aac31639d954" />


*en este caso ya creamos nuestros usuarios asi que los seleccionamos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4bae1566-91ba-4f3f-aa63-7178d71318c0" />


*En el permiso de polices ponemos AmazonS3FullAccess , seleccionamos la casilla y creamos el usuario
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1a5eefe2-c1d0-4c90-9d90-c78ceeca7474" />


*Listo , creamos nuestro grupo , si queremos verificar le damos click al a nuestro grupo y nos saldran nuestros usuarios
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a69887b0-9c2a-4a9b-a94b-b0ab7c0de8c0" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8712c475-f8e6-499a-920f-2201ed0e54d9" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/627d5614-88f2-4425-a6e7-739bd31f6415" />




