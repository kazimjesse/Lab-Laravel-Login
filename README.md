<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://images.ctfassets.net/23aumh6u8s0i/7q90WhvMPGyPqhh5XfG15z/e77f3d9251c3c15102f6066159a7690d/login-page" width="600" alt="Laravel Login"></a></p>

## Introduccion

Este proyecto fue desarrollado con Laravel, un framework de PHP que implementa la arquitectura MVC (Modelo – Vista – Controlador).
En Laravel, la organización de carpetas facilita el desarrollo y el mantenimiento del código, separando responsabilidades claramente:

- Modelos (app/Models)
Aquí se definen las clases que representan las tablas de la base de datos.
Los modelos permiten interactuar con los datos usando Eloquent ORM.

- Controladores (app/Http/Controllers)
Contienen la lógica de la aplicación.
Se encargan de recibir las peticiones desde las rutas, procesar datos (consultando modelos si es necesario) y devolver una respuesta.

- Vistas (resources/views)
Son las plantillas que generan la interfaz de usuario.
Se escriben principalmente en Blade, el motor de plantillas de Laravel, para renderizar HTML dinámico.

- Rutas (routes/web.php y routes/api.php)
Definen los puntos de entrada a la aplicación (URLs).
Cada ruta se asocia a un controlador o a una función que maneja la petición.

## Objetivo del laboratorio

El objetivo principal de este laboratorio es construir una aplicación web básica de autenticación (login y registro de usuarios) con Laravel, aplicando la arquitectura MVC y utilizando migraciones para gestionar la base de datos.

De esta manera se busca:

1. Comprender la organización interna de un proyecto Laravel.

2. Aplicar buenas prácticas de separación de responsabilidades (MVC).

3. Aprender a gestionar bases de datos mediante migraciones y modelos.

4. Implementar un flujo de autenticación sencillo como parte de un sistema real.

## Prerrequisitos: (ecosistema de desarrollo del lab)

- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" width="30"/> **PHP** versión 8.0 o superior  
- <img src="https://getcomposer.org/img/logo-composer-transparent2.png" width="30"/> **Composer** última versión estable  
- <img src="https://laravel.com/img/logomark.min.svg" width="30"/> **Laravel Installer** o crear proyecto con `laravel new` / `composer create-project`  
- <img src="https://www.wampserver.com/favicon.ico" width="30"/> **WampServer** (Entorno de desarrollo local)  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apache/apache-original.svg" width="30"/> **Servidor web: Apache**  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" width="30"/> **Base de datos: MySQL**  
- <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" width="30"/> **Editor de código: Visual Studio Code**

## Base de datos

En este laboratorio se utilizó MySQL, el gestor de base de datos incluido en WAMP. Laravel permite la conexión a distintos motores de base de datos mediante el archivo .env, donde se configuran los parámetros de conexión.

La configuracion del .env sobre la base de datos
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=lab2_login
DB_USERNAME=root
DB_PASSWORD=

## Aspectos de Laravel en torno a la Base de Datos

Laravel utiliza migraciones y Eloquent ORM para interactuar con la base de datos:

- Migraciones
Son archivos de control de versiones que permiten crear, modificar o eliminar tablas de manera estructurada. Cada migración se guarda en la carpeta database/migrations.
Esto facilita que todo el equipo de desarrollo pueda replicar la misma estructura de base de datos sin necesidad de exportar e importar manualmente.

- Modelos
Se encuentran en la carpeta app/Models. Cada modelo representa una tabla de la base de datos y permite trabajar con los registros como objetos de PHP.

- Seeders y Factories
Pueden utilizarse para poblar la base de datos con datos de prueba.

#### php artisan migrate
Ejecutar las migraciones y crear las tablas en la base de datos

## Instalación de dependencias y configuración del entorno

Para la correcta ejecución del laboratorio, se realizaron los siguientes pasos:

### 1. Instalación de Laravel
Se instaló el instalador de Laravel de forma global y posteriormente se creó el proyecto:

composer global require laravel/installer
laravel new nombre_del_proyecto

### 2. Configuración del archivo .env
Se ajustaron las variables de entorno relacionadas a la base de datos, servidor y claves de aplicación.
Luego se limpiaron y cachearon las configuraciones:

php artisan config:clear
php artisan config:cache

### 3. Migraciones de base de datos
Se ejecutaron las migraciones incluidas por defecto para la creación de tablas iniciales:

php artisan migrate

### 4. Dependencias de autenticación en Laravel
Se instalaron las dependencias necesarias para la autenticación con Laravel UI, configurando plantillas de autenticación con Bootstrap:

composer require laravel/ui
php artisan ui bootstrap
php artisan ui bootstrap --auth

### 5. Configuración de frontend
Se instalaron las dependencias de Node.js y se compiló el frontend con Vite:

npm install
npm run dev

### 6. Levantamiento del servidor local
Finalmente, se levantó el servidor de desarrollo de Laravel:

php artisan serve

## Dificultades encontrada y soluciones
Aquí tienes el texto con las correcciones gramaticales, de estilo y de puntuación para mejorar la claridad y formalidad del informe:
•	Dificultad 1: Error de Certificados SSL. El principal problema fue un error con el SSL y los certificados de seguridad, manifestado como: "In CurlDownloader.php line 390: curl error 60 while downloading https://repo.packagist.org/packages.json: SSL certificate problem: unable to get local issuer certificate". Este error indicaba que no se reconocía el archivo cacert.pem, el cual contiene los certificados.
o	Solución: Inicialmente, se intentó solucionar el problema descargando el archivo cacert.pem y modificando las líneas openssl.cafile y curl.cainfo en el archivo php.ini para incluir la dirección correcta del certificado. Dado que esta acción no resolvió el problema, la solución final fue desactivar el antivirus por completo.
•	Dificultad 2: Configuración de la Base de Datos. En un inicio, la base de datos no se generaba al ejecutar el comando php artisan migrate. Esto se debió a que la configuración de la base de datos en el archivo .env estaba comentada y, por defecto, el framework utilizaba SQLite.
o	Solución: Se descomentó la configuración de la base de datos en el archivo .env y se cambió el motor predeterminado a MySQL.

## Referencias

Video tutorial de la profesora Irina Fong: https://www.youtube.com/watch?v=GZMGyYNq3hE
Video tutorial para resolver el problema con el SSL y certificaciones: https://www.youtube.com/watch?v=yzsokU5M6t0
Video tutorial para subir la carpeta del laboratorio de visual studio a GitHub: https://www.youtube.com/watch?v=2hcjEB-Mn7M

## Footer

Este laboratorio ha sido desarrollado por el estudiante de la Universidad Tecnológica de Panamá:

Nombre: Kazim Jesse
Correo: kazim.jesse@utp.ac.pa
Curso: 1SF-131
Instructor del Laboratorio: Irina Fong
Fecha de Ejecucion del laboratorio: 30/9/2025
Fecha de Entrega establecida por el docente: 29/9/2025
