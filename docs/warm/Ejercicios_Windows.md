---
title: Ejercicios básicos manejo Windows
description: Apuntes, prácticas, ejercicio del curso de especialización de ciberseguridad. Ejercicio de comandos Windows.
---

1. Despliegue y administración básica de un dominio Windows. El objetivo de esta práctica es desplegar una infraestructura básica basada en Active Directory y realizar tareas habituales de administración.

      1. Debéis instalar un Windows Server 2022 ( o 2019 en su defecto), un cliente Windows 11 en sendas máquinas virtuales en VirtualBox y configura ambas máquinas para que puedan comunicarse entre sí.
         
      2. Debéis crearos un usuario con vuestro nombre en el cliente
       
      3. Debéis promocionar el Windows Server a controlador de dominio. El nombre de dominio será "cibers8a"
       
      4. Debéis añadir al usuario del cliente en el dominio

      5. Crea los siguientes usuarios de dominio: "Alumno1" "Alumno2" "Profesor"

      6. Crea los grupos: "Alumnos", "Profesores" y añade los usuarios al grupo correspondiente.

      7. Crea una carpeta compartida denominada: "C:\Compartida" y

            - Comparte la carpeta en red. 
            - Asigna permisos de lectura al grupo Alumnos. 
            - Asigna permisos de control total al grupo Profesores. 
            - Comprueba desde el cliente que los permisos funcionan correctamente.
         
      8. Deberéis configurar una GPO que impida a los usuarios acceder al panel de control, obligue a utilizar contraseñas complejas y que establezca una longitud mínima de 12 caracteres.

      9. Tras forzar la aplicación de la GPO, debéis comprobar en el cliente que vuestro que esas politicas se han asignado correctamente.

      10. PowerShell es una de las herramientas más utilizadas por administradores de sistemas y analistas de ciberseguridad para obtener información, automatizar tareas y realizar auditorías. Responde a las siguientes preguntas y cual es el comando que has utilizado

            - ¿Cuántos usuarios hay en el dominio?
            - ¿Qué usuarios tienen privilegios de administrador?
            - Busca el servicio de Windows Update. ¿Está iniciado o detenido?
            - ¿Qué dirección IP tiene tu equipo?
            - ¿Qué proceso está utilizando más memoria?

      10. Abre el Visor de eventos e identifica:

            - Un inicio de sesión correcto.
            - Un apagado o reinicio del sistema.
            - Un intento de acceso incorrecto (si existe).


2. El segundo ejercicio propuesto se trata de realizar la [siguiente sala](https://tryhackme.com/r/room/winadbasics) de TryHackMe y adjuntar una captura donde se va que se ha completado el 100% de la misma.