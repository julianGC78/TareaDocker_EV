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

   ![image-20240219190616513](/home/linux/snap/typora/86/.config/Typora/typora-user-images/image-20240219190616513.png)

3. Comprobamos que existe el volume

   ```bash
   $ docker volume ls
   ```

   ![image-20240219190832639](/home/linux/snap/typora/86/.config/Typora/typora-user-images/image-20240219190832639.png)

4. Iniciamos pontainer

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

​	![image-20240219192529885](/home/linux/snap/typora/86/.config/Typora/typora-user-images/image-20240219192529885.png)

![image-20240219193106187](/home/linux/snap/typora/86/.config/Typora/typora-user-images/image-20240219193106187.png)
