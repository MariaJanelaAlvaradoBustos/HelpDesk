## Identificación de Actores
Los usuarios que interactuarán con el sistema se dividen en los siguientes roles:
* **Cliente / Usuario Final:** Empleado o cliente que experimenta un problema técnico o necesita un servicio. Su objetivo principal es reportar incidencias y hacer seguimiento de sus solicitudes.
* **Técnico de Soporte (Agente):** Personal de TI encargado de recibir, diagnosticar y resolver los tickets. 
* **Administrador del Sistema:** Supervisor responsable de gestionar las cuentas de usuario, configurar el catálogo de servicios (categorías, prioridades) y analizar los reportes de rendimiento.

## Requerimientos Funcionales (RF)
* **RF-01 (Gestión de Usuarios):** El sistema debe permitir la autenticación de usuarios según su rol (Cliente, Técnico, Administrador).
* **RF-02 (Creación de Tickets):** Los clientes deben poder generar un nuevo ticket, seleccionando la categoría del problema y adjuntando una descripción detallada.
* **RF-03 (Asignación):** El sistema debe permitir la asignación de tickets a técnicos de forma automática (por carga de trabajo o categoría) o manual (por el Administrador).
* **RF-04 (Gestión de Estados):** El técnico debe poder actualizar el estado del ticket (Nuevo, Asignado, En Progreso, Resuelto, Cerrado).
* **RF-05 (Notificaciones):** El sistema debe enviar alertas (vía correo o panel) cuando el ticket cambie de estado o reciba un comentario.

## Requerimientos No Funcionales (RNF)
* **RNF-01 (Mantenibilidad):** El código debe estar estructurado bajo patrones de diseño (Creacionales, Estructurales, Comportamiento) para facilitar su actualización.
* **RNF-02 (Escalabilidad):** El sistema debe soportar el crecimiento de la base de usuarios y volumen de tickets sin degradar el rendimiento.
