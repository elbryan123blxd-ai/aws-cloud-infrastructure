# AWS Lambda

> Servicio de computación **serverless** para ejecutar código en respuesta a eventos sin administrar servidores.

---

## ⚡ Características Clave

* **Sin Servidores:** Cero gestión de infraestructura, parches o sistemas operativos.
* **Escalado Automático:** Se ajusta al instante según la cantidad de eventos entrantes.
* **Pago por Uso:** Facturación exacta basada en los milisegundos de ejecución.

## 🧩 Componentes Principales

| Componente | Función |
| :--- | :--- |
| **Función** | El código o script encargado de procesar la tarea. |
| **Trigger (Disparador)** | El evento de AWS que activa la ejecución automáticamente. |
| **Runtime** | El entorno seguro del lenguaje de programación (Python, Node.js, etc.). |

## Creando un servicio Lambda

* entramos a la consola de AWS y escribimos en el buscador Lambda
<img width="1920" height="1080" alt="Captura de pantalla (4784)" src="https://github.com/user-attachments/assets/cd025d5d-59f8-4576-86b6-ccfc58d2b615" />

* le damos a create function
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/172d6e61-ef6a-4d50-af09-238d510280dc" />

* Dejaremos la opcion predeterminada que sirve para hacer una demonstracion de como funciona
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1c1929f2-4663-42b3-9398-0f4011251f2c" />

* Agregamos un nombre y en la opcion de runtine seleccionamos Python
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6bea7114-d4cd-4d95-8950-6620b27e1b31" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b1beadd8-e4c7-4e00-bcb9-17e70dae688b" />

* Para que sirven estos servicios?
<img width="1920" height="1080" alt="Captura de pantalla (4794)" src="https://github.com/user-attachments/assets/b3d9e054-4e49-4ee6-932a-030f576fdf00" />

* **Durable execution:** Sirve para apps que deben verificar su estado para resolver inconvenientes que ocurren.

* **EC2 capacity provider:** Es para asignarle EC2, lo dejamos así por ahora.
  

* Creamos la function y deberia salir algo asi:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/22309742-e0ab-4486-b661-2e50c4e5d7a7" />

* Hacemos scrool y..... que es todo esto?
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e863f572-0039-4957-8170-d7790241827f" />

* para abreviarlo un poco es un codigo que nos dio lambda predeterminado que consiste en

* es una plantilla de bienvenida que ejecuta una funcion lambda cada vez que lo despertemos, procesara la llamada y devolvera una respuesta diciendo:"¡Todo salió bien (código 200) y aquí tienes el mensaje: Hello from Lambda!"
<img width="1920" height="1080" alt="Captura de pantalla (4806)" src="https://github.com/user-attachments/assets/ee1f744a-beb7-439f-a072-88c5500e68fc" />

* Para crear el evento primero le damos a create test event
<img width="1920" height="1080" alt="Captura de pantalla (4808)" src="https://github.com/user-attachments/assets/6546ff1a-95e9-45b0-9355-fa10a99ce49a" />

* Le agregamos un nombre y dejamos lo demas por defecto
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2a718cd9-b9cd-4e3c-9097-0d6bb7858647" />

* Le damos al boton de save
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1651ad52-b80e-4519-9cb0-8724b2fc5e3a" />

* Ahora le damos al boton Test
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/775a1adc-a817-4df3-9f70-2d882478872d" />

* Felicidades, lograste ejecutarlo y te salio el mensaje con exitooo
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1e9dab45-c605-4c86-a591-85d5839267aa" />

* Recuerda borrar tu funcion lambda por temas de limpieza y buena practica
<img width="1920" height="1080" alt="Captura de pantalla (4815)" src="https://github.com/user-attachments/assets/b607f859-05ae-4a8e-a9fa-12d95e5718ee" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2730d0a2-c444-493a-9566-4560c4d3cc05" />











