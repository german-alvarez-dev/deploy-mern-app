

# Paso a producción: servidor

Transferir tu API local a producción supone desplegar los archivos que la componen a un servidor externo, permitiendo así que las respuestas que ahora se emiten desde `http://localhost:5000/api` pasen a realizarse desde `https://planet-donuts-api.herokuapp.com/api`.
       
## Variables de entorno remoto

Debido a que el archivo `.env` no será desplegado, es necesario habilitar las variables de entorno en tu aplicación de Heroku.

1. Accede mediante la terminal al directorio raíz de tu servidor y asegúrate de que está enlazado al Git de servidor mediante `heroku apps:info --app planet-donuts-api`. Declara entonces cada una de las variables de entorno de tu archivo `.env` (excepto `DOMAIN`) con el comando `heroku config:set NOMBREVARIABLE=VALORVARIABLE --app nombreApp`. Ejemplo:

       heroku config:set CLOUDINARY_NAME=german-cloud --app planet-donuts-api
  
   No olvides sustituir `planet-donuts-api` por el nombre de tu aplicación servidor. Puedes consultar el valor de cualquier variable de entorno con el comando `heroku config:get NOMBREVARIABLE` 

2. Una vez hayas realizado este proceso para cada una, incluye la variable de entorno `DOMAIN` (la misma que en tu servidor local apunta a `http://localhost:3000`) pero con el valor `https://donuts-planet.heorkuapp.com`, es decir, apuntando a tu cliente remoto. Esto garantiza frente a CORS el acceso de tu cliente remoto a la API:

       heroku config:set DOMAIN=https://planet-donuts.herokuapp.com --app planet-donuts-api


## Paso a producción

Transferir los archivos a la aplicación de Heroku hará accesible tu API desde los dominios aceptados por CORS, a la vez que mantendrá todas sus funcionalidades en el entorno local donde puedes seguir desarrollando.

1. Accede mediante la terminal a la raíz de tu servidor, donde se encuentra el archivo `package.json`
2. Agrega los cambios y realiza un primer commit:
       
       git add .
       git commit -m "detalles asociados al commit"

3. Procede a la subida **desde el directorio raíz del proyecto**, donde se encuentran los directorios `/client` y `/server`:
       
       git subtree push --prefix=server heroku_server_master master

4. Una vez finalizado, comprueba la ausencia de errores en los logs mediante el comando `heroku logs --tail --app planet-donuts-api`
5. Abre tu aplicación en el navegador mediante `heroku open --app planet-donuts-api`, o tecleando la URL de la misma. Podrás comprobar si los endpoints de tu API mantienen su funcionalidad, ahora en remoto.

## Interfaz de usuario de Heroku

Puedes acceder a [tu cuenta de Heroku](https://dashboard.heroku.com/apps) mediante el navegador para comprobar detalles de tus aplicaciones: commits (pestaña *Activity*), variables de entorno (pestaña *Settings*), o incluso trabajar con la consola de Heroku en la esquina superior derecha *More => Console*.
