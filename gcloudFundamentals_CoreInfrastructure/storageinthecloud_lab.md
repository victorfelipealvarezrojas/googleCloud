<p align="center">
  <a  href="https://lirp.cdn-website.com/aa0ef369/dms3rep/multi/opt/google-cloud-icon-400w.png" 
      target="blank" >
    <img src="https://lirp.cdn-website.com/aa0ef369/dms3rep/multi/opt/google-cloud-icon-400w.png" 
        width="300" 
        alt="Kotlin Logo" 
    />
</a>
</p>

## Descripción general

<p align="justify">
en este lab, creará un bucket de Cloud Storage y colocará una imagen en él. Además, configurará una aplicación que se ejecute en Compute Engine para utilizar una base de datos que administre Cloud SQL. También configurará un servidor web con PHP, un entorno de desarrollo web que es la base de un software de blogs muy conocido. Fuera de este lab, utilizará técnicas similares para configurar esos paquetes.

También configurará el servidor web para hacer referencia a la imagen del bucket de Cloud Storage.
</p>


## Objetivos
En este lab, aprenderá a realizar las siguientes tareas:

* Crear un bucket de Cloud Storage y colocar una imagen en él

* Crear una instancia de Cloud SQL y configurarla

* Conectarse a la instancia de Cloud SQL desde un servidor web

* Usar la imagen del bucket de Cloud Storage en una página web

#

 ## Tarea 1: Acceda a la consola de Google Cloud Platform (GCP).
 Para cada lab, obtendrá un nuevo proyecto de GCP y un conjunto de recursos sin costo por un tiempo determinado....
#


## Tarea 2: Implemente una instancia de VM del servidor web

  1._ En el menú de navegación () de la consola de GCP, haga clic en Compute Engine > Instancias de VM.

  2._ Haga clic en Crear instancia.

  3._ En la página Crear una instancia, escriba bloghost en Nombre.

  4._ En Región y Zona, seleccione la región y la zona que le asignó Qwiklabs.

  5._ En Tipo de máquina, acepte el valor predeterminado.

  6._ En Disco de arranque, si la imagen que se muestra 
       no  es Debian GNU/Linux 9 (stretch), haga clic en Cambiar y seleccione Debian GNU/Linux 9 (stretch).

  7._ Deje los valores predeterminados de Identidad y acceso a la API sin modificar.

  8._ En Firewall, haga clic en Permitir tráfico HTTP.

  9._ Haga clic en Herramientas de redes, discos, seguridad, administración, usuario único para abrir esa sección del diálogo.

  10._ Haga clic en Administración para abrir esa sección del diálogo.

  11._ Desplácese hacia abajo hasta la sección Automatización y, luego, ingrese la siguiente secuencia de comandos como el valor para la secuencia de comandos de inicio:

  ```bat
    apt-get update
    apt-get install apache2 php php-mysql -y
    service apache2 restart
  ```
> ⚠️ *Asegúrese de proporcionar esa secuencia de comandos como el valor del campo Secuencia de comandos de inicio. Si la coloca en otro campo de manera accidental, no se ejecutará cuando se inicie la instancia de VM.*

11._ Deje la configuración restante con sus valores predeterminados y haga clic en Crear.
	
> ℹ️ *La instancia puede tardar unos dos minutos en iniciarse y estar disponible por completo para su uso.*

12._ En la página Instancias de VM, copie las direcciones IP interna y externa de la instancia de VM bloghost en un editor de texto para usarlas más adelante en este lab.

#

## Tarea 3: Cree un bucket de Cloud Storage con la línea de comandos de gsutil

<p align="justify">
Todos los nombres de los depósitos de Cloud Storage deben ser únicos a nivel global. Para asegurarse de que el nombre del bucket sea único, en estas instrucciones, se le explicará cómo asignarle al bucket el mismo nombre que el ID de su proyecto de Cloud Platform, que también es único a nivel global.
</p>

<p align="justify">
Los depósitos de Cloud Storage se pueden asociar a una ubicación regional o multirregional: EE.UU., UE o ASIA. En esta actividad, asociará el bucket a la ubicación multirregión más cercana a la región y la zona que le asignó Qwiklabs o su instructor.
</p>

1._ En el menú Google Cloud Platform, haga clic en Activar Cloud Shell Activar Cloud Shell. Si aparece un cuadro de diálogo, haga clic en Continuar.

2._ Para mayor comodidad, ingrese la ubicación que eligió en una variable de entorno llamada LOCATION. Ingrese uno de estos comandos:

```
export LOCATION=US
```
O
```
export LOCATION=EU
```
O
```
export LOCATION=ASIA
```

3._ En Cloud Shell, la variable de entorno DEVSHELL_PROJECT_ID contiene el ID de su proyecto. Ingrese este comando para asignarle un nombre al bucket con el ID del proyecto:

