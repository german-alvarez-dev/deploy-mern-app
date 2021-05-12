# Deploy a Heroku

## Objeto del documento

Describir el proceso para deplegar a producción en [Heroku](https://www.heroku.com/) + [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) una MERN Stack app con cliente [`create-react-app`](https://create-react-app.dev/docs/getting-started/) y API [ExpressJS](https://expressjs.com/).

## Objetivo del deploy

**Base de datos**: hacer el paso a producción de la base de datos local a una base de datos remota en MongoDB Atlas:

- Realizar el registro en MongoDB Atlas y crear la base de datos remota (stage 1)
- Exportar los datos de la base de datos local e importaros en la base de datos remota (stage 2)

**Aplicación Heroku**: crear en Heroku la aplicación remota donde desplegar cliente y API:

- Realizar el registro en Heroku y crear la aplicación remota (stage 3)

**Setup en sevidor y _biuld_ en cliente**: configurar el servidor para retornar un `index.html` e integrar un _build_ realizado a partir del cliente:

- _TO-DO_

**Paso a producción**: realizar el paso a producción de la aplicación local a la aplicación remota:

- _TO-DO_

## Fases de paso a producción

- Stage 1: [Registro en MongoDB Atlas y configuración base](https://github.com/german-alvarez-dev/deploy-mern-app/blob/main/stage1.md)
- Stage 2:  [Paso a producción: base de datos](https://github.com/german-alvarez-dev/deploy-mern-app/blob/main/stage2.md)
- Stage 3:  [Registro en Heroku y creación de aplicación remota](https://github.com/german-alvarez-dev/deploy-mern-app/blob/main/stage3.md)
- Stage 4:  _PENDING_
- Stage 5:  _PENDING_
- Stage 6:  _PENDING_

