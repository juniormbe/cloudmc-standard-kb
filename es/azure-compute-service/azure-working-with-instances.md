---
title: "Microsoft Azure: Trabajando con instancias"
slug: azure-trabajando-con-instancias
---


Para crear, modificar o eliminar una instancia, una cuenta con el rol *Usuario* debe ser miembro del entorno que contiene la instancia y también tener asignado el rol de entorno *Editor* o *Propietario*. Una cuenta con el rol de *Administrador* o superior puede crear, modificar o eliminar instancias en un entorno.

Para acceder a las instancias, ve a tu entorno de Microsoft Azure y haz clic en la pestaña **Instancias**.

<!-- Creating an environment - Advanced - Select region -->

### Agregar una instancia

Antes de agregar una instancia, debes tener al menos una red creada en tu entorno de Microsoft Azure.

    1. Haz clic en *Agregar instancia*.
    1. En la página *Agregar instancia*, ingresa los parámetros requeridos para la instancia deseada. Los costos estimados por hora y por mes aparecerán en el lado derecho.
    1. Selecciona la región en la que crear la instancia. La región no se puede cambiar una vez que se crea la instancia.
    1. Puedes optar por adjuntar una IP pública cuando se crea la instancia. Debe haber una dirección IP pública ya asignada y desanexada en la red donde se creará la instancia.
    1. Selecciona la subred para adjuntar a esta instancia.
    1. Haz clic en *Aplicar*. Aparecerá la pestaña **Instancias**. Cuando se haya creado la nueva instancia, aparecerá en la lista y estará en el estado **Iniciando**. Una vez que se haya aprovisionado la instancia, pasará al estado **En ejecución**.

### Obtener detalles de la instancia

1. En la pestaña **Instancias**, haz clic en la instancia. Esto te llevará a la página *Detalles* de la instancia.
    - En la pestaña **Instancias**, hacer clic en el nombre o la dirección IP de una instancia copiará esos datos en tu portapapeles y *no* te llevará a la página de *Detalles* de la instancia.
1. En la página *Detalles* de la instancia, al hacer clic en cualquier cadena, se copiará en el portapapeles.
1. Al hacer clic en *Discos*, accederá a la página de *Discos* de la instancia, donde puedes agregar, cambiar el tamaño, desconectar o eliminar discos en esta instancia. Consulta [Azure: Trabajar con discos](azure-working-with-disks.md) para obtener más información.

### Detener una instancia en ejecución

1. Desde la pestaña **Instancias**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona *Detener*.
1. Aparecerá un cuadro de diálogo solicitando confirmación para continuar. Haz clic en *Aplicar*.
1. La instancia entrará en el estado **Deteniéndose**. Una vez que la instancia haya dejado de ejecutarse, entrará en el estado **Detenido**.

### Inicio de una instancia detenida

1. En la pestaña **Instancias**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona *Iniciar*.
1. La instancia entrará en el estado **Iniciando**. Una vez que la instancia se está iniciando, entrará en el estado **En ejecución**.

### Eliminar una instancia

Se puede eliminar una instancia en cualquier estado. De forma predeterminada, el disco de arranque se elimina con la instancia (consulte a continuación), pero todos los discos de datos adjuntos a la instancia se desconectarán antes de eliminar la instancia y los discos permanecerán en el estado **Separado**.

1. Desde la pestaña **Instancias**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona *Eliminar*.
1. Aparecerá un cuadro de diálogo solicitando confirmación para continuar. Haz clic en *Aplicar*.
    - El cuadro de diálogo también ofrecerá la opción de eliminar el disco de arranque, que está seleccionado de forma predeterminada. Al anular la selección de esta casilla, se desconectará el disco de arranque antes de eliminar la instancia, y el disco permanecerá en el estado **Desconectado**.
1. La instancia entrará en el estado **Eliminando**. Cuando se complete la eliminación, la instancia se eliminará de la pestaña **Instancias**.
