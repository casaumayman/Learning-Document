# Overview
## First step
### Install NestJS
```shell
npm i -g @nestjs/cli
```
### Create new project
```shell
nest new project-name
```
main.ts is entry point
### Platform
* Express  
```js
const app = await NestFactory.create<NestExpressApplication>(AppModule);
```
* Fastify  
```js
const app = await NestFactory.create<NestExpressApplication>(AppModule);
```
### Running the application
```shell
npm run start #run only
npm run start:dev #run in dev mode
```
## Controllers
Controllers are responsible for handling incoming requests and returning responses to the client.
![controller](https://docs.nestjs.com/assets/Controllers_1.png)
### Routing
