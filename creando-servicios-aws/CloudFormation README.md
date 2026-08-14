# ☁️ AWS CloudFormation

## 📌 Introducción

**AWS CloudFormation** es un servicio de **Infrastructure as Code (IaC)** de Amazon Web Services que permite definir, crear y administrar recursos de AWS mediante código.

En lugar de crear manualmente cada recurso desde la consola de AWS, CloudFormation permite utilizar **templates escritos en YAML o JSON** para describir la infraestructura que queremos desplegar.

CloudFormation se encarga de crear estos recursos y administrarlos como un conjunto llamado **Stack**.

---

## 🎯 Objetivo

El objetivo de este proyecto es aprender los fundamentos de **AWS CloudFormation** y aplicar el concepto de **Infrastructure as Code (IaC)** para automatizar el despliegue de infraestructura en AWS.

---

## Trabajando con AWS CloudFormation :
* creacion de entorno local en VS code
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8f84402f-b8f2-4a98-a2fb-0833ea36bee9" />

* asignacion de los valores:
<img width="1920" height="1080" alt="Captura de pantalla (6533)" src="https://github.com/user-attachments/assets/4b613f52-e63b-455b-a19d-57a1b4a4ec53" />

* ahora vamos al servicio de cloudformation e iremos a la opcion de stacks a darle a crreate stacks
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/70a2553e-bd67-420d-8ab7-3ae797f4313f" />

* entramos y le damos al boton de chose file
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3f2698e8-8a79-4449-91f6-6803a0bd171d" />

* escogemos el archivo de ec2 que creamos y le damos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/15ecf14d-8c8e-4b83-b403-5e8f3f7ebf10" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7ecc81bd-dda6-48dc-abaa-a71014f28b91" />

* le podemos un nombre y escogemos un tipo de instancia( cloudFormation leyo el codigo .yaml y se dio cuenta que en la seccion de parametros puse opciones para escoger) , escogemos una y le damos a next
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7d0fd6c6-4160-490f-b3da-7bb4909071bb" />

*aca podemos poner etiquetas ( util en entornos de trabajo para saber quien creo que y donde va ) y en permisos limitamos permisos con politicas IAM
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c0a0010d-1c5e-4f44-afaf-927837607834" />

* aca son opciones de que deberia hacer cloudformation en caso de fallos
<img width="1920" height="1080" alt="Captura de pantalla (6544)" src="https://github.com/user-attachments/assets/781126a2-fa25-4fa4-a9aa-fcb2c2293b17" />

* despues le damos a next y nos llevara a la opcion de stacks , para ver nuestros servicios de template y le damos a view in infraestructura composer
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b97cf8bd-84d3-453c-85cf-4a2564f4e8ab" />

* nos saldra informaicon sobre nuestro servicio
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f1684af6-f763-4aab-af7b-371d5f926a6f" />

* podemos ir al servicio de EC2 para ver su creacion y la informacion
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/50828620-034e-4f19-97f2-11a8fb8d872f" />

* para borrarlo simplemente entramos al stack de cloudformation y lo borramos
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/80f03ae2-07f9-485c-8b2d-dfe62142cd14" />

* gracias x ver

