# Postman2OpenAPI Converter

A tool that converts Postman collections into OpenAPI specifications. This project includes a Node.js backend, an Angular frontend, and support for deployment via AWS Lambda using a Docker container. Anyone can use this service by sending a POST request with a Postman collection as a JSON object. The converter supports both YAML and JSON output formats.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Installation & Setup](#installation--setup)
  - [Frontend (Angular)](#frontend-angular)
  - [Backend (Node.js)](#backend-nodejs)
  - [Docker Deployment](#docker-deployment)
  - [AWS Lambda Deployment](#aws-lambda-deployment)
- [Usage](#usage)
  - [Using the Frontend](#using-the-frontend)
  - [Using the API Directly](#using-the-api-directly)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

The Postman2OpenAPI Converter is designed to ease the transition from Postman collections to standardized OpenAPI specifications. It provides:

- A Node.js backend for converting Postman collections.
- An Angular frontend that offers a user-friendly interface.
- Deployment support via AWS Lambda with a pre-built Docker image.
- Flexibility to output the OpenAPI specification in either YAML or JSON formats.

## Features

- **Conversion Flexibility:** Choose between YAML and JSON output.
- **Error Handling:** Built-in logic to repair and parse invalid JSON collections.
- **User-Friendly UI:** An Angular-based frontend for file uploads and result display.
- **API Endpoint:** Easily accessible endpoint for integration with other tools.
- **Dockerized Deployment:** Run the entire backend locally or on the cloud using Docker.
- **Serverless Ready:** AWS Lambda deployment for scalable, on-demand conversions.

## Architecture

The project is split into three main components:

### Angular Frontend

- Provides a graphical interface to upload Postman collections.
- Displays the converted OpenAPI spec.
- Contains features like file selection, conversion initiation, error messages, and a "copy to clipboard" function.

### Node.js Backend

- Exposes an API endpoint (`/convert`) to handle POST requests.
- Converts the input Postman collection to OpenAPI using libraries like `postman-to-openapi` and `js-yaml`.
- Includes robust error handling to manage malformed JSON by using tools like `jsonrepair`.

### Deployment & Dockerization

- A Docker image is provided for local or server deployment.
- AWS Lambda functions are created using the Docker image to expose the conversion API over the internet.

## Installation & Setup

### Frontend (Angular)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/postman2openapi.git
   cd postman2openapi/frontend
