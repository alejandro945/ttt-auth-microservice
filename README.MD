<div align="center">
    <img src="https://miro.medium.com/max/1400/1*7R3X6gEz2RLRf2ypJTp79w.png">
</div>

# Auth Microservice ☄️

**The Microservice architecture**: Is an architectural style that structures an application as a collection of services that are:

- Highly maintainable and testable
- Loosely coupled
- Independently deployable
- Organized around business capabilities

Microservices approach is all about handling a complex system, but in order to do so, the approach introduces its own set of complexities and implementation challenges. which we will learn in the next part of this series!

# 🗺 Roadmap

| Resources | Description |
| ------------- | - |
| 🧶 **[Framework]** | New using Nest? Here's everything you need to know! |
| 🧅 **[Clean Architecture]** | Minimize the human resources required to build and maintain the required system. |
| 🎉 **[Functional Guide]** | Build production ML pipelines with simple functions. |

[Framework]: https://docs.nestjs.com/
[Clean Architecture]: https://www.freecodecamp.org/news/a-quick-introduction-to-clean-architecture-990c014448d2/
[Functional Guide]: https://github.com/alejandro945

## Nest as Backend Framework 🐱

### ¿Why Nest?  

Nest natively supports the microservice architectural style of development. In Nest, a microservice is fundamentally an application that uses a different transport layer than HTTP. But this does not only stay here Nest supports several built-in **transport layer** implementations, called transporters, which are responsible for transmitting messages between different microservice instances.

### Configuration ⚡️

**1-Package Installation**

```bash
npm i --save @nestjs/microservices
```

**2-Instantiate a Microservice**
```ts
import { NestFactory } from '@nestjs/core';
import { Transport, MicroserviceOptions } from '@nestjs/microservices';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.createMicroservice<MicroserviceOptions>(
    AppModule,
    {
      transport: Transport.TCP,
    },
  );
  app.listen();
}
bootstrap();
```

### Clean Architecture 🧼

![Screenshot](https://miro.medium.com/max/1400/1*0u-ekVHFu7Om7Z-VTwFHvg.png)
This diagram is taken from the official article by Robert C. Martin.

Each circle represents different areas of the software. The outermost layer is the lowest level of the software and as we move in deeper, the level will be higher. In general, as we move in deeper, the layer is less prone to change.

## Folder Structure

```bash
ttt-auth-microservice
  |- node_modules
  |- src
     |- application
        |- config
            |- environment.ts
        |- app.ts
     |- domain
        |- models
        |- use-cases
           |- impl
     |- infrastructure
        |- driven-adapters
           |- adapters
           |- providers
        |- entry-points
           |- api
     |- index.ts
  |- tests
     |- domain
     |- infrastructure
  .env
  package.json
  READMED.md
```