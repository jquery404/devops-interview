# Interview Web App

A simple TypeScript web application that returns "Hello World". This app is containerised and ready for deployment.

## Features

- TypeScript-based Express web server
- Returns "Hello World" on the root endpoint
- Health check endpoint at `/health`
- Docker containerization
- Jest testing suite

## Prerequisites

- Node.js 20+ (for local development)
- Docker and Docker Compose (for containerised deployment)

## Installation

Install dependencies:

```bash
npm install
```

## Development

Run the app locally in development mode:

```bash
npm run dev
```

The server will start on `http://localhost:3000`

## Build

Compile TypeScript to JavaScript:

```bash
npm run build
```

Run the compiled version:

```bash
npm start
```

## Testing

Run tests:

```bash
npm test
```

Generate coverage report:

```bash
npm run test:coverage
```

## Docker

### Build the Docker image

```bash
docker build -t interview-webapp .
```

### Run the container

```bash
docker run -p 3000:3000 interview-webapp
```

### Using Docker Compose

For local testing with Docker Compose:

```bash
docker-compose up
```


## Endpoints

- `GET /` - Returns "Hello World"
- `GET /health` - Returns health status JSON: `{"status": "ok"}`

## Testing the Application

Once running, test the endpoints:

```bash
# Test Hello World endpoint
curl http://localhost:3000/

# Test health endpoint
curl http://localhost:3000/health
```

## Project Structure

```
.
├── src/
│   ├── app.ts           # Express app configuration
│   ├── index.ts         # Entry point
│   └── app.test.ts      # Jest tests
├── dist/                # Compiled JavaScript (generated)
├── coverage/            # Test coverage reports (generated)
├── Dockerfile           # Docker configuration
├── docker-compose.yml   # Docker Compose configuration
├── tsconfig.json        # TypeScript configuration
├── jest.config.js       # Jest configuration
├── package.json         # Dependencies and scripts
└── README.md            # This file
```

## Interview Tasks

The following tasks should be completed as a take-home assignment. Allocate 30-60 minutes to complete the task.
You will have access to this codebase the day before your interview to implement CI/CD workflows using GitHub Actions.
Feel free to fork this repo generate a CI/CD in your forks GitHub actions, alternatively you could use tools like [excalidraw](https://excalidraw.com/) to generate diagrams, write the yaml files, or use pseudo code.

### Task 1: Continuous Integration (CI) Workflow

**Requirement:**
Every change must pass continuous integration checks before making its way to the master branch.

**CI Must Verify:**
- The TypeScript application compiles successfully
- All tests pass
- The Docker image can be built successfully

**Points for discussion:**
- What events should trigger CI? (push to feature branches, pull requests, etc.)
- How can you optimize build times?
- What information should developers see when CI fails?


### Task 2: Continuous Deployment (CD) Workflow

**Requirement:**
Changes merged to master should be deployed automatically to production.

**CD Must Include:**
- Deploy the application (you can mock this step with docker, or use pseudo code)
- Post-deployment verification:
  - Verify the health check endpoint returns 200 status
- Notification when deployment or verification fails
  - These notifications don't need to go anywhere real, printing to stdout is fine

**Points for discussion:**
In a busy team repository with many daily commits to master, you need to consider:
1. **Deployment Triggers**: How do you handle high-frequency commits? Should every commit trigger deployment?
2. **Concurrent Deployments**: How do you handle multiple deployments triggered in quick succession?
3. **Rollback Strategy**: If smoke tests fail, how do you handle rollback? How would you ensure a rollback reverts to exactly the previous deployment state rather than rebuilding an older commit?
4. **Environment Management**: How would you extend this to handle different environments (staging vs production)?



