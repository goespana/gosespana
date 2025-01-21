
## ¿Se puede usar Google Pay?

No se puede hacer que GPay/Wallet funcione en GrapheneOS y es una limitación en la medida en que Google Pay/Wallet requiere el cumplimiento completo de SafetyNet.

GrapheneOS puede pasar BasicIntegrity pero el OS no puede pasar ctsProfileMatch ya que eso requeriría que GrapheneOS sea whitelisted por Google. Google Pay/Wallet requiere ambos.

Fuente: https://discuss.grapheneos.org/d/475-wallet-google-pay

### Alternativa a GPay:

Algunos bancos permiten en su app poder hacer pagos con NFC. Tenemos constancia de que estos bancos lo permiten:
- BBVA
- Cajamar
- iCard
- EVO


Otra alternativa seria llevar la tarjeta en una funda como estas: https://www.amazon.com/Spigen-Slim-Armor-Designed-MP671/dp/B0BZ5PBKXP


## ¿El usuario propietario tiene acceso a alguna información del resto de usuarios?

No. Los perfiles de usuario son espacios de trabajo aislados con sus propias instancias de aplicaciones, datos de aplicación y datos del perfil (contactos, almacenamiento de medios, directorio de inicio, etc.). 
Las aplicaciones no pueden ver las aplicaciones de otros perfiles y solo pueden comunicarse con las aplicaciones dentro del propio perfil de usuario (con el consentimiento mutuo de la otra aplicación). 

Cada perfil de usuario tiene sus propias llaves de cifrado basadas en su método de bloqueo. Son una excelente opción para GrapheneOS, pero tienen mucho potencial para mejoras.

Fuente: https://grapheneos.org/features#improved-user-profiles

## ¿Puede una aplicación ver el contenido de otra aplicación o afectarla de alguna manera?
En GrapheneOS (y en Android en general), una aplicación no puede ver el contenido de otra aplicación ni afectarla directamente, salvo apps con el mismo id de grupo (apps del mismo developer) o apps de sistema.

Esto se debe a:

1. **Aislamiento de Aplicaciones**: Cada aplicación se ejecuta en su propio entorno aislado, lo que impide el acceso directo a los datos de otras aplicaciones.
    
2. **Permisos**: Las aplicaciones necesitan permisos específicos para acceder a ciertos datos. Sin estos permisos, no pueden interactuar con la información de otras aplicaciones.
    
3. **Sandboxing**: Las aplicaciones están "sandboxed", lo que significa que están restringidas en su capacidad para interactuar entre sí, mejorando así la seguridad y la privacidad del usuario.

Fuente: https://source.android.com/docs/security/app-sandbox

También hay que tener en cuenta que en el ecosistema de Android, la comunicación entre aplicaciones se realiza a través de mecanismos como "intents" y "binders". Los "intents" son mensajes que permiten que diferentes componentes de una aplicación, como actividades y servicios, se comuniquen entre sí. Por otro lado, los "binders" son una forma de comunicación inter-procesos que facilita la interacción entre distintas aplicaciones. Estos mecanismos son esenciales para el funcionamiento de las apps, pero también pueden plantear preocupaciones sobre la privacidad del usuario.

Cuando una aplicación no depende de servicios de Google, es menos probable que existan conexiones maliciosas entre ella y otras aplicaciones. Esto sugiere que las aplicaciones que no utilizan herramientas de seguimiento de Google podrían ser menos propensas a compartir información de manera no ética, lo que podría proteger mejor la privacidad del usuario.

Sin embargo, es importante tener en cuenta que cualquier aplicación que incluya un "tracker" tiene el potencial de comprometer la privacidad. Un "tracker" puede recopilar datos directamente del dispositivo sin necesidad de comunicarse con otras aplicaciones, lo que significa que puede operar de manera más oculta. Desde la perspectiva de un desarrollador de "trackers", no sería rentable intentar obtener datos de un número limitado de dispositivos que utilizan Google Play Services, ya que hay una base mucho más amplia de dispositivos Android disponibles.

Pero no todos los "trackers" son intrusivos o maliciosos. Algunas aplicaciones pueden enviar datos a sus propietarios sin necesidad de incluir un "tracker". Esto resalta la complejidad del ecosistema de aplicaciones y la necesidad de evaluar cada caso de manera individual. En resumen, la preocupación por la privacidad en el uso de aplicaciones debe ser matizada, considerando tanto la tecnología utilizada como el contexto en el que se emplea.


## Existe alguna alternativa mejor o parecida a GOS?

Tabla comparativa de diferentes ROMs:

https://eylenburg.github.io/android_comparison.htm


## Pixel con la pantalla en verde?
Es un problema de hardware, si puedes que te cambien el dispositivo en la tienda donde lo compraste.
https://support.google.com/pixelphone/thread/238632160/%C2%BFpor-qu%C3%A9-la-pantalla-de-mi-pixel-7-se-puso-verde?hl=es
