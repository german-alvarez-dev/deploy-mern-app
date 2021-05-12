
# Registro y creación de aplicaciones para cliente y servidor en Heroku

El objetivo final que perseguimos con este proceso de pasar a producción (despliegue, _deploy_, etc) es disponer de dos aplicaciones independientes para el cliente y el servidor que conectaremos de la siguiente forma:

- Tu cliente de React se alojará en `https://myclient.herokuapp.com/` emitiendo las peticiones que procedan para consumir tu API.
- Tu API de Express responderá desde `https://myserver.herokuapp.com/`a cada petición con el JSON que proceda.

Heroku ofrece un servicio gratuito de alojamiento para aplicaciones basadas en NodeJS, pudiendo desplegar a sus servidores los archivos tanto de tu cliente como de tu servidor y obteniendo así una URL para cada uno que permitirá accederlos.

## Elige los nombres de tus aplicaciones 

Tú elegirás qué nombre deseas para tus aplicaciones, aunque en adelante usaremos para esta documentación las URLs `https://donuts-planet.herokuapp.com/`y `https://donuts-planet-api.herokuapp.com/` como ejemplo de cliente y servidor, respectivamente. 

Si tu proyecto se llama, por ejemplo, Restaurants Locator, sería ideal elegir un nombre como `restaurants-locator` para el cliente, lo que dará lugar a la URL https://restaurants-locator.herokuapp.com y `restaurants-locator-api` para el servidor, lo que dará lugar a la URL https://restaurants-locator-api.herokuapp.com.

No llames a tu aplicación `donuts-planet`. Este nombre sólo lo usaremos a efectos ejemplificativos.

## Registro 

Accede a [Heroku](https://www.heroku.com/) y realiza el proceso de registro con los datos personales.

Todos los demás pasos los realizaremos desde la terminal, por lo que no es necesario continuar ningún proceso en la página web.

## Instalación de Heroku CLI

Para hacer uso de los comandos de Heroku en tu terminal, es necesario realizar la instalación de la Interfaz de Línea de Comandos (CLI) de Heroku, accediendo a [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli) y siguiendo las instrucciones de instalación. 
Esto habilitará el uso de [todos los comandos de Heroku](https://devcenter.heroku.com/articles/heroku-cli-commands) en nuestra terminal.

## Inicio de sesión Heroku CLI

Para identificarnos en Heroku CLI y acceder a nuestra cuenta de Heroku desde la terminal, usaremos el comando `heroku login` siguiendo los pasos. 

Podremos cerrar la sesión cuando necesitemos mediante el comando `heroku logout`.

## Creación de aplicación cliente en Heroku

Alojaremos nuestro cliente de React en una aplicación de Heroku. Elige un buen nombre en este punto, ya que este será el que Heroku incluya en la URL pública con la que se podrá acceder a tu aplicación desde cualquier navegador. Es por ello que, si creases una aplicación de nombre `donuts-planet`, la URL final de tu producto sería:

    https://donuts-planet.herokuapp.com/
    
1. Accede mediante la terminal a la raíz de tu aplicación cliente `/client`, donde se encuentra su `package.json`, e introduce el comando necesario para crear la aplicación de Heroku y agregar el buildpack:

   ````
   heroku create donuts-planet -b https://github.com/mars/create-react-app-buildpack.git
   ````

2. Ahora enlaza el directorio `/client` en el que te encuentras al Git de la aplicación de Heroku:

   ````
   git remote add heroku_client_master https://git.heroku.com/xxx.git
   ````

3. Puedes comprobar en cualquier momento la aplicación de Heroku asociada a un Git mediante el comando:

   ````
   heroku info --app donuts-planet
   ````
 
Una vez hayas procedido, podrás acceder a esa URL. Recuerda que el número máximo de aplicaciones que podrás crear en una cuenta de Heroku sin indicar los datos de tu tarjeta de crédito es de 5 aplicaciones.

## Creación de aplicación servidor en Heroku

Usaremos de nuevo el comando `create` para crear nuestra aplicación donde alojaremos tu API de Express, pero esta vez lo haremos accediendo mediante la terminal al directorio raíz de la aplicación de servidor `/server`, donde se encuentra su `package.json`. 

En este caso no es necesario Buildpack, y no olvides cambiar también el nombre de la aplicación y del remoto: 

    heroku create donuts-planet-api
    
    git remote add heroku_server_master https://git.heroku.com/xxx.git
    
    heroku info --app donuts-planet-api
    
