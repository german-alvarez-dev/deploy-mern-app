
# Registro en Heroku y creación de aplicación remota

El objetivo final que perseguimos con este proceso de pasar a producción (despliegue, _deploy_, etc) es disponer de una aplicación de servidor que, a la vez que mantiene sus funcionalidades REST, sirva un archivo `index.html` donde React realice la composición del cliente. La aplicación de React estará contenida en el directorio `/public` del servidor.

## Elige el nombre de tus aplicación

Tú elegirás qué nombre deseas para tu aplicación, aunque en adelante usaremos para esta documentación la URL `https://donuts-planet.herokuapp.com/` a modo de ejemplo. 

Si tu proyecto se llama, por ejemplo, Restaurants Locator, sería ideal elegir un nombre como `restaurants-locator`, lo que dará lugar a la URL https://restaurants-locator.herokuapp.com.

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

## Creación de aplicación en Heroku

Alojaremos nuestra aplicación local una aplicación remota de Heroku. Elige un buen nombre en este punto, ya que este será el que Heroku incluya en la URL pública con la que se podrá acceder a tu aplicación desde cualquier navegador. Es por ello que, si creases una aplicación de nombre `donuts-planet`, la URL final de tu producto sería:

    https://donuts-planet.herokuapp.com/
    
1. Accede mediante la terminal a la raíz de tu aplicación servidor `/server`, donde se encuentra su `package.json`, e introduce el comando necesario para crear la aplicación de Heroku y agregar el buildpack:

   ````
   heroku create donuts-planet
   ````

2. Ahora enlaza el directorio `/server` en el que te encuentras al Git de la aplicación de Heroku:

   ````
   git remote add heroku_server_master https://git.heroku.com/xxx.git
   ````

3. Puedes comprobar en cualquier momento la aplicación de Heroku asociada a un Git mediante el comando:

   ````
   heroku info --app donuts-planet
   ````
 
Una vez hayas procedido, podrás acceder a esa URL aunque, hasta que porcedas al deploy, permanecerá vacía.

Recuerda que el número máximo de aplicaciones que podrás crear en una cuenta de Heroku sin indicar los datos de tu tarjeta de crédito es de 5 aplicaciones.
