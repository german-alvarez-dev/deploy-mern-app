
# Registro y configuración base en MongoDB Atlas

MongoDB Atlas ofrece un servicio gratuito para alojar bases de datos en remoto, pudiendo accederlas a través de un string de conexión que sustituirá a tu actual `mongodb://localhost/db_local`

Si ya dispones de una cuenta de MongoDB Atlas y ya obtuviste un string de conexión previamente, accede a tu cuenta y ve al inicio de la web. Selecciona en la esquina superior derecha *New Project*, dale un nombre para crearlo y haz click sobre *Build a Cluster*. Retoma entonces este manual en el punto 2.

## Registro y configuración de Cluster

1. Acceder a [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) y comenzar el proceso de registro con los datos personales.<br/><br/>
2. En la siguiente pantalla, seleccionar *Skip*: 
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601658684/Captura_de_pantalla_2020-10-02_a_las_19.09.26.png" width="700"/><br/><br/>
3. En la siguiente pantalla, seleccionar *Shared Cluster* (compartido y gratuito):
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601658764/Captura_de_pantalla_2020-10-02_a_las_19.12.07.png" width="700"/><br/><br/>
4. En la siguiente pantalla, mantener AWS y seleccionar un servidor europeo. Seleccionar *Create Cluster*:
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601659031/Captura_de_pantalla_2020-10-02_a_las_19.17.01.png" width="700"/><br/><br/>

## Obtención del string de conexión

5. Una vez creado el Cluster, seleccionar *Connect*.<br/><br/>
6. En la sección *Add a connection IP address* de la ventana modal, seleccionar  *Allow Access from Anywhere*. 
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601659526/Captura_de_pantalla_2020-10-02_a_las_19.22.34.png" width="700"/><br/><br/>
  Veremos que el campo *IP Address* toma el valor `0.0.0.0/0` permitiendo asi el acceso a la base de datos desde cualquier IP.  
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601659536/Captura_de_pantalla_2020-10-02_a_las_19.25.28.png" width="700"/><br/><br/>
  Seleccionar *Add IP Address.* <br/><br/>
7. En la sección *Create a database user* de la ventana modal, rellenar el nombre de usuario para acceder a la base de datos y una contraseña. Seleccionar *Create database User*:
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601659726/Captura_de_pantalla_2020-10-02_a_las_19.27.33.png" width="700"/><br/><br/> 
8. A continuación, seleccionar *Choose a connection method*. <br/><br/>
9. Entre los métodos de conexión, seleccionar *Connect using MongoDB Compass*:
  <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601659855/Captura_de_pantalla_2020-10-02_a_las_19.30.13.png" width="700"/><br/><br/>
10. Copiar el string de conexión y modificarlo de la siguiente forma:
    - Sustituir `<password>` por la contraseña de conexión.
    - Sustituir `/test` por el nombre deseado para la base de datos.
    <img src="https://res.cloudinary.com/ironhack-german/image/upload/v1601660110/Captura_de_pantalla_2020-10-02_a_las_19.31.39.png" width="700"/><br/><br/>
11. Guardar el string de conexión para integrarlo tanto en la aplicación de ExpressJS como en MongoDB Compass.
