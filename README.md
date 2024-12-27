# GitLab B.V. Node.js Express Project

This repository is for a Node.js Express project. The project includes examples of how to set up an Express server, use docker, and test using Supertest and Mocha. The project is built to be run in a Docker environment. In the sections below, you will find the steps to setup and run the project.

## Developer Certificate of Origin and License
By contributing to GitLab B.V., you accept and agree to the following terms and conditions for your present and future contributions submitted to GitLab B.V. Except for the license granted herein to GitLab B.V. and recipients of software distributed by GitLab B.V., you reserve all right, title, and interest in and to your Contributions. All contributions are subject to the Developer Certificate of Origin and license set out at [here](https://docs.gitlab.com/ce/legal/developer_certificate_of_origin). _This notice should stay as the first item in the CONTRIBUTING.md file._

## Prerequisites

You need to have the following installed:
- Node.js version 14 or later
- npm version 7 or later
- Docker version 21 or later
- Git

Instead of running this project locally, you can also pull the docker image using command `docker pull node:21-alpine`.

## Install Dependencies

To install dependencies, run `npm install` in the terminal. This will install express, mocha, and supertest.

## Local Setup

To start the server, use the `npm start` command. The app will be running at `http://localhost:5000`.

## Docker Setup

1. To build the Docker image, run `docker build -t gitlab/nodejs-express:v1 .`
2. To start a Docker container, run `docker run -d -p 80:5000 gitlab/nodejs-express:v1`
3. The app will be running at `http://localhost:5000`

## Testing

To test, run command `npm test` in your terminal. It will use Mocha & Supertest to test Express routes.

## CI/CD Setup

Please refer to the specific CI/CD pipeline configuration for further instructions.

## Code of Conduct

We follow the Contributor Covenant code of conduct. Find it [here](https://contributor-covenant.org/version/1/1/0/).

## License

MIT License

Copyright(c)2017-Present GitLab B.V. 

The above copyright notice and this permission notice should be included in all copies or substantial portions of the Software.