# WORDPRESS CON DOCKER COMPOSE
En esta práctica vamos a explicar paso a paso cómo levantar un contenedor de docker con **Wordpress**

siguiendo la guía de los documentod de **docker**

El primer paso será pegar el codigo que nos proporcióna la guia en el archivo **YML**
# EXPLICACIÓN
 ## Configuración de Docker Compose

El siguiente fragmento es un archivo de configuración para Docker Compose, una herramienta que permite definir y ejecutar aplicaciones basadas en contenedores Docker. En este caso, se establece un entorno de desarrollo con dos servicios: una base de datos (db) y una aplicación de WordPress (wordpress).

### Servicio `db`

Este servicio configura una base de datos que utiliza el sistema de gestión de bases de datos MariaDB. A continuación se detallan los aspectos clave de la configuración:

- **`image: mariadb:10.6.4-focal`**: Se especifica la imagen de Docker que se usará para este servicio, que corresponde a MariaDB versión 10.6.4 basada en Ubuntu Focal Fossa.

- **`command: '--default-authentication-plugin=mysql_native_password'`**: Define el comando que se ejecutará al iniciar el contenedor. Establece la autenticación predeterminada del servidor MariaDB en "mysql_native_password".

- **`volumes`**: Mapea un volumen llamado `db_data` para almacenar los datos de la base de datos en `/var/lib/mysql`.

- **`restart: always`**: Configura el reinicio automático del contenedor en caso de fallo.

- **`environment`**: Define variables de entorno necesarias para la configuración de la base de datos, como la contraseña de root, el nombre de la base de datos, el usuario de la base de datos y la contraseña del usuario.

- **`expose`**: Expone los puertos 3306 y 33060 para que otros servicios dentro de la red de Docker puedan comunicarse con la base de datos.

### Servicio `wordpress`

Este servicio configura un contenedor para ejecutar una instancia de WordPress. Aquí están los detalles importantes de la configuración:

- **`image: wordpress:latest`**: Especifica la imagen de Docker para WordPress, utilizando la última versión disponible.

- **`volumes`**: Mapea un volumen llamado `wp_data` para almacenar los datos del sitio web de WordPress en `/var/www/html`.

- **`ports`**: Mapea el puerto 80 del host al puerto 80 del contenedor de WordPress, permitiendo que el sitio sea accesible desde el puerto 80 del servidor.

- **`restart: always`**: Configura el reinicio automático del contenedor en caso de fallo.

- **`environment`**: Define variables de entorno necesarias para la configuración de WordPress, incluyendo la información de la base de datos a la que se conectará WordPress.

### Volumenes

- **`db_data`**: Define un volumen llamado `db_data` utilizado para almacenar los datos de la base de datos MariaDB.

- **`wp_data`**: Define un volumen llamado `wp_data` utilizado para almacenar los datos del sitio web de WordPress.



