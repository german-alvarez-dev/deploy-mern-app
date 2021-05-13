# Retorno de aplicación React desde servidor 

Tu aplicación de Express debe retornar un archivo `index.html` desde su directorio `/public`, donde React creará la SPA que conformará el cliente. Para ello, es necesario configurar el servidor a este efecto, así como deshabilitar la gestión de errores 404 y 500 que, en adelante, será asumida por React.


## Build de producción 

Tu aplicación de React debe ser comprimida a su versión de producción e incluida en el directorio `/public` del servidor:

1. Accede al directorio `/client` de tu proyecto y ejecuta el comando `npm run build`. Esto creará un directorio `/build` con la versión de tu cliente comprimida y lista para subir a producción. 
2. Mueve todo el contenido de este nuevo directorio a `/public` en tu servidor.



## Configuración de servidor

Para que tu servidor pueda enviar archivos al front, es necesario incluir el siguiente middleware al final de `app.js`, lo que permitirá enviar siempre el `index.html` que incluye el build de React al cliente:

       app.use((req, res) => res.sendFile(__dirname + "/public/index.html"));
  
Asimismo, la gestión de errores 404 y 500 ya está siendo asumida por los propios endpoints del servidor, por lo que el archivo `error-handlers.config.js` de tu directorio `/config` ya no es necesario. Elimina tanto el archivo como su requerimiento en `app.js`.


## Paso a producción

