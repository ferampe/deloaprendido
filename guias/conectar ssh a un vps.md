# Como conectar por SSH a un servidor VPS

Pare indicarle que nuestro servidor VPS que confie en nuestra conexion, debemos hacer la siguiente configuración.

1. Crear nuestra llave publica y privada en nuestro equipo local

```
ssh-keygen
```

Aqui saldra una mensaje para poner el nombre de la llave, en mi caso por ejemplo vps_server1.
Luego nos pedira una clave, es mas seguro configurarle clave pero la ventaja es que podamos confiar en el equipo, asi que se puede dejar en blanco, se tiene que dar ENTER 2 veces.

Luego copiar la clave, abrimos con el comando cat la llave publica

```
cat ~/.ssh/vps_server1.pub
```
Copiamos todo el contenido


Luego nos vamos a nuestro servidor VPS

nos dirigimos a la carpeta ~/.ssh y dentro creamos un archivo llamado authorized_keys y pegamos el codigo copiado de la llave publica local.

Ahora podemos conectarnos de ls siguiente manera desde nuestro equipo local

```
ssh root@ip_del_vps ~/.ssh/vps_serve1
```

Si queremos acortar este metodo de conexion, podemos crear un archivo config y conectarnos mas facilmente, dentro de la carpeta .ssh creamos un archivo llamado config sin ninguna extensión y ponemso los siguiente valores

```

ServerAliveInterval 120
ServerAliveCountMax 3

Host server1
        HostName ip_del_vps
        User root
        IdentityFile /home/user/.ssh/vps_server1
```

Ahora podemos conestarnos de la siguiente forma

```
ssh server1
```
