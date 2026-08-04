# Terraform con AWS 🚀

Bienvenido a esta sección de automatización de infraestructura. Aquí encontrarás configuraciones para desplegar y gestionar recursos en **Amazon Web Services (AWS)** utilizando **Terraform**.

## ¿Qué es Terraform?
Terraform es una herramienta de código abierto desarrollada por HashiCorp que permite definir y aprovisionar infraestructura mediante un lenguaje declarativo conocido como HCL (HashiCorp Configuration Language). 

### Ventajas principales:
* **Infraestructura como Código (IaC):** Versiona, reutiliza y documenta tu arquitectura en la nube de la misma forma que el código de una aplicación.
* **Automatización:** Evita errores manuales en la consola de AWS desplegando entornos completos en segundos.
* **Control de Estado:** Mantiene un registro preciso de los recursos creados gracias a su archivo de estado (`terraform.tfstate`).

# Comandos Principales de Terraform

Terraform se gestiona principalmente a través de cuatro comandos fundamentales para su ciclo de vida. A continuación se detallan cada uno de ellos:

---

### 1. Inicialización (`init`)
Inicializa un directorio que contiene archivos de configuración de Terraform. Este comando descarga los proveedores necesarios y configura el backend.

\`\`\`bash
terraform init
\`\`\`

* **Cuándo usarlo:** Al clonar un proyecto nuevo, al agregar un nuevo proveedor o módulo, o al configurar el backend por primera vez.

---

### 2. Planificación (`plan`)
Crea un plan de ejecución previa. Terraform analiza la configuración actual frente al estado real en la infraestructura y muestra qué acciones se realizarán (crear, modificar o destruir recursos).

\`\`\`bash
terraform plan
\`\`\`

* **Cuándo usarlo:** Siempre antes de aplicar cambios para verificar que el resultado sea el esperado y evitar errores en producción.

---

### 3. Aplicación (`apply`)
Aplica los cambios necesarios para alcanzar el estado deseado de la configuración (ejecuta el plan generado).

\`\`\`bash
terraform apply
\`\`\`

* *Nota:* Puedes usar \`terraform apply -auto-approve\` para omitir la confirmación interactiva (ideal para pipelines de CI/CD).
* **Cuándo usarlo:** Cuando estés seguro de los cambios mostrados en el comando \`plan\` y desees aprovisionar o actualizar tu infraestructura.

---

### 4. Destrucción (`destroy`)
Destruye toda la infraestructura administrada por tu configuración de Terraform.

\`\`\`bash
terraform destroy
\`\`\`

* *Nota:* Al igual que el anterior, acepta el parámetro \`-auto-approve\` para saltarse la confirmación.
* **Cuándo usarlo:** Para limpiar entornos temporales, laboratorios o cuando ya no se necesiten los recursos creados.


## Trabajando con terraform
* Para trabajar con terraform primero debemos tener un usuario IAM en aws y darle todos los permisos de admin
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b0659681-1f41-4d37-99b8-c16fe9e68168" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a28ff865-6fdf-4e8f-b77a-bd3c2ba13051" />

*Le crearemos un par de acces keys
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/91741c63-a871-4aa8-97cb-54bc9060fed0" />

*Nos dirigiremos a vs code donde ya descargamos terraform anteriormente:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/76a94ac7-8b40-4a83-a594-3f58beb4600d" />

* Una imagen vale mas que mil palabras, a continuacion veran un codigo con el significado de cada parte :
<img width="1920" height="1080" alt="Captura de pantalla (5213)" src="https://github.com/user-attachments/assets/0d7518c4-b461-49dc-aab6-d7525c60e869" />

* Cree una carpeta y me movi a ella , y tambien agregue un alias a terraform = tf , para evitar escribir a cada rato terraform
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0a7f23ff-2e93-42f8-9e08-0f0853506b94" />

* Usee el comando tf plan para poder ver una recopilacion de lo que haremos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/32065f6f-781f-41d7-b31e-5fa771e8b539" />

* Usare el tf apply para poder aplicar los cambios
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6a80068c-b485-4ff4-8e9c-e2cf6064807b" />

*YYY.. no funciona esperen intentare resolver esto
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8bf5d76f-c792-4843-aefd-3150eedcf888" />

*Usaremos estre otro codigo , tuve que poner un codigo mejor que busca la imagen mas reciente para evitar descargar imagenes viejas , tambien le di los permisos al IAM user  , no se preocupen por las modificaciones las instancias se crearan igualemtene
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5db5b42f-4596-4985-b619-cfe73d714906" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9cc88b66-463c-4470-920f-1071934a32c5" />

*Ahora si se creo con exito felicidadess, en vez de dar click a todo a cada rato solo ponemos un codigo y ya , mejor
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fb73f999-437b-4fee-a052-e813ba088995" />

*y ahora para eliminar la instancia bryan? facil , entramos a aws , le damos a ............ nanana nada de eso, porque hacer eso si tenemos terraform solo damos el comando : tf destroy
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7cb54b0a-94c3-4641-b773-ac384aff378f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0346496b-f517-47c9-b49f-607caf858357" />

* como veran esos fueron los comandos basicos y una forma de trabajar con terraform , cuando aprenda mas siempre documentare mis cambios , gracias x ver #Contratenme







