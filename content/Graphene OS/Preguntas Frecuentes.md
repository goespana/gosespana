
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
En GrapheneOS (y en Android en general), una aplicación no puede ver el contenido de otra aplicación ni afectarla directamente. Esto se debe a:

1. **Aislamiento de Aplicaciones**: Cada aplicación se ejecuta en su propio entorno aislado, lo que impide el acceso directo a los datos de otras aplicaciones.
    
2. **Permisos**: Las aplicaciones necesitan permisos específicos para acceder a ciertos datos. Sin estos permisos, no pueden interactuar con la información de otras aplicaciones.
    
3. **Sandboxing**: Las aplicaciones están "sandboxed", lo que significa que están restringidas en su capacidad para interactuar entre sí, mejorando así la seguridad y la privacidad del usuario.

Fuente: https://source.android.com/docs/security/app-sandbox


## Existe alguna alternativa mejor o parecida a GOS?

Tabla comparativa de diferentes ROMs: 

https://eylenburg.github.io/android_comparison.htm


lalala