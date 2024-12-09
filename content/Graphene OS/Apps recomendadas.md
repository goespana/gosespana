---
title: Apps recomendadas
draft: false
tags:
  - grapheneos
  - privacidad
---

En github hay un listado enorme de muchas alternativas a las apps mainstream que no respetan nuestra privacidad (https://github.com/pluja/awesome-privacy)

Pero ahí van algunas de las apps que hemos elegido en el grupo de telegram de GrapheneOS en español (unofficial). Anímate a entrar al grupo y enseñarnos alguna otra que te parezca interesante!

Grupo de telegram: https://t.me/grapheneosEsp

# Aplicaciones recomendadas

Para evitar rastreadores lo ideal es usar la app en su versión web, preferiblemente con un navegador como Brave que tiene un potente bloqueador.

¿Cómo hacemos esto?
En el navegador Brave, cuando abrimos una página web (por ejemplo Wallapop) abajo a la derecha veremos 3 puntitos en vertical. En el menú desplegable clicamos en la opción "Agregar a la pantalla principal".

![[APP version web2.png]]
# Tienda de Apps

**F-Droid:** [https://f-droid.org/es/](https://f-droid.org/es/)

F-Droid es un catálogo instalable de aplicaciones FOSS (Software Libre y de Código Abierto) para la plataforma Android.

**Aurora Store**: [https://aurorastore.org/]
Aurora Store es una alternativa gratuita de Google Play Store donde puedes descargar aplicaciones, actualizar las aplicaciones que ya tienes, recibir detalles sobre los rastreadores en la aplicación, ocultar tu ubicación, buscar aplicaciones y hacer mucho más.
# Gestionar actualizaciones de nuestras APPS
**Obtanium**: https://github.com/ImranR98/Obtainium

Obtainium nos permite instalar y actualizar aplicaciones directamente desde sus páginas de versiones, y recibir notificaciones cuando las nuevas versiones estén disponibles.

# Verificar autenticidad de las apps
**AppVerifier**: https://github.com/soupslurpr/AppVerifier

Es un visor y verificador de hash de certificados de firma de aplicaciones. Te permite verificar fácilmente que tus aplicaciones son genuinas con otros.

Tutorial: https://inv.nadeko.net/watch?v=IkrujqcM-9Y

# Gestor de contraseñas
Lo ideal es que gestionemos nosotros la base de datos de las contraseñas en lugar de cederla (aunque encriptada) a una empresa.

Por supuesto esto implica la responsabilidad de <u>realizar copias de seguridad</u> recurrentemente para evitar la perdida de las contraseñas.

Tenemos dos opciones:

1. Alojar el servicio en un servidor casero 

	- **Vaultwarden**: https://github.com/dani-garcia/vaultwarden

2. Usar una app offline (todo en local dentro de nuestro dispositivo)

	- **Keepass**: https://www.keepassdx.com/

# 2FA tokens de verificación
**Aegis Authenticator**: https://github.com/beemdevelopment/Aegis

Todo se guarda en local, IMPORTANTE guardar el código de recuperación que te da cada servicio cuando se crea el token 2FA (a mi me gusta apuntarlo en una libreta) y CREAR BACKUPS de la bóveda de Aegis y GUARDARLOS en otro dispositivo.

# Sincronizar archivos entre dispositivos
**Syncthing**: https://github.com/syncthing/syncthing

Syncthing es una aplicación que le permite sincronizar sus archivos en múltiples dispositivos. Esto significa la creación, modificación o eliminación de archivos en uno la máquina se replicará automáticamente en sus otros dispositivos.

Debido a que la app Syncthing ha dejado de dar soporte en Android (https://forum.syncthing.net/t/discontinuing-syncthing-android/23002), hemos encontrado este fork:

**Syncthing-Fork:** https://github.com/Catfriend1/syncthing-android

# Multimedia
- **NewPipe**: https://newpipe.net/

	App para ver videos de youtube de manera privada, sin iniciar sesión podemos seguir los canales, sin anuncios, reproducción del audio con el móvil bloqueado...

- **RiMusic**: https://rimusic.xyz/

	Una aplicación para Android de código abierto y multilingüe para reproducir música de YouTube Music

- **AntennaPod**: https://antennapod.org/

	AntennaPod es un reproductor de podcast completamente abierto. La aplicación es software libre y puedes suscribirte a cualquier canal RSS. 

# Mapas
## App de búsqueda:
**GMaps WV**: https://github.com/Divested-Mobile/Maps
Es una app WebView para usar Google Maps sin exponer su dispositivo. 

En GMaps WV podremos buscar el lugar donde queremos ir (también vale para buscar restaurantes y sus reseñas), sin embargo no se podrá usar como navegador. Para esto tenemos dos buenas alternativas:

## Apps de navegación:
- **Organic Maps**: https://organicmaps.app/es/

- **OsmAnd**: https://osmand.net/

Pero todos sabemos que el mejor buscador de lugares es Google, entonces tenemos que combinar ambas herramientas para beneficiarnos de sus resultados sin comprometer nuestra privacidad:

<u>¿Como usarlas de manera conjunta?</u>
Buscaremos el lugar donde queremos ir en GMaps WV, le daremos a "compartir" y seleccionaremos la app de navegación que tengamos (Organic Maps o  OsmAnd). Seguidamente se abrirá la app con el lugar seleccionado en GMaps WV y ya podremos iniciar la navegación.

# Notificaciones
**You Have Mail**: https://f-droid.org/packages/dev.lbeernaert.youhavemail/

App para notificaciones de email sin Google Play Services
Se recomienda tener el 2FA en el servicio de mail ya que deberemos introducir la contraseña en la app You Have Mail para poder recibir las notificaciones.

# Pasar archivos y portapapeles entre usuarios
**Inter Profile Sharing**: https://github.com/VentralDigital/InterProfileSharing/releases

Esta es una aplicación nativa y sencilla que permite enviar medios y texto a otro perfil de usuario de Android de manera tan fácil como compartir con otra aplicación. No requiere configuraciones complicadas ni trucos elaborados, y su código es de código abierto y gratuito. 

La aplicación busca resolver la dificultad de transferir archivos entre perfiles, evitando métodos poco prácticos como el uso de USB o aplicaciones de mensajería.

# Tiempo
**Breezy Weather**: https://github.com/breezy-weather/breezy-weather

Breezy Weather es una aplicación del clima que se centra en el diseño, ofreciendo una experiencia de usuario simple y limpia, animaciones suaves y un enfoque en Material Design, además de una gran capacidad de personalización.

# Videoconferencias
**Jitsi Meet**: https://github.com/jitsi/jitsi-meet

Jitsi Meet es un proyecto de código abierto que permite a los usuarios utilizar y desplegar plataformas de videoconferencia con calidad de video y características de vanguardia.

# Calendario
**Fossify Calendar**: https://github.com/FossifyOrg/Calendar

Fossify también tiene otras apps como un administrador de archivos, app de sms, de telefono, etc. Pero todo esto ya lo tiene GrapheneOS, lo único que el falta de serie es un calendario. Podéis probar también el resto de apps, pero con las nativas de GOS es suficiente.
