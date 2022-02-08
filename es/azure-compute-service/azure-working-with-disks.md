---
title: "Microsoft Azure: Trabajando con discos"
slug: azure-trabajando-con-discos
---


Un **disco** es un almacenamiento que se presenta a una instancia como un dispositivo de bloque, que luego se puede montar y usar. Todas las instancias tienen un disco de arranque, que se puede cambiar de tamaño pero que no se puede separar de su instancia. Se pueden crear, cambiar de tamaño, adjuntar o separar y eliminar discos adicionales.

Para crear, modificar o eliminar un disco, una cuenta con el rol *Usuario* debe ser miembro del entorno que contiene la instancia y también tener asignado el rol de entorno *Editor* o *Propietario*. Una cuenta con la función *Administrador* o superior puede crear, modificar o eliminar discos en un entorno.

Para acceder a los discos, ve a tu entorno de Microsoft Azure y haz clic en la pestaña **Discos**.

### Crear un disco

1. En la pestaña *Discos*, haz clic en *Agregar disco*. Accederás a la página *Agregar disco*.
1. Introduce un nombre para tu disco.
1. Selecciona la región en la que deseas que esté disponible el disco. La región no se puede cambiar una vez que se crea el disco. Un disco solo se puede adjuntar a una instancia en la misma región.
1. Ingresa los parámetros para el tipo de disco y el tamaño del disco.
1. Haz clic en *Aplicar*. Aparecerá la pestaña **Discos**. El disco se creará y aparecerá en el estado **Separado**.

### Adjuntar un disco a una instancia

Un disco se puede adjuntar solamente a una instancia cuando el disco está en el estado **Desconectado**. Además, debe existir al menos una instancia en la región donde se encuentra el disco.

1. Desde la pestaña **Discos**, haz clic en el menú **Acción** a la derecha del disco que deseas adjuntar y haz clic en *Adjuntar*.
1. Aparecerá el cuadro de diálogo *Adjuntar*. Selecciona la instancia deseada de la lista emergente **Instancia**.
    - De forma predeterminada, un disco se adjunta a una instancia con el número de unidad lógica (LUN) más bajo disponible en la instancia. Si se requiere un LUN personalizado para este disco, marca la casilla **LUN personalizado** y especifica qué LUN deseas asignar a este disco. El LUN elegido debe ser exclusivo de todos los demás discos conectados a la instancia.
1. Hagz clic en *Aplicar*. El disco se adjuntará a la instancia y aparecerá en el estado **Adjunto**. El disco ahora está listo para ser montado o particionado.

### Desconectar un disco de una instancia

**Nota:** Desconectar un disco de una instancia en ejecución puede provocar la corrupción del disco y la pérdida de datos. Siempre desmonta correctamente el volumen desde el sistema operativo de la instancia antes de desconectar un disco.

1. En la pestaña *Discos*, haz clic en el menú **Acción** a la derecha del disco que deseas desconectar y haz clic en *Desconectar*.
1. Aparecerá el cuadro de diálogo *Separar*, solicitando confirmación para continuar. Haz clic en *Aplicar*.
1. El disco se desconectará y volverá al estado **Desconectado**.

De manera alternativa, un disco puede separarse de una instancia a través de la página *Instance details*.

### Cambiar el tamaño de un disco o cambiar el tipo de disco

Se puede cambiar el tamaño de un disco para aumentar la cantidad de espacio de almacenamiento asignado. El espacio en disco solo se puede aumentar. No se admite la reducción del tamaño de un disco. Además, se puede cambiar el tipo de rendimiento del disco.

**Nota:** Si el disco está conectado a una instancia en ejecución, la modificación del disco reiniciará la instancia.

1. En la página *Discos*, haz clic en el menú **Acción** a la derecha del disco que deseas modificar y haz clic en *Editar*.
1. Aparecerá la página *Editar*.
1. Para cambiar el tipo de rendimiento del disco, selecciona la opción deseada de la lista emergente **Tipo**.
1. Para cambiar el tamaño del disco, mueve el control deslizante **Tamaño del disco** al número de gigabytes deseado para el disco.
1. Haz clic en *Aplicar*. El disco se modificará en consecuencia y aparecerá una notificación cuando la operación haya finalizado.
1. El sistema de archivos ahora se puede ampliar desde el sistema operativo de la instancia.

De manera alternativa, se puede cambiar el tamaño de un disco si se adjunta a través de la página *Discos* de la instancia.

### Eliminar un disco

Se debe desconectar un disco antes de poder eliminarlo. La eliminación de un disco es permanente. Esta acción no se puede deshacer.

1. Desde la pestaña **Discos**, haz clic en el menú **Acción** a la derecha del disco que deseas eliminar y haz clic en *Eliminar*.
1. Aparecerá un cuadro de diálogo solicitando confirmación para continuar. Haz clic en *Aplicar*.
1. Este disco se eliminará y se eliminará de la lista de discos.
