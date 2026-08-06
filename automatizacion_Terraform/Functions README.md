# Despliegue de Servidor Nginx con Terraform

Este proyecto contiene la infraestructura como código (IaC) necesaria para desplegar una instancia EC2 en AWS, configurar un servidor web Nginx y establecer las reglas de seguridad necesarias.

## 📋 Requisitos Previos

- Tener instalado **Terraform**.
- Configurar tus credenciales de AWS en tu entorno.
- Un archivo de clave pública SSH en el directorio raíz llamado `nginx-server.key.pub`.

## 🚀 Código de Terraform

Copia el siguiente bloque en tu archivo `main.tf`:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "nginx-server" {
  ami           = "ami-0440d3b780d96b29d"
  instance_type = "t3.micro"

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
    Name        = "nginx-server"
    Environment = "test"
    Owner       = "ariel.molina@caosbinario.com"
    Team        = "DevOps"
    Project     = "webinar"
  }
}

resource "aws_key_pair" "nginx-server-ssh" {
  key_name   = "nginx-server-ssh"
  public_key = file("nginx-server.key.pub")

  tags = {
    Name        = "nginx-server-ssh"
    Environment = "test"
    Owner       = "ariel.molina@caosbinario.com"
    Team        = "DevOps"
    Project     = "webinar"
  }
}

resource "aws_security_group" "nginx-server-sg" {
  name        = "nginx-server-sg"
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
    Name        = "nginx-server-sg"
    Environment = "test"
    Owner       = "ariel.molina@caosbinario.com"
    Team        = "DevOps"
    Project     = "webinar"
  }
}
```

## Trabajando con terraform
* una imagen vale mas que mil palabras asi que les mandare capturas de mi codigo para que entiendan , a continuacion 3 imagenes descriptiva

<img width="1920" height="1080" alt="Captura de pantalla (5590)" src="https://github.com/user-attachments/assets/5eed9fa8-898b-4d09-bab4-4655cfa7290c" />
<img width="1920" height="1080" alt="Captura de pantalla (5596)" src="https://github.com/user-attachments/assets/6ba75ed2-9cb9-4459-ab5d-7e82db1f99cb" />

* Cadacodigo tiene su significado , asi que alistamos nuestros comandos , tf init , tf apply
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6ef72805-09d5-46e7-948a-0c130f16a207" />
* como veran dice Plan: 3 to add, 0 to change, 0 to destroy. , lo que significa que estamos agregando el ec2 , security group y el SSH
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/85697121-992c-4a10-82cb-06b30d49d839" />

* verrificamos que esta bien todo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ee3445c6-5037-412e-a77e-ace6e1794a2c" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/80b48256-fbb3-407c-9978-30f80eadece1" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c8287faf-7ecf-43fc-9ec8-58f95f54b593" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bbf55fd2-0f23-43c3-938d-2857c90f05d9" />


