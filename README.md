# Deploy a Heroku

## Objeto del documento

Describir el proceso para deplegar a producción en [Heroku](https://www.heroku.com/) + [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) una MERN Stack application con cliente [`create-react-app`](https://create-react-app.dev/docs/getting-started/) y servidor [ExpressJS](https://expressjs.com/).

## Objetivo del deploy

**Base de datos**: hacer el paso a producción de la base de datos local a una base de datos remota en MongoDB Atlas:

1. Realizar el registro en MongoDB Atlas y crear la base de datos remota (stage 1)
2. Exportar los datos de la base de datos local e importaros en la base de datos remota (stage 2)

**Aplicaciones cliente/servidor**: crear en Heroku las aplicaciones de cliente y servidor remotas donde desplegar las locales:

1. Realizar el registro en Heroku y crear las aplicaciones remotas (stage 3)

**Deploy cliente/servidor**: crear en Heroku las aplicaciones de cliente y servidor remotas donde desplegar las locales:

1. Desplegar aplicación de servidor en Heroku (stage 4)
2. Desplegar aplicación de cliente en Heroku (stage 5)

## Fases de paso a producción

- Stage 1: [Registro en MongoDB Atlas y configuración base](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage1.md)
- Stage 2:  [Paso a producción: base de datos](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage2.md)
- Stage 3:  [Registro en Heroku y creación de aplicaciones para cliente y servidor](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage3.md)
- Stage 4:  [Paso a producción: servidor](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage4.md)
- Stage 5:  [Paso a producción: cliente](https://github.com/german-alvarez-dev/deploy-react-express-app/blob/main/stage5.md)

