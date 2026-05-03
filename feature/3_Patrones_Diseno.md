# Implementación de Patrones de Diseño

Para garantizar que el sistema de Help Desk sea escalable y mantenible, se ha diseñado la arquitectura integrando tres patrones de diseño fundamentales, cumpliendo con las buenas prácticas de ingeniería de software.

## Patrón Creacional: Factory Method
**Problema:** El sistema necesita crear diferentes tipos de tickets (Incidencias de Hardware, Problemas de Software, Solicitudes de Acceso) sin acoplar el código a las clases específicas de cada ticket.
**Solución:** Se implementa `TicketFactory`. El cliente solicita un ticket pasando el tipo, y la fábrica se encarga de instanciar la clase correcta.
* **Clase Base:** `Interface Ticket`
* **Fábrica:** `TicketFactory.crearTicket(tipo)`
* **Beneficio:** Si en el futuro se añade un nuevo tipo de ticket (ej. Mantenimiento Preventivo), solo se modifica la fábrica, respetando el principio Abierto/Cerrado (Open/Closed).

## Patrón Estructural: Facade (Fachada)
**Problema:** El proceso de crear un ticket complejo implica interactuar con varios subsistemas: verificar el usuario, validar el SLA (Prioridad), registrar en base de datos y enviar notificación inicial.
**Solución:** Se crea una clase `HelpDeskFacade`.
* **Uso:** El cliente o la interfaz gráfica solo llama a `HelpDeskFacade.generarNuevoTicket(datos)`.
* **Beneficio:** Oculta la complejidad estructural del sistema al cliente. El Facade se encarga por detrás de orquestar al `UsuarioService`, `SlaService` y `NotificacionService`.

## Patrón de Comportamiento: State (Estado)
**Problema:** Un ticket pasa por múltiples estados lógicos (Nuevo, Asignado, En Proceso, Resuelto, Cerrado). Dependiendo del estado, el ticket tiene reglas diferentes (ej. un ticket "Cerrado" no puede ser modificado por un técnico).
**Solución:** Se implementa el patrón State para que el ticket cambie su comportamiento dinámicamente.
* **Contexto:** Clase `Ticket` que tiene una variable de tipo `EstadoTicket`.
* **Estados (Clases concretas):** `EstadoNuevo`, `EstadoEnProceso`, `EstadoCerrado`.
* **Beneficio:** Evitamos tener un código lleno de condicionales (`if/else` o `switch`) gigantes. Cada estado maneja su propia lógica de transición.
