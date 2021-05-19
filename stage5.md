

# Paso a producción

Transferir tu aplicación a producción supone subir todos los archivos de tu directorio `/server` a Heroku. 

`
       git add .
       
       git commit -m "deploy"
       
       git subtree push --prefix=server heroku main
`
