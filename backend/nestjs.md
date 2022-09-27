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

- Express

```ts
const app = await NestFactory.create<NestExpressApplication>(AppModule);
```

- Fastify

```ts
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

### Generate controller

```shell
nest g controller cats
```

### Routing

- Use **@Controller('cats')** before class to define CatsController.
- Use **@Get('findAll')** before method to define route /cats/findAll.

### Request object

- Use **@Req()** before parameter to access Express Request Object.  
  Example:
  ```ts
  findAll(@Req() request: Request): string {
    return 'This action returns all cats';
  }
  ```
- We can use dedicated decorators instead of whole [Express Request Object](https://expressjs.com/en/api.html#req).
  - **@Next()**: next
  - **@Session()**: req.session
  - **@Query(key?: string)**: req.query/req.query[key]
  - **@Body(key?: string)**: req.body/req.body[key]
- We also use **@Res()** before parameter to access [Express Response Object](https://expressjs.com/en/4x/api.html#res).

### Resource

Beside **@Get()**, we also have others HTTP method:

- **@Post()**.
- **@Put()**.
- **@Delete()**.
- **@All()**: Handle all method.

### Route parameters

Get dynamic data from request url. Ex: /cats/:id

```ts
@Get(':id')
findOne(@Param() params): string {
  console.log(params.id);
  return `This action returns a #${params.id} cat`;
}
```

Or:

```ts
@Get(':id')
findOne(@Param('id') id: string): string {
  return `This action returns a #${id} cat`;
}
```

### Asynchronicity
