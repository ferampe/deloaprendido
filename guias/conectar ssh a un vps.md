# ¿Cómo conectarse a tu servidor VPS por ssh de forma segura y rapida?

Si trabajas con servidores remotos de manera frecuente, esta configuración te ayudara a tener una conexión segura y muy rapida, con llaves publicas y privadas SSH y un archivo config.

## Paso 1: Generar tu llave publica y privada en tu equioi local
Desde tu terminal local:
```
ssh-keygen
```


```
Generating public/private ed25523 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25523): vps_server1

```

```
Enter passphrase (empty for no passphrase):
```


> **Nota:** Puedes darle un nombre personalizado, por ejemplo: vps_server1.
Cuando te pida una contraseña, puedes dejarla en blanco para una conexión rápida desde un equipo confiable (aunque por seguridad es mejor usar una clave).

## Paso 2: Copiar la clave publica

```
cat ~/.ssh/vps_server1.pub
```
copia el codigo completo

## Paso 3: Agregar la clave publica al servidor VPS
Conectate a tu VPS crea (si no existe) la carpeta .ssh y el archivo authorized_keys
```
mkdir ~/.ssh
vim ~/.ssh/authorized_keys
```
Pega ahi la clave publica que copiaste.

## Paso 4: Conectate usando tu llave privada
Desde tu equipo local

```
ssh root@ip_del_vps ~/.ssh/vps_serve1
```

## Paso 5: Mejora tu agilidad de conexión
Podemos crear un archivo config y conectarnos de forma mas rapida.

Creamos un archivo config (sin extensión) dentro de la carpeta .ssh

```
vim config
```
añade lo siguiente, reemplaza ip_del_vps

```
ServerAliveInterval 120
ServerAliveCountMax 3

Host server1
        HostName ip_del_vps
        User root
        IdentityFile /home/user/.ssh/vps_server1
```

Luego solo conectate de la siguiente manera

```
ssh server1
```

