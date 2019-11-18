# Generar claves publica-privada y configurar servidor para conexión remota SSH sin contraseña.

1. Generar las llaves desde la parte del cliente:
Primero entras en el CMD de tu ordenador y escribes el comando `ssh-keygen`

![](images/doc4/doc_4_Windows10_keygen.jpg)


2. Cambias el nombre de la llave publica a authorized_keys

  ![](images/doc4/doc_4_llavesCreadas.jpg)

3. Subir la llave publica al servidor

  *Es recomendable instalar [Link a wingw10](http://mingw-w64.org/doku.php)*

  Cuando terminemos de crear la clave publica en el cliente el siguiente paso es exportarlos al servidor. Lo primero es entrar en el terminal del servidor y dirigirse al directorio `~/ssh.` con el siguiente comando.

    cd home/USUARIO/.ssh

Una vez hecho eso creamos un archivo donde se guardara la clave publica del usuario.

    touch authorized_keys

Ahora pasamos al terminal del cliente y entramos en el directorio `~/ssh.` con el siguiente comando.

    cd ~/.ssh

En este punto tenemos que exportar la llave publica al servidor con el siguiente comando. Con este comando lo manda directamente al archivo `authorized_keys`

    ssh-copy-id -i ~/.ssh/rsa.pub USUARIO@(ip del servidor)

Si entramos al archivo authorized_keys con el siguiente comando veremos la clave publica del cliente. Para verlo inserta el siguiente comando dentro de la carpeta `/ssh.`

    cat authorized_keys

Este sera el resultado.

![](images/doc4/doc_4_authorized_keys.png)

Si lo hemos hecho todo bien cuando nos conectemos al servidor no nos pedira la contraseña:

  ![](images/doc4/doc_4_comprobacion.png)
