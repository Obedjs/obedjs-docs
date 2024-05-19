<!-- ## [Introduction](#introduction)

> obedjs is a lightweight framework built on top of Express.js for rapidly developing APIs with Node.js and Express. -->

## [Installation](#installation)

To get started, you can either scaffold the project with the Obedjs CLI, or clone a starter project (both will produce the same outcome).

To scaffold the project with the Obedjs CLI, run the following commands. This will create a new project directory, and populate the directory with the initial core ObedJs files and supporting modules, creating a conventional base structure for your project. Creating a new project with the Obedjs CLI is recommended for first-time users.

### Install the CLI

```bash
npm install -g obedjs-cli
```

### Create a new project

```bash
obedjs create my-new-project
```
### Alternatively

```bash  
git clone  https://github.com/Obedjs/obedjs.git project-name
cd my-new-project
npm install
```

## [Server](#server)

```bash
import express, { Application } from 'express';
import appRoutes from './routes/app/app.route';

const app: Application = express();

app.use(express.json());
app.use('/', appRoutes);

const PORT: number = parseInt(process.env.PORT || '3000', 10);

app.listen(PORT, () => {
  console.log(`ObedJs Listening on port ${PORT}`);
});

export default app;
```

### Run the server in development mode

```bash
npm run start:dev
```

### Run the server production mode

```bash
npm run start:prod

```

## [Basic Routing](#route)
Routing refers to how an application’s endpoints (URIs) respond to client requests. For an introduction to routing, see Basic routing.


```code
import { Router } from 'express';
import { AppController } from '../../controllers/app/app.controller';
import { AppService } from '../../services/app/app.service';

const router = Router();
const service = new AppService();
const controller = new AppController(service);

router.get('/', controller.getHello.bind(controller));


export default router;
```

## [Guide](#guide)

### [Controller](#controller)
Controllers are responsible for handling incoming requests and returning responses to the client.

```bash
npm run generate controller User
```
```code
router.get('/', controller.fetchAll.bind(controller));
router.update('/:id', controller.update.bind(controller));
router.delete('/:id', controller.delete.bind(controller));
router.post('/', controller.create.bind(controller));
```

### [Service](#service)

```bash
npm run generate service User
```

```code
export class AppService {
  public async getHello(): Promise<any> {
    return {
      message: "Hello obedjs"
    }
  }
}

```

### [Route](#route)

```bash
npm run generate route User

```

### [Resource](#resource)

```bash
npm run generate all User

```

### [Dto](#dto)

```bash
npm run generate dto SignUp

```

### [Middleware](#middleware)
Middleware is a function which is called before the route handler. Middleware functions have access to the request and response objects, and the next() middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

```bash
npm run generate middleware Auth
```

### [Configuration](#configuration)

```bash
npm run generate config Database
```

### [Logger](#logger)

Install the obedjs-logger package(is preinstall already)

```bash
npm i obedjs-logger
```

```code
import Logger, { LogLevel } from 'obedjs-logger';

const logger = new Logger(LogLevel.DEBUG, 'project.log');

logger.info('This is an info message');
logger.warn('This is a warning message');
logger.error('This is an error message');
logger.debug('This is a debug message');
```

### [Validation](#validation)

It is best practice to validate the correctness of any data sent into a web application. To automatically validate incoming requests, ObedJs make use of class-validator out-of-the-box

```bash
  npm i class-validator

```

### [Error Handling](#error-handling)

Error Handling refers to how Express catches and processes errors that occur both synchronously and asynchronously. Express comes with a default error handler so you don’t need to write your own to get started.


## [Advanced Usage](#advanced-usage)

### [Security](#security)
The list below enumerates the Express vulnerabilities that were fixed in the specified version update.

NOTE: If you believe you have discovered a security vulnerability in Obedjs, please see Security Policies and Procedures.

### [Production](#production)
#### Docker file setup

```bash
npm run generate docker Dockerfile
```

## Testing

### [Unit Test](#unit-test)

```bash
npm run test
```

### [E2E Test](#e2e-test)

```bash
npm run test:e2e
```
