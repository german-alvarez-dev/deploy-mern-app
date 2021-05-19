# Configuración de cliente y servidor para producción

Tu aplicación de Express debe retornar un archivo `index.html` desde su directorio `/public`, donde React creará la SPA que conformará el cliente. Para ello, es necesario configurar el servidor a este efecto, así como deshabilitar la gestión de errores 404 y 500 que, en adelante, será asumida por React.


## Variables de entorno en cliente

El cliente debe tomar, para todos los servicios, el base URL `http://localhost:5000/api` durante el trabajo en local, mientras que la versión de prducción debe apuntar a `https://donuts-planet.herokuapp.com/api`.

Para esto usaremos [las variables de entorno de Create React App](https://create-react-app.dev/docs/adding-custom-environment-variables/). Modifica los scripts de React en el `package.json`, incluyendo la misma variable para que apunte a una u otra URL base según el entorno:

````json
 "scripts": {
    "start": "REACT_APP_BASE_URL=http://localhost:5000/api react-scripts start",
    "build": "REACT_APP_BASE_URL=https://donuts-planet.herokuapp.com/api react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
````
Asimismo, recuerda modificar todos los servicios para que tomen `process.env.REACT_APP_BASE_URL` como BaseURL.


## Build de producción 

Tu aplicación de React debe ser comprimida a su versión de producción e incluida en el directorio `/public` del servidor:

1. Accede al directorio `/client` de tu proyecto y ejecuta el comando `npm run build`. Esto creará un directorio `/build` con la versión de tu cliente comprimida y lista para subir a producción. 
2. Mueve todo el contenido de este nuevo directorio a `/public` en tu servidor.


## Configuración de servidor

Para que tu servidor pueda enviar archivos al front, es necesario incluir el siguiente middleware al final de `app.js`, lo que permitirá enviar siempre el `index.html` que incluye el build de React al cliente:

       app.use((req, res) => res.sendFile(__dirname + "/public/index.html"));
  
Asimismo, la gestión de errores 404 y 500 ya está siendo asumida por los propios endpoints del servidor, por lo que el archivo `error-handlers.config.js` de tu directorio `/config` ya no es necesario. Elimina tanto el archivo como su requerimiento en `app.js`, e infórmate sobre [cómo gestionar errores 404 desde React Router](https://naveenda.medium.com/creating-a-custom-404-notfound-page-with-react-routers-56af9ad67807).

