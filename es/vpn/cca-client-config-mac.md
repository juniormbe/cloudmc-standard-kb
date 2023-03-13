---
title: "Configurar el cliente: macOS"
slug: configurar-el-cliente-macos
---

Este sistema operativo proporciona un cliente VPN IKEv2 nativo. Estos son los pasos para configurar una conexión VPN:

#### Instalar el certificado

1. Haz doble clic en el certificado que descargaste y guardaste en tu computadora (por ejemplo: **cloudmc-vpn.crt**) y agrégalo a tu llavero de **inicio de sesión** (*login* en inglés).
    ![Agregar certificado](/assets/Mac-1-Add-Certificate.png)
1. Abre la aplicación *Acceso a Llaveros*: *Finder > Aplicaciones > Utilidades > Acceso a Llaveros.app*
1. Haz clic en **Inicio de sesión** en el lado izquierdo, luego en *Certificados* en la parte superior derecha.
1. En el cuadro de búsqueda en la parte superior derecha de la ventana Acceso a Llaveros, busca el certificado que acabas de agregar.
    ![Acceso a llavero](/assets/Mac-2-Keychain.png)
1. Haz doble clic en el certificado y, en el primer cuadro desplegable que dice *Seguridad IP (IPsec)*, selecciona **Confiar siempre**. Ahora puedes cerrar la ventana.
    ![Confiar siempre en este certificado](/assets/Mac-3-Always-Trust.png)


#### Crear la conexión VPN

1. Abra *Configuraciónn del Sistema... -> Red*
1. Haz clic en el botón **+** para agregar una VPN
    - **Interfaz:** VPN
    - **Tipo de VPN:** IKEv2
    - **Nombre del servicio:** un nombre para tu conexión VPN (por ejemplo: cloudmc-vpn)
    ![Agregar VPN](/assets/Mac-4-Add-VPN.png)
1. Desde la izquierda, selecciona la conexión que acabas de crear e ingresa los siguientes detalles.
    - **Servidor:** dirección IP pública
    - **ID remoto:** igual que el servidor
    - **Identificación local:** déjelo en blanco
    - Haz clic en *Configuración de autenticación...*
        - **Nombre de usuario:** el nombre de usuario del usuario de VPN
        - **Contraseña** la contraseña de usuario de VPN
        ![Autenticar](/assets/Mac-5-Authentication.png)
1. Haz clic en *Crear*.
1. Marca la opción *Mostrar estado de VPN en la barra de menús* para acceder más fácilmente.
1. Ahora puedes conectarte a la VPN desde la barra de menú.
