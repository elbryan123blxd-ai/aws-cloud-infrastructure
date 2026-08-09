# 🚀 Terraform Variables: Precedence & Loading Order

Este documento detalla el orden de precedencia y las formas en que Terraform carga las variables (variables y su orden de prioridad de menor a mayor).

## 📋 Orden de Precedencia (De menor a mayor prioridad)

Cuando defines variables en Terraform, el sistema sigue una jerarquía estricta para determinar qué valor utilizar si hay múltiples fuentes. El orden de prioridad (del 1 al 7, donde el último sobrescribe a los anteriores) es el siguiente:

1. **Manual / Valores por defecto (`default`)**: Los valores definidos dentro del bloque `variable` en los archivos `.tf`.
2. **Variables de entorno (`Environment variables`)**: Variables del sistema operativo con el prefijo `TF_VAR_` (ej. `TF_VAR_nombre_variable`).
3. **Archivos `terraform.tfvars` o `terraform.tfvars.json`**: Archivos de configuración automática estándar en el directorio raíz.
4. **Archivos `*.tfvars` personalizados (no cargados por defecto)**: Archivos con extensión `.tfvars` que deben pasarse explícitamente mediante el argumento `-var-file=archivo.tfvars`.
5. **Archivos automáticos `*.auto.tfvars` o `*.auto.tfvars.json`**: Archivos que Terraform carga automáticamente si tienen el sufijo `.auto.tfvars`.
6. **Argumentos en línea de comandos (`-var` y `-var-file`)**: Los valores pasados directamente al ejecutar comandos de Terraform en la terminal.

## Trabajando  con las variables

### Forma manual
* la forma manual es la mas tediosa y honestamente es la menos practica , pero es bueno saber siempre todos los datos, tengo mi codigo tf y en resumen esta variable consiste en escribir manualmente en la consola los datos que nos faltan, ahi escribi en otra carpeta variable.tf de forma manual 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ab57c440-fc4a-47a3-9d9a-a76fc3a2b8db" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/03020b23-0689-43ab-b1c8-3048b0c18653" />

*Como veran nos esta pidiendo de forma manual poner los datos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/57d7b120-a550-4ca9-959e-fffa3dca6fd6" />

### Forma default
* simplemente cambiamos el formato variable.tf y le pones datos default para que terraform lo lea y sepa que poner de forma predeterminada, por ejemplo yo quiero siempre crear un ec2 t2.micro porque soy misio , creo el default y con eso siempre que cree una ec2 no tengo que especificar todo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/57b212d7-8fae-4c9a-b7df-c6ae803499c7" />

### Forma DE TF_FAR_name
*esta forma sirve para poder guardar tus datos en tu terminal.. miren primero cambiaremos el archivo variable.tf , ponemos el comando TF_VAR_ .... y el nombre de tu instancia o region ,etc y cada vez que le de a terraform apply lo usara con esos datos que ya guardo en la terminal
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b1718795-b328-4635-907b-e438dd7d7e09" />

### terraform.tfvars.json
*esta es una de mis favoritas porque los datos se quedan en un archivo ,y puedo hacer un gitignore y nunca mis credenciales ,ademas que se ve mas limpio y profesional , entonces funcionaria asi

*main.tf =s el que utiliza esos valores para construir la infraestructura en AWS
*variables.tf: Es el que declara las variables (anuncia qué variables van a existir y de qué tipo son).
terraform.tfvars.json: Es el que guarda los valores reales de esas variables de forma limpia y automática.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f860634c-73ea-45f5-a662-f5ea597586eb" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5973c153-9dcf-4b20-80e0-d509bbdceb2f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0c265cbc-44cd-4057-9916-17ec8912d3a3" />


### -var-file
* este funciona distinto , pues en la terminal pondremos el nombre de nuestro archivo seguido de -var-file
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/02107885-0c77-4a7a-b1ce-153f8ae0445e" />

*para que sirve? supongamos que tenemos una configuracion de las cosas para subirlo a produccion y otra configuracion para subirlo a pruebas , con eso simplemente pones ese comando y le dices a terraform que datos quiere que use en este preciso momento


### infra.auto.tfvars
* es lo mismo que el anterior pero mejro porque se activa solito , solo pones terraform apply y se cargan los datos solitos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dd90aa0e-d388-49b8-92b7-ae1ec4470796" />


### -var and -var file
* el ultimo solo es que tu le especifiques que servicios tendra en la misma terminal
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/38f5f03f-e05e-4236-b0e0-7ebd00f5c5b9" />
