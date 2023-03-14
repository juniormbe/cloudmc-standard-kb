---
title: "Configurar el cliente: Ubuntu 18.04"
slug: configurar-el-cliente-ubuntu
---

Esta guía te ayudará a configurar la VPN de administración remota en Ubuntu utilizando el administrador de red, que está instalado de forma predeterminada en la versión de Desktop.

1. Instala los paquetes necesarios:
   - `sudo apt-get install strongswan network-manager-strongswan libcharon-extra-plugins`
1. Abre la aplicación *Configuración*, navega a la pestaña *Red* a la izquierda.
1. Haz clic en **+** junto a *VPN*.
1. Selecciona **IPsec/IKEv2 (strongswan)** como tipo de VPN.

![Diálogo de selección de VPN](/assets/Lx-1-Strongswan.png)

5. Ve a la pestaña *Identidad*.
5. Asigna un nombre a la VPN, por ejemplo: **cloud-vpn.cer**
5. En *Puerta de enlace*, el campo *Dirección* es la IP pública que se muestra en la página de configuración de VPN y *Certificado* es el archivo de certificado que se muestra en la página de configuración de VPN.
5. En *Cliente*, establece *Autenticación* en *EAP*.
5. Rellena los campos *Nombre de usuario* y *Contraseña*.
5. En *Opciones*, marca la casilla de verificación **Solicitar una dirección IP interna**.

![Página de configuración de VPN](/assets/Lx-2-Request-internal.png)

11. Opcionalmente, puedes ir a la pestaña *IPv4* y marcar **Usar esta conexión solo para recursos en su red**.
11. Haz clic en *Agregar* en la parte superior derecha de la ventana para guardar la configuración.


Ahora puedes habilitar la VPN desde la página *Red* o desde el widget de red en la parte superior derecha de la pantalla.
