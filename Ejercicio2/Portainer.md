# Portoiner

1. IDescarga de Portainer

   ```bash
    $ docker pull portainer/portainer
   ```

![image-20240219194438402](./Portoiner.assets/image-20240219194438402.png)

2. Creamos un volumen Docker para la persistencia de datos:

   ```bash
   $ docker volume create portainer_data
   ```

   ![image-20240219194519678](./Portoiner.assets/image-20240219194519678.png)

3. Comprobamos que existe el volume

   ```bash
   $ docker volume ls
   ```

   ![image-20240219194546900](./Portoiner.assets/image-20240219194546900.png)

4. Iniciamos portainer

   ```bash
   $ docker run -d -p 9000:9000 --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
   ```

   - `-d`: Ejecutar el contenedor en segundo plano.
   - `-p 9000:9000`: Mapear el puerto 9000 del host al puerto 9000 del contenedor.
   - `--name portainer`: Asignar un nombre al contenedor.
   - `--restart always`: Reiniciar el contenedor automáticamente en caso de fallo o reinicio del sistema.
   - `-v /var/run/docker.sock:/var/run/docker.sock`: Proporcionar acceso al socket de Docker para gestionar los contenedores.
   - `-v portainer_data:/data`: Asociar el volumen creado al directorio `/data` dentro del contenedor.

​     5. Accedemos a Portainer

​	![image-20240219194645659](./Portoiner.assets/image-20240219194645659.png)

6. Muestra contenedores activos, para un contenedor, borra un contenedor

   - Contenedores activos

   ![image-20240220183858609](./Portainer.assets/image-20240220183858609.png)

   - Parar un contenedor lo selecionamos y cliclamos en stop

   ![image-20240220184143632](./Portainer.assets/image-20240220184143632.png)

   - Borrar contenedo, selecionamos y clicamos remove

   ![image-20240220184320618](./Portainer.assets/image-20240220184320618.png)

7. Muestra alguna operación con redes Docker

   - Creacion de una red con portainer

   ![image-20240220191747312](./Portainer.assets/image-20240220191747312.png)

   ![image-20240220191813006](./Portainer.assets/image-20240220191813006.png)

   - Creamos un contenedor nuevo con la image de mysql y vamos a utilizar la red creade llamada Mi_red

   ![image-20240220192411547](./Portainer.assets/image-20240220192411547.png)

   - Escojo red

   ![image-20240220192511576](./Portainer.assets/image-20240220192511576.png)

   - Implemento contenedor, para ello tuve que crea un equipo un usuario y darles permisos.

   ![image-20240220195957203](./Portainer.assets/image-20240220195957203.png)

   - Vemos el contendeor creado y est el red creada con ip 172.20.0.2

​	

![image-20240220201544213](./Portainer.assets/image-20240220201544213.png)

![image-20240220201951115](./Portainer.assets/image-20240220201951115.png)

8. Muestra alguna operación con volúmenes Docker

   - Creo un volumen llamado volumen1

     ![image-20240220202217650](./Portainer.assets/image-20240220202217650.png)

     ![image-20240220202354899](./Portainer.assets/image-20240220202354899.png)

   - Lo elimino

   ![image-20240220202600350](./Portainer.assets/image-20240220202600350.png)

   ![image-20240220202636531](./Portainer.assets/image-20240220202636531.png)

