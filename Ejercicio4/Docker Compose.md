# Docker Compose

##### Desplegar la aplicación cmatrix utilizando docker-compose.

1. Captura de pantalla y documento donde se vea el fichero docker-compose.yaml .

   - Creamos el archivo `docker-compose.yaml`, en la linea command ejecutamos ese comando por que tubimos pron¡blemas con otras imagenes, esta es la imagen oficial de ubuntu

   ![image-20240221200508538](./Docker%20Compose.assets/image-20240221200508538.png)

   - ejecutamos este comando para crear el contenedor

     ```bash
     $ docker-compose up -d
     ```

   ![image-20240221200212110](./Docker%20Compose.assets/image-20240221200212110.png)

2. Captura de pantalla y documento donde se vea la aplicación funcionando. Se valorará conseguir el efecto Greenrain .

   - Arrancas la app y lo ejecutamos en una terminal

     ```bash
     $ docker ps
     $ docker exec -it cmatrix_container /bin/bash
     $ cmatrix
     ```

   ![image-20240221201348485](./Docker%20Compose.assets/image-20240221201348485.png)

   ![image-20240221201429283](./Docker%20Compose.assets/image-20240221201429283.png)

3. Explicar brevemente cómo funciona esta aplicación.

   - Es una aplicación que muestra una simulación de la matriz de código en la terminal. Estas son algunas de las caracteristicas que puedes aplicar a cmatrix.

     1. Puedes cambiar el color: green, red, blue, white, yellow, cyan, magenta and black.

        ```bash
        sudo apt-get install man-db
        ```

        ![image-20240221203220454](./Docker%20Compose.assets/image-20240221203220454.png)

     2. Velociodad de la matriz

        ```bash
        cmatrix -u 2
        ```

     3. Cambiar el estilo de la matriz

        ```bash
        cmatrix -o 2
        ```

        



