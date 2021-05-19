

# Paso a producción

Transferir tu aplicación a producción supone subir todos los archivos de tu directorio `/server` a Heroku. Hazlo desde el directorio raíz del proyecto, donde se encuentran los subdirectorios `/client` y `/server`.

````
git add .
       
git commit -m "deploy"
       
git subtree push --prefix=server heroku_app_master main
````
