
Esta guía es para poder acceder a nuestros servicios locales de manera segura con el https (sin exponerlos a Internet, es decir, accediendo solo desde la LAN o conectándonos con VPN a la LAN).

Software usado en esta guía:
- [Adguard Home](https://github.com/AdguardTeam/AdGuardHome)
- [Nginx Proxy Manager (NPM)](https://github.com/NginxProxyManager/nginx-proxy-manager)
- [mkcert](https://github.com/FiloSottile/mkcert)

Antes de empezar, quiero aclarar algunos conceptos:

**DNS (Sistema de Nombres de Dominio)** es como la agenda de contactos de Internet. Cuando quieres visitar un sitio web, en lugar de recordar un número complicado (la dirección IP), solo escribes el nombre del sitio (como www.startpage.com) y el DNS se encarga de encontrar la dirección IP correcta para ti.

La **reescritura DNS** es una herramienta que nos permite cambiar la dirección que se asocia a un nombre de dominio. Esto es útil si tienes un servidor en casa (como Proxmox) y quieres acceder a diferentes servicios sin tener que recordar las direcciones IP locales, que pueden ser difíciles de manejar.

Un **proxy inverso** es como un portero en un edificio. Cuando alguien quiere entrar, el portero recibe la solicitud y decide a qué departamento (o servidor) enviar a esa persona. Esto ayuda a gestionar el tráfico y a mantener la seguridad, ya que el portero puede filtrar quién entra y quién no. 
**NPM** recibe las solicitudes de los clientes (navegadores, aplicaciones, etc.) dirigidas a los dominios que se han configurado (en este caso, `*.server.org`) y las redirige a los servicios internos que están corriendo en la red, utilizando la IP y el puerto que se ha especificado.

**Nginx Proxy Manager (NPM) maneja SSL** obteniendo un certificado que permite cifrar las conexiones, de modo que cuando un usuario accede a un servicio a través de NPM, la información que se envía y recibe está protegida. NPM desencripta la información para procesarla y luego la envía al servicio interno, y cuando el servicio responde, NPM vuelve a cifrar la información antes de enviarla de vuelta al usuario, asegurando así que la comunicación sea segura.

Explicado todo esto, vamos a configurarlo.

# Reescritura DNS en Adguard Home
Se presupone que ya tenemos una instalación de `Adguard Home`.

En el menú de arriba seleccionamos `Filtros/Reescrituras DNS`

![[AdguardHome_reescrituraDNS.png]]

Hacemos clic en el botón verde `Añadir reescritura DNS` (abajo a la izquierda de la foto) y nos aparecerá esta ventana flotante:

![[AdguardHome_añadir-reescritura-DNS.png]]

1. En la primera caja de texto añadiremos el nombre del dominio que queremos usar para todos los servicios (en mi caso `server.org`) y delante pondremos un (`*`)

	El asterisco ( * ) en la reescritura DNS se utiliza como un comodín. En el contexto de DNS, significa que cualquier subdominio de `server.org` será capturado por esa regla.
	Permite que una sola regla se aplique a todos los subdominios de un dominio específico.

	Por ejemplo, si tienes la entrada `*.server.org`, esto incluiría:

	- nextcloud.server.org
	- homeassistant.server.org
	- firefly.server.org
	- ...

	Esto es útil para redirigir o manejar múltiples subdominios sin tener que crear una entrada específica para cada uno. Sin embargo, no capturará el dominio base (en este caso, `server.org` sin subdominio).
	
2. En la Segunda caja de texto añadiremos la IP de nuestro Nginx Proxy Manager (NPM), en mi caso 192.168.8.200. 

	Al apuntar `*.server.org` a la IP de NPM, cualquier solicitud que llegue a un subdominio de `server.org` será redirigida a tu servidor NPM. Por ejemplo, si alguien intenta acceder a `nextcloud.server.org`, la solicitud se enviará a la IP de NPM.
	
No te preocupes si no lo entiendes, cuando veamos el apartado de Nginx Proxy Manager lo verás mas claro. Tu de momento configura esto y confía en mí.

Bien una vez configurado esto, nos vamos a NPM.

# Nginx Proxy Manager

Una vez iniciado sesión nos vamos al menú horizontal de arriba,  `Hosts/Proxy Hosts`

![[NPM_ProxyHosts.png]]

En la parte derecha hacemos clic en el boton `Add Proxy Host`

![[NPM_AddProxyHost.png]]

Se abrirá una ventana, en la pestaña `Details` deberemos rellenar la siguiente información:

- **Domain Names**: Aquí pondremos el nombre del servicio + .server.org
- **Scheme**: Normalmente lo dejaremos en http, pero algunos servicios como proxmox requieren https, eso depende de cada servicio.
- **Forward Hostname / IP:** Aquí pondremos la IP local de nuestro servicio (en este caso la IP de Nextcloud)
- **Forward Port**: Aquí pondremos el puerto que usa el servicio (en el caso de Nextcloud por defecto usa el 8080)
- **Activar** la opción **Block Common Exploits**

Ejemplo visual:

![[NPM_NewProxyHost.png]]

Una vez configurado esto, si guardamos veremos en proxy Host en la lista de `sources` y si visitamos `nextcloud.server.org` deberia redirigirnos correctamente a la interfaz web, sin embargo Nextcloud requiere que añadamos en el archivo `config.php` el dominio en la variable `trusted domains`. Si lo has echo con otro servicio deberia dejarte acceder sin tocar nada mas. 

Aquí te dejo el link de la documentación de Nextcloud para hacer esto: https://docs.nextcloud.com/server/29/admin_manual/installation/installation_wizard.html#trusted-domains

PD: si instalaste Nextcloud como yo en docker compose, este archivo estará en la carpeta nextcloud/cloud/config

**IMPORTANTE:** Debes tener configurado correctamente el DNS en el equipo desde el que quieras acceder al subdomnio, si no, no te va a redirigir correctamente. Básicamente tienes que ir a la configuración de Red, buscar la configuración DNS y poner la IP de tu AdguardHome.

SI eres como yo y accedes a los servicios desde fuera de casa con VPN, asegúrate de que la configuración del cliente también tiene la IP DNS correcta, la IP de AdguardHome en este caso.

Bien, hasta aquí hemos conseguido redirigir el subdominio para poder acceder al servicio sin tener que memorizar la IP de cada uno, ahora vamos a crear un certificado SSL para poder acceder con https.

# Crear certificado SSL local con mkcert

Bien, pues para crear un certificado SSL es muy sencillo, primero tenemos que instalar `mkcert`

## En Windows

1. **Instalar Chocolatey** (si no lo tienes):
   - Abre PowerShell como administrador y ejecuta:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

2. **Instalar mkcert**:
   - Una vez que Chocolatey esté instalado, ejecuta:

```powershell
choco install mkcert
```

3. **Instalar el CA (Autoridad Certificadora)**:
   - Ejecuta el siguiente comando en PowerShell:

 ```powershell
mkcert -install
```

## En macOS

1. **Instalar Homebrew** (si no lo tienes): Abre la terminal y ejecuta:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. **Instalar mkcert**: Ejecuta el siguiente comando en la terminal:

```bash
brew install mkcert
```

3. **Instalar el CA**: 

```bash
mkcert -install
```

## En Linux

Para instalar `mkcert` en Linux utilizando `apt`, puedes seguir estos pasos:

1. **Actualizar el sistema**: Abre una terminal y asegúrate de que tu lista de paquetes esté actualizada.

```
sudo apt update
```

2. **Instalar las dependencias necesarias**: `mkcert` requiere `libnss3-tools` para funcionar correctamente. Instálalo con el siguiente comando:

```
sudo apt install libnss3-tools
```

3. **Instalar `mkcert`**: A partir de ahora, puedes instalar `mkcert` directamente desde el repositorio de `snap` o descargarlo manualmente. Si prefieres usar `snap`, primero asegúrate de que `snapd` esté instalado:

```
sudo apt install snapd
```

Luego, instala `mkcert` usando `snap`:

```
sudo snap install mkcert
```

Si se ha instalado correctamente salta al **punto 6** de mas abajo para **Instalar la Autoridad Certificadora (CA)**

### Instalación manual de mkcert:

Si prefieres descargarlo manualmente, puedes hacerlo desde el [repositorio de mkcert en GitHub](https://github.com/FiloSottile/mkcert/releases). Descarga la versión adecuada para tu sistema y sigue las instrucciones de instalación.

**Instalar dependencias**: Asegúrate de tener `libnss3-tools` instalado. En Ubuntu, puedes instalarlo con:

```bash
sudo apt install libnss3-tools
```

**Descargar mkcert**: Ve a la [página de lanzamientos de mkcert en GitHub](https://github.com/FiloSottile/mkcert/releases) y descarga la versión adecuada para tu sistema. Para linux será algo asi como `mkcert-vx.x.x-linux-amd64`

#### Instalación de mkcert desde un archivo descargado

1. **Abre una terminal**.

2. **Navega al directorio donde descargaste el archivo**. Por ejemplo, si lo descargaste en la carpeta `Descargas`, puedes usar:

```
cd ~/Descargas
```

3. **Haz el archivo ejecutable**. Ejecuta el siguiente comando para darle permisos de ejecución (cambia el nombre del archivo por el que tu te hayas descargado):

```
chmod +x mkcert-vx.x.x-linux-amd64
```

4. **Mover el archivo a un directorio en tu PATH**. Para que puedas ejecutar `mkcert` desde cualquier lugar, mueve el archivo a `/usr/local/bin` (o a otro directorio que esté en tu PATH):

```
sudo mv mkcert-vx.x.x-linux-amd64 /usr/local/bin/mkcert
```

5. **Verifica la instalación**. Puedes comprobar que `mkcert` se ha instalado correctamente ejecutando:
   
```
mkcert --version
```

Salida esperada (Tiene que mostrarte la versión que hay instalada) 

```
v1.4.4
```

---

Una vez intalado mkcert, procedemos a:

6. **Instalar la Autoridad Certificadora (CA)**. Finalmente, ejecuta el siguiente comando para instalar la CA que `mkcert` necesita:

```
mkcert -install
```

Una vez hecho todo este proceso ya podemos crear un certificado para un dominio local con el siguiente comando:

```bash
mkcert *.server.org
```

Esto generará dos archivos:

`_wildcard.server.org-key.pem`
`_wildcard.server.org.pem`

Estos dos archivos guárdalos bien, son el certificado y la llave privada de certificado.

El certificado (`_wildcard.server.org-key.pem`) es el archivo que necesitarás instalar en tus dispositivos para que reconozcan el certificado SSL de tus nuevos subdominios.

### Instalación del certificado en NPM

Volvemos a NPM, nos dirigimos al menú SSL Certificates, hacemos clic en el botón `Add SSL Certificate` (en la parte derecha) y seleccionamos `Custom`

![[NPM_AddSSLCertificate.png]]

Ponemos un nombre al certificado y añadimos los dos archivos que hemos creado antes:

![[NPM_AddCustomCertificate.png]]

Volvemos a la ventana de Hosts/Proxy Hosts y hacemos clic en los tres puntitos verticales de la derecha del Proxy Host de `nextcloud.server.org` que hemos creado anteriormente, seleccionamos `Edit`:

![[NPM_EditProxyHost.png]]

Vamos a la pestaña SSL y seleccionamos el certificado que acabamos de añadir:

![[NPM_AñadirCertificadoSSL.png]]

Seleccionamos la opción Force SSL y guardamos

![[NPM_ForceSSL.png]]

Si hemos realizado todo correctamente deberíamos poder acceder a nuestro servicio con el subdominio y con el certificado SSL con el protocolo https y sin ninguna alerta de seguridad

![[Certificado_SSL_OK.png]]

