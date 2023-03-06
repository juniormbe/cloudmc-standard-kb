---
title: "GCP: Trabajar con discos e instantáneas"
slug: gcp-trabajar-con-discos-e-instantaneas
---


Un **disco** es el almacenamiento que se presenta a una instancia como un dispositivo de bloque, que luego se puede montar y usar. Todas las instancias tienen un **disco de arranque**, que se puede cambiar de tamaño pero que no se puede separar de su instancia. Los discos persistentes adicionales se pueden crear, cambiar de tamaño, adjuntar o desconectar y eliminar.

Para crear, modificar o eliminar un disco, una cuenta con la función *Usuario* debe ser miembro del entorno que contiene la instancia y también tener asignada la función de entorno *Editor* o *Propietario*. Una cuenta con el rol de *Administrador* o superior puede crear, modificar o eliminar discos en un entorno.

Para acceder a los discos, navega hasta tu entorno de Google Cloud Platform y haz clic en la pestaña **Cómputo**, luego haz clic en *Discos*.

### Crea un disco

1. En la página *Discos*, haz clic en *Agregar un disco*. Serás llevado a la página *Agregar un disco*.
1. Ingresa un nombre para tu disco.
1. Selecciona la región y la zona donde deseas que esté disponible el disco. La región y la zona no se pueden cambiar una vez que se crea el disco. Un disco solo se puede adjuntar a una instancia en la misma región y zona.
1. Ingresa los parámetros para el tipo de disco, el tamaño del disco y el tamaño del bloque.
1. Haz clic en *Aplicar*. El disco se creará y aparecerá en la página *Discos* en el estado **listo**.

### Adjuntar un disco a una instancia

No se puede adjuntar un disco a una instancia cuando el disco ya se encuentra en el estado **adjunto**.

1. Desde la página *Discos*, haz clic en el menú **Acción** a la derecha del disco que desea adjuntar y haz clic en *Adjuntar*.
1. Aparecerá el cuadro de diálogo *Adjuntar*. Selecciona la instancia deseada de la lista emergente **Instancia**.
1. Elige si este disco debe presentarse a la instancia como un dispositivo grabable o como un dispositivo de solo lectura.
1. Elige si este disco debe conservarse si se elimina la instancia a la que está adjunto o si este disco debe eliminarse junto con la instancia adjunta.
1. Haz clic en *Aplicar*. El disco se adjuntará a la instancia y aparecerá en el estado **adjunto**. El disco ahora está listo para ser montado o particionado.

### Desconectar un disco de una instancia

**Nota:** Desconectar un disco de una instancia en ejecución puede provocar daños en el disco y pérdida de datos. Siempre desmonta correctamente el volumen desde el sistema operativo de la instancia antes de desconectar un disco.

1. Desde la página *Discos*, haz clic en el menú **Acción** a la derecha del disco que deseas desconectar y haz clic en *Separar*.
1. Aparecerá un cuadro de diálogo pidiendo confirmación para continuar. Haz clic en *Aplicar*.
1. El disco se desconectará y volverá al estado **listo**.

Alternativamente, se puede desconectar un disco de una instancia a través de la página *Detalles de la instancia*.

### Cambiar el tamaño de un disco

Se puede cambiar el tamaño de un disco para aumentar la cantidad de espacio de almacenamiento asignado. El espacio en disco solo se puede aumentar. No se admite la reducción del tamaño de un disco.

1. Desde la página *Discos*, haz clic en el menú **Acción** a la derecha del disco cuyo tamaño desea cambiar y haz clic en *Cambiar el tamaño*.
1. Aparecerá un cuadro de diálogo. En el cuadro de texto etiquetado **Tamaño del disco**, ingresa el número de gigabytes deseado para el disco.
1. Haz clic en *Aplicar*. Se cambiará el tamaño del disco y aparecerá una notificación cuando se complete la operación.
1. El sistema de archivos ahora se puede ampliar desde el sistema operativo de la instancia.

Como alternativa, se puede cambiar el tamaño de un disco si se adjunta a través de la página *Detalles de la instancia* de la instancia.

### Eliminar un disco

Un disco debe desconectarse antes de poder eliminarlo. Eliminar un disco es permanente. Esta acción no se puede deshacer.

1. Desde la página *Discos*, haz clic en el menú **Acción** a la derecha del disco que deseas eliminar y haz clic en *Eliminar*.
1. Aparecerá un cuadro de diálogo pidiendo confirmación para continuar. haz clic en *Aplicar*.
1. Este disco se eliminará y se eliminará de la lista de discos.

### Tomar una instantánea de un disco

Una instantánea de un disco es una copia instantánea de un disco en un momento dado.

1. Desde la página *Disco *, haz clic en el menú **Acción** a la derecha del disco que deseas capturar y haz clic en *Tomar instantánea*.
1. Aparecerá un cuadro de diálogo solicitando el nombre que se le dará a la instantánea. Haz clic en *Aplicar*.
1. Se tomará la instantánea y aparecerá en la página *Instantáneas* en el estado **Creando**.
1. Cuando se crea la instantánea, cambiará al estado **Cargando**. Cuando esté completo, aparecerá en el estado **Listo**.
