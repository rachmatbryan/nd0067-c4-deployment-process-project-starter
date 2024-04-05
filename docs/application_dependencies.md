# App Dependencies

This document outlines the dependencies and scripts used in the udagram application, which consists of a frontend and a backend.

## Frontend

The frontend of the application is built using the Ionic Framework with Angular. The dependencies and scripts are defined in the `package.json` file.

### Dependencies:

- `@angular/*`: The collection of Angular packages provides the framework for building the frontend application.
- `@ionic-native/*`: These packages are part of Ionic's native API system which allows access to native device functions.
- `@ionic/angular`: This is the Angular-specific package for Ionic.
- `core-js`: A modular standard library for JavaScript, providing polyfills for many ECMAScript features.
- `rxjs`: Library for reactive programming using Observables, making it easier to compose asynchronous or callback-based code.
- `zone.js`: An execution context for JavaScript, needed for Angular's change detection.

### DevDependencies:

- `@angular-devkit/*`, `@angular/cli`, `@angular/compiler-cli`, `@angular/language-service`: These packages are part of the Angular CLI used for building and serving the application during development.
- `@ionic/angular-toolkit`: Provides schematics and builders for Angular CLI projects that use Ionic.
- `@types/*`: TypeScript type definitions for various libraries.
- `@typescript-eslint/*`: TypeScript-specific linting rules for ESLint.
- `codelyzer`: A set of tslint rules developed for Angular and based on the guidelines from the Angular style guide.
- `jasmine`, `karma`: Testing framework and its associated test runner.
- `protractor`: End-to-end test framework for Angular and AngularJS applications.
- `ts-node`, `tslint`, `typescript`: TypeScript execution environment and linter, and the language itself.

### Scripts:

- `start`: Runs the application using the Angular CLI's server.
- `build`: Compiles the application and makes it ready for production.
- `test`: Runs the unit tests for the application using Karma and Jasmine.
- `e2e`: Executes end-to-end tests using Protractor.
- `lint`: Lints the application code using ESLint and Codelyzer.
- `deploy`: Deploys the application to AWS Elastic Beanstalk.

## Backend

The backend is a Node.js application with the following scripts defined for various operations:

### Scripts:

- `start`: Starts the server using the compiled JavaScript files from the TypeScript source.
- `start:dev`: Alias for `start`, used for clarity in a development environment.
- `tsc`: Runs the TypeScript compiler.
- `dev`: Starts the TypeScript Node.js development server with automatic restarts on file changes.
- `prod`: Compiles the TypeScript source to JavaScript and runs the server in production mode.
- `clean`: Removes the `www` build directory.
- `deploy`: Builds the application and deploys it to a specified Elastic Beanstalk environment.
- `build`: Installs dependencies, cleans the build directory, compiles TypeScript, copies necessary config files, and prepares the deployment archive.
- `test`: A placeholder for running tests, to be defined by the developer.

Note that the specific versions of dependencies and the exact scripts may vary based on the requirements and updates of the project. Always consult the `package.json` file for the most accurate and up-to-date information.
