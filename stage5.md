

# Paso a producción: cliente

Transferir tu aplicación de React a producción supone compilarla para desplegar los archivos que la componen a un servidor externo, permitiendo así que las peticiones que ahora se emiten desde `http://localhost:3000` pasen a realizarse desde `https://planet-donuts.herokuapp.com`.
       

## Variable de entorno remoto

En este punto, todos tus servicios de Axios apuntan al BaseUrl `process.env.REACT_APP_API_URL`. Si bien esta variable de entorno se encuentra declarada en el script de start, esta solo está vigente en local por lo que es necesario darla de alta en remoto para que apunte a la API remota, situada en `https://donuts-planet-api.herokuapp.con`. 

Esto permitirá que las peticiones que se realizan desde tus servicios en local sigan apuntando a `http://localhost:5000/api` mientras que en remoto apuntarán a `https://planet-donuts-api.herokuapp.com/api`.
 
1. Accede mediante la terminal al directorio raíz de tu cliente y asegúrate de que está enlazado al Git de cliente mediante `heroku apps:info --app donuts-planet`. Declara entonces una variable de entorno remoto en tu aplicación de Heroku:

       heroku config:set REACT_APP_API_URL=https://planet-donuts-api.herokuapp.com/api --app planet-donuts

   

## Paso a producción

Transferir los archivos a la aplicación de Heroku permitirá acceder tu cliente de React desde cualquier navegador, a la vez que mantendrá todas sus funcionalidades en el entorno local, donde puedes seguir desarrollando.

1. Accede mediante la terminal a la raíz de tu cliente, donde se encuentra el archivo `package.json`
2. Agrega los cambios y realiza un primer commit:
  ````
    git add .
    git commit -m "detalles asociados al commit" 
  ````
3. Procede a la subida **desde el directorio raíz del proyecto**, donde se encuentran los directorios `/client` y `/server`:
       
       git subtree push --prefix=client heroku_client_master master
       
4. Una vez finalizado, comprueba la ausencia de errores en los logs mediante el comando `heroku logs --tail --app planet-donuts`
5. Abre tu aplicación en el navegador mediante `heroku open --app planet-donuts`, o tecleando la URL de la misma. Podrás navegar a través de ella como lo haces en en entorno local.

## Interfaz de usuario de Heroku

Puedes acceder a [tu cuenta de Heroku](https://dashboard.heroku.com/apps) mediante el navegador para comprobar detalles de tus aplicaciones: commits (pestaña *Activity*), variables de entorno (pestaña *Settings*), o incluso trabajar con la consola de Heroku en la esquina superior derecha *More => Console*.
