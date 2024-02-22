# Servidor de Bases de Datos

* Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen **mariadb** para que sea accesible desde el puerto 3306.

* Antes de arrancarlo visitar la página del contenedor en ***Docker Hub*** y establecer las variables de entorno necesarias para que:

  * La contraseña de root sea `root`
  * Crear una base de datos automáticamente al arrancar que se llame `prueba`
  * Crear el usuario `invitado` con la contraseña `invitado`

  ```bash
  #Crear el contenedor con las variables requeridas
  docker run --name bbdd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=prueba -e MYSQL_USER=invitado -e MYSQL_PASSWORD=invitado -d mariadb
  
  # Una vez tengamos esto, para comprobar que el contenedor está arrancado y funcionando ejecutamos lo siguiente:
  docker ps
  ```

  ![image-20240222092634874](./Servidor%20de%20bases%20de%20datos.assets/image-20240222092634874.png)

  ![image-20240222092729856](./Servidor%20de%20bases%20de%20datos.assets/image-20240222092729856.png)

Entregar un documento con las siguientes capturas de pantalla y los comandos empleados para resolver cada apartado:

* Captura de pantalla y documento que desde el navegador muestre el fichero `index.html`

  ```bash
  #Crear el fichero index.html
  nano index.html
  
  #Estructura HTML de ejemplo:
  <!DOCTYPE html>
  <html>
          <head>
                  <title>Mi pagina web</title>
          </head>
          <body>
                  <h1>Bienvenido a mi pagina web</h1>
                  <p>Esta es una pagina web de prueba creada para la tarea Docker</p>
          </body>
  </html>
  ```

  ![image-20240222093316442](./Servidor%20de%20bases%20de%20datos.assets/image-20240222093316442.png)

  ```bash
  #Creamos ahora el fichero .php para el siguiente apartado:
  nano mes.php
  
  #Escribimos el script .php
  <?php
  	echo date('F');
  ?>
  
  #Crear un contenedor con la imagen de php y apache
  sudo docker run -v /home/linux/Escritorio/TareaDocker_EV/Ejercicio1:/var/www/html -p 80:80 -d php:7.4-apache
  ```

  Una vez tengamos todo esto listo, buscamos en el navegador 'localhost' y ya se nos mostraría todo:

  ![image-20240222094039508](./Servidor%20de%20bases%20de%20datos.assets/image-20240222094039508.png)

  ![image-20240222094110380](./Servidor%20de%20bases%20de%20datos.assets/image-20240222094110380.png)

* Captura de pantalla y documento que desde un navegador se muestre la salida del script `mes.php`

  ![image-20240222094212719](./Servidor%20de%20bases%20de%20datos.assets/image-20240222094212719.png)

* Captura de pantalla y documento donde se vea el tamaño del contenedor `web` después de crear los dos ficheros.

  ![image-20240222095351307](./Servidor%20de%20bases%20de%20datos.assets/image-20240222095351307.png)

  ```bash
  #Te muestra una lista de todos los contenedores en ejecución junto con el tamaño de cada uno
  docker ps -s
  ```

  

* Captura de pantalla y documento donde desde un cliente de base de datos (instalado en tu ordenador) se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba (`show databases`). El acceso se debe realizar desde el ordenador que tenéis instalado Docker, <u>no</u> hay que acceder desde dentro del contenedor, es decir, no usar `docker exec`.

  Para poder mostrar la base de datos 'prueba' debemos de instalar un software llamado dbeaver-ce, el cual nos va a facilitar bastante todo.

  El software se encuentra en la snap de ubuntu (Ubuntu Software) y tiene este aspecto:
  ![image-20240222102648711](./Servidor%20de%20bases%20de%20datos.assets/image-20240222102648711.png)

  

  Una vez esté descargada, seguimos estos pasos:

  * Abre DBeaver
  * Haz clic en Database en la barra de menú y luego en New Database Connection
  * Selecciona el tipo de base de datos (por ejemplo MySQL) y haz clic en Next
  * En la pestaña Main, introduce 'localhost', en el campo 'Host', 3306 en el campo Port, el nombre de tu base de datos en el campo Database, root en el campo User Name y tu contraseña en el campo Password
  * Por último haz clic en Test Connection y si la conexión es exitosa, haz clic en Finish

  

  ![image-20240222102550032](./Servidor%20de%20bases%20de%20datos.assets/image-20240222102550032.png)

  

* Captura de pantalla y documento donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado.

  ```bash
  # Para comprobar que no se puede eliminar el contenedor ejecutamos lo siguiente:
  
  #Muestra los contenedores creados y arrancados
  sudo docker ps 
  
  #Comando para eliminar el contenedor con la imagen mariadb
  sudo docker rmi bbdd
  ```

  ![image-20240222104619059](./Servidor%20de%20bases%20de%20datos.assets/image-20240222104619059.png)

