# Ejercicio 3 - Contenedores en red

1. Crea una red bridge redbd

   ```bash
   docker network create --driver bridge redbd
   ```

   

2. Crea un contenedor con una imagen de mariaDB que estará en la red redbd . Este contenedor se
  ejecutará en segundo plano, y será accesible a través del puerto 3306. (Es necesario definir la
  contraseña del usuario root y un volumen de datos persistente)

  ```bash
  docker run --name mariadb --network=redbd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -v volumenred:/var/lib/mysql -d mariadb
  ```

  

3. Crear un contenedor con Adminer que se pueda conectar al contenedor de la BD

   ```bash
   docker run --name adminer --network=redbd -p 8080:8080 -d adminer
   ```

   

4. Comprobar que el contenedor Adminer puede conectar con el contenedor mysql abriendo un
  navegador web y accediendo a la URL: http://localhost:8080

  ![image-20240223173839509](./Contenedores%20en%20red.assets/image-20240223173839509.png)

  Rellenamos con los siguientes datos:
  ![image-20240223173919124](./Contenedores%20en%20red.assets/image-20240223173919124.png)

  ![image-20240223173938796](./Contenedores%20en%20red.assets/image-20240223173938796.png)

Entregar los siguientes Captura de pantalla y documento s y los comandos empleados para resolver cada
apartado:

* Captura de pantalla y documento donde se vean los contenedores creados y en ejecución

  ```bash
  sudo docker ps
  ```

  ![image-20240223174203444](./Contenedores%20en%20red.assets/image-20240223174203444.png)

  

* Captura de pantalla y documento donde se vea el acceso a la BD a través de la interfaz web de Adminer

  ![image-20240223173839509](./Contenedores%20en%20red.assets/image-20240223173839509.png)

  ![image-20240223174059325](./Contenedores%20en%20red.assets/image-20240223174059325.png)

  

* Captura de pantalla y documento donde se vea la creación de una BD con la interfaz web Adminer

  ![image-20240223174357110](./Contenedores%20en%20red.assets/image-20240223174357110.png)

  ![image-20240223174430247](./Contenedores%20en%20red.assets/image-20240223174430247.png)

* Captura de pantalla y documento donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD

  ![image-20240223174624879](./Contenedores%20en%20red.assets/image-20240223174624879.png)

* Borrar los contenedores la red y los volúmenes utilizados

  ```bash
  docker rm -f mariadb adminer
  docker network rm redbd
  docker volume rm volumenred
  ```

  Comprobamos que lo ha eliminado correctamente:

  ![image-20240223174903380](./Contenedores%20en%20red.assets/image-20240223174903380.png)