```
gsutil mb -l $LOCATION gs://$DEVSHELL_PROJECT_ID
```
*Si se le solicita, haga clic en Autorizar para continuar.*

4._ Recupere una imagen de banner desde una ubicación de Cloud Storage de acceso público:

```
gsutil cp gs://cloud-training/gcpfci/my-excellent-blog.png my-excellent-blog.png
```

5._ Copie la imagen del banner en el bucket de Cloud Storage que acaba de crear:
```
gsutil cp my-excellent-blog.png gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png
```
6._ Modifique la Lista de control de acceso del objeto que acaba de crear, de modo que sea legible para todos los usuarios:

```
gsutil acl ch -u allUsers:R gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png
```

#

## Tarea 4: Cree la instancia de Cloud SQL

1._ en el menú de navegación (Menú de navegación) de la consola de GCP, haga clic en SQL.

2._ Haga clic en Crear instancia.

3._ En la opción Elegir un motor para la base de datos, seleccione MySQL.

4._ En ID de instancia, escriba blog-db y en Contraseña raíz, ingrese una contraseña de su elección.

> ℹ️ *elija una contraseña que recuerde. No es necesario ocultarla, ya que utilizará mecanismos de conexión a los que no tienen acceso todos los usuarios.*

5._ Seleccione Zona única y configure la región y zona que asignó Qwiklabs.

> ℹ️ *Son la misma región y zona en las que inició la instancia bloghost. Para lograr un mejor rendimiento, ubique al cliente y la base de datos cerca.*

6._ Haga clic en Crear instancia.
> ℹ️ *Espere a que termine de implementarse la instancia. Esto tardará unos minutos.*

7._ Haga clic en el nombre de la instancia, **blog-db**, para abrir su página de detalles.

8._ En la página de detalles de las instancias de SQL, copie la dirección IP pública de la instancia de SQL en un editor de texto para usarla más adelante en este lab.

9._ Haga clic en el menú **Usuarios** ubicado en el lado izquierdo y, luego, en **AGREGAR CUENTA DE USUARIO**.

10._En **Nombre de usuario**, escriba blogdbuser.

11._ En **Contraseña**, ingrese una contraseña de su elección. Recuérdela.

12._ Haga clic en **AGREGAR** para agregar la cuenta de usuario a la base de datos.

> ℹ️ *Espere a que se cree el usuario.*

13._ Haga clic en la pestaña Conexiones y, luego, en Agregar red.

> ℹ️ *Si se le ofrece la opción de elegir entre una conexión IP privada y una IP pública, elija IP pública para los fines de este lab. La función IP privada estaba disponible en versión beta cuando se redactó este lab.*

> ℹ️ *Es posible que el botón Agregar red esté inhabilitado si aún no se completó el proceso de creación de la cuenta de usuario.*

14._ En **Nombre**, escriba web front end.

15._ En **Red**, ingrese la dirección IP externa de la instancia de VM **bloghost**, seguida de /32.

El resultado se verá como el siguiente ejemplo:

```sh
35.192.208.2/32
```

> ℹ️ *Asegúrese de utilizar la dirección IP externa de la instancia de VM seguida de /32. No use la dirección IP interna de la instancia de VM. No utilice la dirección IP de muestra de este ejemplo.*

16._ Haga clic en Listo para finalizar el proceso de definición de la red autorizada.

17._ Haga clic en Guardar para guardar el cambio de configuración.

> ℹ️ *Nota: Si aparece el mensaje Hay otra operación en curso, espere unos minutos hasta que se muestre una marca de verificación verde en blog-db para guardar la configuración.*

#

## Tarea 5: Configure una aplicación en una instancia de Compute Engine para utilizar Cloud SQL

1._ En el menú de navegación (Menú de navegación), haga clic en Compute Engine > Instancias de VM.

2._ En la lista de instancias de VM, haga clic en SSH en la fila de la instancia de VM bloghost.

3._ En la sesión SSH, en bloghost, cambie el directorio de trabajo a la raíz del documento del servidor web:

```sh
cd /var/www/html
```
4._ Use el editor de texto nano para modificar un archivo llamado index.php:

```sh
sudo nano index.php
```

5._ Pegue el siguiente contenido en el archivo:
```html
<html>
<head><title>Welcome to my excellent blog</title></head>
<body>
<h1>Welcome to my excellent blog</h1>
<?php
    $dbserver = "CLOUDSQLIP";
    $dbuser = "blogdbuser";
    $dbpassword = "DBPASSWORD";
    // In a production blog, we would not store the MySQL
    // password in the document root. Instead, we would store it in a
    // configuration file elsewhere on the web server VM instance.
    $conn = new mysqli($dbserver, $dbuser, $dbpassword);
    if (mysqli_connect_error()) {
            echo ("Database connection failed: " . mysqli_connect_error());
    } else {
            echo ("Database connection succeeded.");
    }
?>
</body></html>
```

