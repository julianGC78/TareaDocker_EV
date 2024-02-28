# Imagen con Dockerfile

1. Creación inicial del contenedor - documenta los pasos hasta el borrado del mismo

   - Crear cuenta de Docker Hub

     ![image-20240223092928553](./Imagen%20con%20Dockerfile.assets/image-20240223092928553.png)

   - Archivo index.html

     ![image-20240223201136196](./Imagen%20con%20Dockerfile.assets/image-20240223201136196.png)

   - Crear archivo php, la creo en la misma carpeta del ejercicio 5

     ```bash
     $ nano mes-php
     ```

     ![image-20240223201511351](./Imagen%20con%20Dockerfile.assets/image-20240223201511351.png)

   - Creamos Contenedor con imagen

     ```bash
     $ docker run -d --name web -p 8000:80 -v /home/linux/Documentos/TareaDocker_EV/Ejercicios5:/var/www/html php:7.4-apache
     ```

     ![image-20240223210341599](./Imagen%20con%20Dockerfile.assets/image-20240223210341599.png)

     ![image-20240223211558213](./Imagen%20con%20Dockerfile.assets/image-20240223211558213.png)

   - Entramos en el navegado con localhost:8000

     ![image-20240223210544717](./Imagen%20con%20Dockerfile.assets/image-20240223210544717.png)

   - Mostramos el script con el mes actual

     ![image-20240223210648534](./Imagen%20con%20Dockerfile.assets/image-20240223210648534.png)

   - Borrar contenedor, primero paramos y luego borramos

     ```bash
     $ docker stop web
     $ docker rm web
     ```

     ![image-20240223211710379](./Imagen%20con%20Dockerfile.assets/image-20240223211710379.png)

2. Bloque de código con el Dockerfile

   - Creamos archivo Dokerfile en ejercicio 5

     ```bash
     $ nano Dokerfile
     ```

     ![image-20240223213044922](./Imagen%20con%20Dockerfile.assets/image-20240223213044922.png)

     ![image-20240223213017850](./Imagen%20con%20Dockerfile.assets/image-20240223213017850.png)

3. Captura de pantalla y documento donde se vea el comando que crea la nueva imagen.

   ```bash
   $ docker build -t my-php-web .
   ```

   ![image-20240223213952495](./Imagen%20con%20Dockerfile.assets/image-20240223213952495.png)

4. Captura de pantalla y documento donde se vea la imagen subida a tu cuenta de Docker Hub.

   - Iniciamos sesión en Docker

     ```bash
     $ docker login
     ```

     ![image-20240223230019784](./Imagen%20con%20Dockerfile.assets/image-20240223230019784.png)

   - Etiquetamos la imagen con nuestro nombre de usuario

     ```bash
     $ docker tag my-php-web juliangc24/my-php-web
     ```

     ![image-20240223230710704](./Imagen%20con%20Dockerfile.assets/image-20240223230710704.png)

   - subimos la imagen a nuestra cuenta Docker hub

     ```bash
     $ docker push juliangc24/my-php-web
     ```

     ![image-20240223230957462](./Imagen%20con%20Dockerfile.assets/image-20240223230957462.png)

     ![image-20240223231252329](./Imagen%20con%20Dockerfile.assets/image-20240223231252329.png)

5. Captura de pantalla y documento donde se vea la bajada de la imagen - por parte de otra persona del
     grupo - y la creación de un contenedor.

     Para ello, creamos un usuario:

     ```bash
     sudo adduser olai sudo
     docker pull juliangc24/my-php-web
     ```

     ![image-20240226095118085](./Imagen%20con%20Dockerfile.assets/image-20240226095118085.png)

```
sudo docker run -d --name web2 -p 8001:80 juliangc24/my-php-web
sudo docker ps
```

![image-20240226095326403](./Imagen%20con%20Dockerfile.assets/image-20240226095326403.png)



6. Captura de pantalla y documento donde se ve el acceso al navegador con el sitio servidor

   ![image-20240226095540630](./Imagen%20con%20Dockerfile.assets/image-20240226095540630.png)
