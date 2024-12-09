---
title: Perfiles de usuario
draft: false
tags:
  - grapheneos
  - privacidad
  - perfiles_de_usuario
---

# **Propuesta para la Creación de 5 Perfiles en GrapheneOS**

El objetivo es establecer un entorno digital seguro y eficiente mediante la creación de cuatro perfiles en GrapheneOS, cada uno diseñado para un propósito específico, garantizando la privacidad y la separación de actividades.

Al implementar esta propuesta, el usuario podrá disfrutar de un entorno digital organizado y seguro, donde cada aspecto de su vida esté claramente separado y protegido. Esto no solo mejorará la productividad, sino que también garantizará la privacidad y la seguridad de la información personal, laboral y financiera.

Sin embargo, cada persona tiene diferentes necesidades en diferentes ámbitos y las posiblidades pueden ser infinitas (bueno hay un máximo de 31 usuarios + 1 invitado que se pueden crear) pero a lo que me refiero es que adaptes a tus casos de uso cada perfil. Hay gente que con dos usuarios ya le es necesario y habrá gente que necesite más o mas específicos.

Experimenta con ello, esto es solo una propuesta, pero ten en cuenta que contra mas usuarios tengas mas se te va a dificultar el dia a dia en tu mundo digital, a veces menos es mas.
## **Perfil 1: Propietario (Principal)**

Este será el perfil más utilizado para actividades diarias, navegación y entretenimiento.
En este perfil NO INSTALES los Google Play Services.

**Aplicaciones:** Siempre prioriza el uso de las web apps (uso de los servicios desde la web y no desde su app, en el artículo de Apps recomendadas explico como hacerlo.) 
Instalar solo aplicaciones de código abierto (FOSS) o que no requieran servicios de Google. Por ejemplo:

- Navegadores como Vanadium, Brave y Mullvad
- Aplicaciones de mensajería como Signal, Telegram, Session, etc 
- Aplicaciones de productividad como MuPDF, OnlyOffice...
- Aplicaciones de entretenimineto: NewPipe, RiMusic, AntennaPod

**VPN:** Mantener siempre activa una VPN como MullvadVPN o ProtonVPN para proteger la privacidad y la seguridad de la conexión.

**Hábito:** Fomentar el uso de aplicaciones FOSS y revisar regularmente las alternativas disponibles en https://alternativeto.net/

## **Perfil 2: Trabajo**

Este perfil estará dedicado exclusivamente a actividades laborales y comunicación profesional en el caso de que no tengamos un teléfono aparte para el trabajo.

**Aplicaciones**: Priorizar el uso de web apps y en la medida de lo posible evitar instalar los servicios de Google

**Seguridad:** Configurar el perfil para que solo las aplicaciones necesarias tengan acceso a datos relevantes (con Storage Scopes) y utilizar cifrado para proteger la información sensible.

## **Perfil 3: Banco** 

Perfil dedicado a la gestión de finanzas y servicios bancarios. Aquí muy probablemente tengas que instalar los servicios de Google para que funcionen correctamente algunas apps.

**Aplicaciones:** Instalar aplicaciones bancarias y de gestión de finanzas, que pueden requerir servicios de Google para su funcionamiento.

**Seguridad:** Asegurarse de que este perfil esté protegido con un método de bloqueo robusto y que se cierre sesión cuando no esté en uso.

**Cifrado:** Utilizar cifrado para proteger la información financiera almacenada.

## **Perfil 4: Tor (Privacidad Aumentada)**

Este perfil será para actividades que requieren un alto nivel de privacidad, como el uso de wallets de criptomonedas.

**Aplicaciones:** Instalar Orbot o InviZible para acceder enmascarar todo el tráfico del usuario

- **Navegación Segura:** Utilizar navegadores compatibles con Tor (como Tor Browser) para una navegación anónima.

- **Wallets Cripto:** Instalar aplicaciones de wallets de criptomonedas que prioricen la privacidad y la seguridad.

- **Cierre de Sesión Regular:** Implementar un hábito de cerrar sesión en este perfil al finalizar las actividades para mantener la seguridad.

## Perfil 5: Google

En este perfil podemos instalar los servicios de Google para poder usar esas apps que no encontramos alternativa y necesitan los GFS para funcionar.

**Recomendaciones:**

- Usar VPN

- Crear una cuenta de Google sin ningún dato personal:

	Para crear una cuenta de Google sin necesidad de ningún número de teléfono, desde el usuario con los Google Services instalados, vamos a Configuración/Contraseñas, llaves de acceso y cuentas/Agregar cuenta. Ahí y apodremos crear una cuenta de google sin proporcionar absolutamente ningún dato nuestro.  
	Durante la configuración de cuenta seleccionar las opciones para rechazar que guarden un registro de nuestra actividad.

- Crear y usar cuentas de los servicios sin dar ningún dato personal

## **Gestión de Datos y Seguridad**

- **Cifrado de Datos:** Asegurarse de que todos los perfiles utilicen cifrado para proteger la información almacenada.
- **Control de Notificaciones:** Configurar el reenvío de notificaciones solo en el perfil propietario, para evitar distracciones en los otros perfiles.
- **Revisión de Permisos:** Regularmente revisar los permisos de las aplicaciones en cada perfil para asegurarse de que no accedan a información innecesaria.

## Pasar archivos y portapapeles entre usuarios

**Inter Profile Sharing**: https://github.com/VentralDigital/InterProfileSharing/releases

Esta es una aplicación nativa y sencilla que permite enviar medios y texto a otro perfil de usuario de Android de manera tan fácil como compartir con otra aplicación. No requiere configuraciones complicadas ni trucos elaborados, y su código es de código abierto y gratuito. 

La aplicación busca resolver la dificultad de transferir archivos entre perfiles, evitando métodos poco prácticos como el uso de USB o aplicaciones de mensajería.