> ℹ️ *Más adelante, insertará la dirección IP de su instancia de Cloud SQL y la contraseña de la base de datos en este archivo. Por ahora, deje el archivo sin modificar.*

6._ Presione Ctrl + O y, luego, Intro para guardar el archivo editado.

7._ Presione Ctrl + X para salir del editor de texto nano.

Reinicie el servidor web:


```sh
sudo service apache2 restart
```
9._ Abra una pestaña nueva del navegador web y pegue la dirección IP externa de la instancia de VM bloghost seguida de /index.php en la barra de direcciones. La URL se verá de la siguiente manera:

```sh 
35.192.208.2/index.php
```


> ℹ️ *Asegúrese de usar la dirección IP externa de la instancia de VM seguida de /index.php. No use la dirección IP interna de la instancia de VM. No utilice la dirección IP de muestra de este ejemplo.*

Cuando cargue la página, verá que su contenido incluye un mensaje de error que comienza con las siguientes palabras:


```sh 
Database connection failed: ...
```


> ℹ️ *Este mensaje aparece porque aún no ha configurado la conexión de PHP en su instancia de Cloud SQL.*

10._ Regrese a la sesión SSH en bloghost. Use el editor de texto nano para volver a modificar el archivo index.php.

```sh
sudo nano index.php
```

11._ En el editor de texto nano, reemplace CLOUDSQLIP por la dirección IP pública de la instancia de Cloud SQL que anotó antes. Deje las comillas del valor en su lugar.

12._ En el editor de texto nano, reemplace DBPASSWORD por la contraseña de la base de datos de Cloud SQL que definió antes. Deje las comillas del valor en su lugar.

13._ Presione Ctrl + O y, luego, Intro para guardar el archivo editado.

14._ Presione Ctrl + X para salir del editor de texto nano.

15._ Reinicie el servidor web:

```sh
sudo service apache2 restart
```

16._ Regrese a la pestaña del navegador web en la que abrió la dirección IP externa de la instancia de VM bloghost. Cuando cargue la página, aparecerá el siguiente mensaje:

```sh
Database connection succeeded.
```

> ℹ️ *En un blog real, el estado de conexión de la base de datos no será visible para los visitantes del blog. En su lugar, solo el administrador debería gestionar la conexión de la base de datos.*

#

## Tarea 6: Configure una aplicación en una instancia de Compute Engine para utilizar un objeto de Cloud Storage

1._ En la consola de GCP, haga clic en Cloud Storage > Navegador.

2._ Haga clic en el bucket con el mismo nombre de su proyecto de GCP.

3._ En este depósito, hay un objeto llamado my-excellent-blog.png. Copie la URL que obtiene del ícono de vínculo que aparece en la columna Acceso público de ese objeto o junto a las palabras “Vínculo público”, si se muestran.


> ℹ️ *Si no ve el ícono de vínculo ni las palabras "Vínculo público", intente actualizar el navegador. Si aún no ve el ícono de vínculo, regrese a Cloud Shell y confirme que se haya llevado a cabo con éxito su intento de cambiar la Lista de control de acceso del objeto con el comando gsutil acl ch.*

4._ Regrese a la sesión SSH en su instancia de VM bloghost.

5._ Ingrese este comando para configurar su directorio de trabajo en la raíz del documento del servidor web:

```sh
cd /var/www/html
```

6._ Use el editor de texto nano para modificar el archivo index.php:
```sh
sudo nano index.php
```

7._ Use las teclas de flecha para mover el cursor a la línea que contiene el elemento h1. Presione Intro para abrir una línea de visualización en blanco nueva y, luego, pegue la URL que copió antes en la línea.

8._ Pegue esta marca HTML justo antes de la URL:

```sh
<img src='
```

9._ Coloque una comilla simple de cierre y un corchete angular de cierre al final de la URL:

```sh
'>
```

La línea resultante se verá como el siguiente ejemplo:
```html
<img src='https://storage.googleapis.com/qwiklabs-gcp-0005e186fa559a09/my-excellent-blog.png'>
```

El resultado de estos pasos es colocar la línea que contiene ```<img src='...'>``` justo antes de la que contiene ```<h1>...</h1>```.

10._ Presione Ctrl + O y, luego, Intro para guardar el archivo editado.

11._ Presione Ctrl + X para salir del editor de texto nano.

12._ Reinicie el servidor web:

```
sudo service apache2 restart
```

13._ Regrese a la pestaña del navegador web en la que abrió la dirección IP externa de la instancia de VM bloghost. Cuando cargue la página, verá que su contenido ahora incluye una imagen de banner.



¡Felicitaciones!
