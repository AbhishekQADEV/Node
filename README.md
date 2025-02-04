```
# Node Express Template Project

This project is a template for Node.js Express applications. It's an Express.js app that comes with a basic hello world route and HTTP response.

## Software Requirements

For MacOS:

- Node.js (v14.15.0 or later)
- npm (v6.14.8 or later)
- Docker (v20.10.11 or later)

For Windows:

- Node.js (v14.15.0 or later)
- npm (v6.14.8 or later)
- Docker for Windows (v20.10.11 or later)

## Database Requirements

No database requirements specified.

## Installing Steps for MacOS

1. Install [Homebrew](https://brew.sh/)
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
2. Install Node.js
```
brew install node
```
3. Install Docker
```
brew install docker
```
4. Clone the repository
```
git clone {repo link}
```
5. Navigate to the cloned repository
```
cd {repo name}
```
6. Install dependencies
```
npm install
```

## Installing Steps for Windows

1. Install Node.js & npm. Instructions can be found [here](https://nodejs.org/en/download/package-manager/#windows)
2. Install Docker for Windows. Instructions can be found [here](https://docs.docker.com/docker-for-windows/install/)
3. Clone the repository
```
git clone {repo link}
```
4. Navigate to the cloned repository
```
cd {repo name}
```
5. Install dependencies
```
npm install
```

## Local Development

Start the development server with:

```
node server.js
```

## Testing

Run tests with:

```
npm test
```

## Building and Running in Docker

The `Dockerfile` is already set up for this project.

1. Build docker image:
```
docker build -t {repo name} .
```
2. Run docker image:
```
docker run -p 5000:80 {repo name}
```
It's set up to expose port 80, so you can navigate to `http://localhost:5000` on your browser.

## CI/CD pipeline

This project is set up to work with GitLab's Auto DevOps CI/CD pipeline. If not already enabled for this project, then you can turn it on from Project Settings as per [GitLab's documentation](https://docs.gitlab.com/ee/topics/autodevops/#enable-or-disable-auto-devops).
```
