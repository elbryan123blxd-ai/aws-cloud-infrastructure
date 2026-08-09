# Estructura Modular en Terraform

## Introducción
Al escalar proyectos de infraestructura como código, mantener toda la configuración en un único archivo (`main.tf`) se vuelve insostenible. La **modularización y separación en archivos** es una de las mejores prácticas en el mundo DevOps.

Terraform procesa automáticamente todos los archivos con extensión `.tf` dentro de un mismo directorio como una configuración unificada. Aprovechar esto nos permite organizar los recursos según su responsabilidad lógica.

## ¿Por qué separar tus archivos?
* **Mantenibilidad:** Facilita la lectura y edición al trabajar con archivos pequeños y enfocados.
* **Depuración:** Localiza errores rápidamente al saber exactamente en qué archivo reside cada componente.
* **Trabajo en equipo:** Reduce los conflictos de control de versiones (Git) al permitir que diferentes colaboradores trabajen en recursos distintos simultáneamente.
* **Orden:** Establece una estructura profesional y escalable para proyectos de cualquier tamaño.

## Ejemplo de Estructura Recomendada
Para mantener el orden, sigue una nomenclatura que indique el propósito de cada componente:

| Archivo | Responsabilidad |
| :--- | :--- |
| `00.variables.tf` | Definición de variables de entrada. |
| `01.provider.tf` | Configuración del proveedor de nube y región. |
| `02.ec2.tf` | Definición de instancias y recursos de cómputo. |
| `03.key.tf` | Gestión de pares de llaves SSH. |
| `04.sg.tf` | Reglas de seguridad y firewall. |
| `terraform.tfvars` | Asignación de valores reales a las variables. |

---
*Diseñado para mantener una infraestructura limpia, profesional y fácil de escalar.*

# Trabajando con la separacion de archivos
*en git bash usamos el comando  :  touch 00.variables.tf 01.provider.tf 02.ec2.tf 03.key.tf 04.sg.tf terraform.tfvars outputs.tf  para crear todos los archivos necesarios
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6fe77317-1c90-46a6-bb78-ed94a6ee7bb7" />

*veremos la creacion de los archivos necesarios
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4678c16b-38b5-4b72-a66b-dcb22a7ffd89" />

* a verdad usaremos este codigo nuevo, los unicos cambios son que les asigne variables y cambie algunos valores:
```hcl
variable "ami_id" {
  description = "ID de la AMI para la instancia EC2"
  default     = "ami-0440d3b780d96b29d"
}

variable "instance_type" {
  description = "Tipo de instancia EC2"
  default     = "t3.micro"
}

variable "server_name" {
  description = "Nombre del servidor web"
  default     = "nginx-server"
}

variable "environment" {
  description = "Ambiente de la aplicación"
  default     = "test"
}

###### provider ######
provider "aws" {
  region = "us-east-1"
}

###### resource ######
resource "aws_instance" "nginx-server" {
  ami           = var.ami_id
  instance_type = var.instance_type

  user_data = <<-EOF
  #!/bin/bash
  sudo yum install -y nginx
  sudo systemctl enable nginx
  sudo systemctl start nginx
  EOF

  key_name = aws_key_pair.nginx-server-ssh.key_name

  vpc_security_group_ids = [
    aws_security_group.nginx-server-sg.id
  ]

  tags = {
    Name        = var.server_name
    Environment = var.environment
    Owner       = "elbryan123blxd@gmail.com"
    Team        = "Cloud"
    Project     = "contratenme xfa"
  }
}

###### ssh ######
resource "aws_key_pair" "nginx-server-ssh" {
  key_name   = "nginx-server-ssh"
  public_key = file("nginx-server.key.pub")

  tags = {
    Name        = "${var.server_name}-ssh"
    Environment = var.environment
    Owner       = "elbryan123blxd@gmail.com"
    Team        = "Cloud"
    Project     = "contratenme xfa"
  }
}

###### SG ######
resource "aws_security_group" "nginx-server-sg" {
  name        = "${var.server_name}-sg"
  description = "Security group allowing SSH and HTTP access"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name        = "${var.server_name}-sg"
    Environment = var.environment
    Owner       = "elbryan123blxd@gmail.com"
    Team        = "Cloud"
    Project     = "contratenme xfa"
  }
}

####### output #######
output "server_public_ip" {
  description = "Dirección IP pública de la instancia EC2"
  value       = aws_instance.nginx-server.public_ip
}

output "server_public_dns" {
  description = "DNS público de la instancia EC2"
  value       = aws_instance.nginx-server.public_dns
}
```
*ahora entramos a cada uno de los archivos creados y le pondremos su contenido , el contenido viene del propio main:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/48b2a3b4-f7c8-4b24-8b1b-dffeb0984c0e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d2543d0e-aa3f-4243-b65f-6acfda245cd3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ac1a4516-21fc-49ca-b036-09e22af4d046" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e40a4e27-8865-4aca-9530-0ce998e1d122" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e6692918-8d28-47b7-9a17-3937467b18e5" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cac2be34-9bdc-4449-b947-19976ff0a955" />

* nuestro archivo main se quedara vacio :C, pues empezamos a poner los valores del main en varios archivos por separado asi que lo borraremos :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/475dbf65-6ea5-4d9c-9706-7bb2a301da1d" />

* Ahora en .tfvars asignaremos valores reales que declaramos en nuestro proyecto
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d88792fd-19de-4ead-a28f-85026aaeff8b" />

* Al momento d e darle tf apply saldran los valores que se cambiaron en las instancias
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7addb5cf-5f56-4943-ba8a-6353ee138944" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/18e5b57c-d53b-4382-9385-ee6bb2f02dce" />

*que pasa si tenemos dos archivos tfvars?? como sabremos cual escogera terraform:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e07ad943-eb88-4c33-bd3d-106e8bfd9361" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2e76217d-495f-4bed-b622-e5b25e0837ae" />
* como veran tengo dos archivos tf vars , para escoger uno debemos decirle explicitamente a la terminal que tfvars queremos usar

* usamos el comando : tf plan --var-file=contratenme.tfvars   ,  y tf nos indicara que se cambiaran algunas cosas pues estamos agarrando otro tfvars
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/82de70d4-6e34-4fff-9814-796e5ef27400" />

* Si se dan cuenta tf es inteligente y nos indica que cosas van a cambiar
<img width="1920" height="1080" alt="Captura de pantalla (5805)" src="https://github.com/user-attachments/assets/df109060-cd0d-4ee3-9847-2a629a4d4954" />

* OJO , HACIENDO ESTO NO ESTAMOS CREANDO DOS MAQUINAS DE TERRAFORM , SIMPLEMENTE LES CAMBIAMOS LAS CARACTERISTICAS

* ESTE ARCHIVO ES EL QUE MANDA Y PARA TERRAFORM ESTAMOS MODIFICANDO EL MISMO ARCHIVO
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/953af52b-73e8-442c-85c0-7d47b0551f68" />

* recuerden siempre darle el comando terraform destroy , la siguiente seccion voy a averiguar para crear dos maquinas virtuales distinas para dos entornos distinos , por ejemplo una maquina para test y otro para produccion , una vez mas gracias por ver #contratenme
