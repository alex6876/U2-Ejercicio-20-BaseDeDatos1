# Base de Datos de Gestión de Espacio de Coworking

Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para un centro o espacio de trabajo compartido (coworking), administrando miembros/usuarios, espacios de trabajo reservables, reservas de instalaciones, registros de control de acceso por RFID y consumos adicionales realizables por los usuarios.

---

## Descripción

El sistema modela una estructura de datos relacional para la gestión operativa y comercial de un espacio de coworking. Permite administrar la información de los miembros y clientes adheridos, los diferentes tipos de espacios de trabajo disponibles (escritorios, salas de reuniones, oficinas privadas), las reservas programadas por fecha y horario, la trazabilidad de los ingresos y egresos mediante tarjetas RFID, y el registro de consommés o servicios adicionales utilizados durante la estancia.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Espacio Trabajo:


* id_Codigo espacio: Clave primaria única identificadora del espacio físico.


* nombre: Denominación o identificación del ambiente (ej. Sala A, Puesto 12).


* tipo de espacio: Categorización del ambiente (ej. sala de reuniones, escritorio individual, oficina).


* capacidad maxima: Cantidad máxima de ocupantes permitidos.


* tarifa x hora: Costo por uso por hora.


* tarifa por joranada: Costo por uso por jornada completa.




* Miembro:


* id_DNI: Clave primaria única identificadora del miembro.


* nombre: Nombre del miembro.


* Empresa: Nombre de la empresa u organización a la que representa.


* correo electronico: Dirección de correo electrónico de contacto.


* Id_tarjeta RFID: Código único del dispositivo RFID asignado para acceso.




* Reserva:


* id_reserva: Clave primaria única del registro de reserva.


* fecha de uso: Fecha programada para el uso del espacio.


* hora de inicio: Hora estipulada de inicio del uso.


* hora de fin: Hora estimada de finalización.


* dias: Duración o días comprendidos en la reserva.




* Control de Acceso:


* id_fichaje: Clave primaria única del registro de fichaje o evento de acceso.


* fecha y hora: Marca temporal en que se registró la lectura de tarjeta.


* sentido del movimiento: Dirección del tránsito registrado (ej. entrada, salida).


* id_tarjeta RFID: Clave foránea o código del dispositivo de lectura vinculado.




* Consumo:


* id_consumo: Clave primaria única del consumo facturado o realizado.


* fecha: Fecha en que se realizó el consumo.


* descripción: Detalle del producto o servicio contratado (ej. café, impresiones, snacks).


* cantidad: Unidades consumidas.


* costo: Valor monetario total o unitario del consumo.





---

## Relaciones del Modelo

1. Espacio Trabajo ↔ Reserva (Relación 1:N):


* Un espacio de trabajo puede ser reservado en múltiples ocasiones a lo largo del tiempo, pero cada reserva concierne a un único espacio de trabajo específico.




2. Miembro ↔ Reserva (Relación 1:N):


* Un miembro puede realizar múltiples reservas para diferentes momentos o espacios, pero cada reserva queda registrada a nombre de un único miembro.




3. Miembro ↔ Control de Acceso (Relación 1:N):


* Un miembro genera múltiples registros de fichaje/acceso cada vez que ingresa o egresa de las instalaciones utilizando su tarjeta RFID, perteneciendo cada fichaje a un único miembro.




4. Miembro ↔ Consumo (Relación 1:N):


* Un miembro puede incurrir en múltiples consumos de bienes o servicios dentro del coworking, pero cada consumo se adjudica a un único miembro.
