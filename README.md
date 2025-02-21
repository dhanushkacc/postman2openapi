Postman2OpenAPI Converter
A tool that converts Postman collections into OpenAPI specifications. This project includes a Node.js backend, an Angular frontend, and support for deployment via AWS Lambda using a Docker container. Anyone can use this service by sending a POST request with a Postman collection as a JSON object. The converter supports both YAML and JSON output formats.

Table of Contents
Overview
Features
Architecture
Installation & Setup
Frontend (Angular)
Backend (Node.js)
Docker Deployment
AWS Lambda Deployment
Usage
Using the Frontend
Using the API Directly
API Reference
Contributing
License
Contact
Overview
The Postman2OpenAPI Converter is designed to ease the transition from Postman collections to standardized OpenAPI specifications. It provides:

A Node.js backend for converting Postman collections.
An Angular frontend that offers a user-friendly interface.
Deployment support via AWS Lambda with a pre-built Docker image.
Flexibility to output the OpenAPI specification in either YAML or JSON formats.
Features
Conversion Flexibility: Choose between YAML and JSON output.
Error Handling: Built-in logic to repair and parse invalid JSON collections.
User-Friendly UI: An Angular-based frontend for file uploads and result display.
API Endpoint: Easily accessible endpoint for integration with other tools.
Dockerized Deployment: Run the entire backend locally or on the cloud using Docker.
Serverless Ready: AWS Lambda deployment for scalable, on-demand conversions.
Architecture
The project is split into three main components:

Angular Frontend:

Provides a graphical interface to upload Postman collections.
Displays the converted OpenAPI spec.
Contains features like file selection, conversion initiation, error messages, and a "copy to clipboard" function.
Node.js Backend:

Exposes an API endpoint (/convert) to handle POST requests.
Converts the input Postman collection to OpenAPI using libraries like postman-to-openapi and js-yaml.
Includes robust error handling to manage malformed JSON by using tools like jsonrepair.
Deployment & Dockerization:

A Docker image is provided for local or server deployment.
AWS Lambda functions are created using the Docker image to expose the conversion API over the internet.
Installation & Setup
Frontend (Angular)
Clone the repository:
bash
Copy
git clone https://github.com/yourusername/postman2openapi.git
cd postman2openapi/frontend
Install dependencies:
bash
Copy
npm install
Run the application:
bash
Copy
ng serve
The application should now be running on http://localhost:4200.
Backend (Node.js)
Navigate to the backend directory:
bash
Copy
cd ../backend
Install dependencies:
bash
Copy
npm install
Start the server:
bash
Copy
node server.js
The server will be available on the port defined in your configuration (commonly port 3000).
Docker Deployment
To run the backend locally using Docker, you can pull the Docker image:

bash
Copy
docker pull dhanushka23/postman2openapi:tagname
Then run the container:

bash
Copy
docker run -p 3000:3000 dhanushka23/postman2openapi:tagname
AWS Lambda Deployment
For external usage, the backend is deployed as a serverless function in AWS Lambda. The steps include:

Dockerize the Node.js backend:
The provided Docker image is used to package the entire Node.js backend.
Deploy to AWS Lambda:
Create a Lambda function that uses the Docker image. This function will expose the /convert endpoint at:
bash
Copy
https://kvxeityuj7ejiyuo7w64ovbgg40lmava.lambda-url.eu-north-1.on.aws/convert
Accessing the Service:
Anyone can send a POST request with a valid Postman collection (JSON format) to the endpoint and specify if they want the output in YAML or JSON.
Usage
Using the Frontend
Upload File:
Click on the file input to select your Postman collection file.
Select Format:
Choose your desired output format (YAML or JSON).
Convert:
Click the convert button to start the conversion.
Copy Result:
Use the “Copy to Clipboard” button to copy the converted OpenAPI specification.
Using the API Directly
Send a POST request to the conversion endpoint with a JSON body:

json
Copy
{
  "collection": "{...}",  // Your Postman collection as a JSON string
  "format": "yaml"         // Or "json" for JSON output
}
Example using curl:

bash
Copy
curl -X POST https://kvxeityuj7ejiyuo7w64ovbgg40lmava.lambda-url.eu-north-1.on.aws/convert \
-H "Content-Type: application/json" \
-d '{"collection": "YOUR_POSTMAN_COLLECTION_JSON", "format": "yaml"}'
API Reference
POST /convert
Description: Converts a Postman collection into an OpenAPI specification.
Request Body:
collection (string): A valid JSON string representing the Postman collection.
format (string): The desired output format, either yaml or json.
Response:
On success: Returns an object containing openApiSpec with the converted specification.
On failure: Returns an error object with details about the failure.
Contributing
Contributions are welcome! Please follow these guidelines:

Fork the repository and create a new branch for your feature or bug fix.
Ensure your code is well-documented and includes tests where appropriate.
Submit a pull request with a clear description of your changes.
Follow the existing coding style and documentation practices.
