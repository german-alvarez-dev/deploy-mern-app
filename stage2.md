# Paso a producción: base de datos

En este punto, tu aplicación de ExpressJS está conectada a una base de datos local de MongoDB que es accedida a través del método `connect()`de Mongoose y el string de conexión `mongodb://localhost/yourdatabase`. Esto es apto para un entorno local de desarrollo, pero no sería posible accederla desde un entorno de producción ya que, valga la redundancia, es *local*. Tu equipo no cumple ninguno de los requisitos de accesibilidad, capacidad o concurrencia de un servidor, entre otros. 

Realizaremos aquí las operaciones necesarias para transferir tu base de datos a la nube: exportar las colecciones locales de tu equipo a una base de datos remota (de producción) en [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) contra la que trabajarás en adelante.

## Conexión de Mongo Compass con la base de datos remnota

Mongo Compass permite la conexión tanto a las bases de datos locales como a un base de datos remota.

1. Abre Mongo Compass y en el menú superior selecciona *Connect => Connect to...*

2. Pega tu string de conexión de MongoDB Atlas y selecciona Connect. Estarás visualizando asi tu Cluster donde a continuación importaremos tus datos. 

## Exportación de base de datos local

MongoDB permite exportar como archivos JSON tus colecciones de una BBDD local. Estos pueden ser después importados a una BBDD remota. 

1. Accede mediante la terminal al directorio donde deseas crear los archivos JSON de tus colecciones.

2. Haz uso del comando `mongoexport` de MongoDB para exportarte la primera colección, siguiendo esta sintaxis:

   `mongoexport --collection=<collection> --db=<database> --out=<file>`
    
    - Sustituye `<collection>` por el nombre de la colección
    - Sustituye `<database>` por el nombre de la base de datos
    - Sustituye `<file>` por el nombre del archivo que creará MongoDB con tu colección, con extensión `.json`.

   Ejemplo:
 
     `mongoexport --collection=students --db=school --out=students-collection.json`

3. Comprueba cómo se ha creado el archivo con los datos y repite el proceso para colección, cambiando el nombre de la colección y el nombre del archivo en cada una.

## Importación de base de datos remota

MongoDB Atlas permite alojar y gestionar bases de datos en sus servidores a través del string de conexión obtenido tras el registro.

1. Accede mediante la terminal al directorio donde se encuentran los archivos JSON de tus colecciones.
2. Haz uso del comando `mongoimport` de MongoDB para importarte la primera colección, siguiendo esta sintaxis:

   `mongoimport --uri="<connectionstring>" --collection=<collection> --file=<file>`
    
    - Sustituye `<connectionstring>` por el string de conexión de MongoDB Atlas, entre comillas. 
    - Sustituye `<collection>` por el nombre de la colección que se creará, que debe ser igual al nombre de la colección local.
    - Sustituye `<file>` por el nombre del archivo donde se encuentran los datos de la colección.

   Ejemplo:
 
     `mongoimport --uri="mongodb+srv://your_user:your_pwd.ooyyy.mongodb.net/school" --collection=students --file=students-collection.json`
     
     Si ya habías importado antes esta colección, incluye el flag `--drop` para vaciarla previo a re-importarla y evitar que se acumulen los registros.

3. En Mongo Compass, actualiza la vista y comprueba que se ha creado tanto tu colección como los documentos que la conforman. Lo que estás viendo es ya tu base de datos remota.
4. Repite el proceso para cada colección, cambiando el nombre de la colección y el nombre del archivo en cada comando.


## Conexión de la base de datos remota con tu aplicación de ExpressJS

Despídete de tu base de datos local porque en adelante trabajarás contra la base de datos remota, tal y como hacías con la base de datos local. Todas las operaciones pueden realizarse de igual manera en una y otra, así como ambas pueden ser gestionadas a través de Mongo Compass como ya has visto.

1. Accede al archivo `.env` de tu aplicación de Express, y crea la variable de entorno `DB_REMOTE` con el string de conexión de MongoDB Atlas como valor. 

    `DB_REMOTE=mongodb+srv://your_user:your_pwd.ooyyy.mongodb.net/school`

2. Modifica el método `connect()` de tu aplicación, tomando como valor de conexión esta variable de entorno:

    ````javascript
    mongoose
       .connect(process.env.DB_REMOTE, ...
    ````

3. Reinicia el servidor y comprueba cómo sigue funcionando con normalidad, ahora contra MongoDB Atlas.
