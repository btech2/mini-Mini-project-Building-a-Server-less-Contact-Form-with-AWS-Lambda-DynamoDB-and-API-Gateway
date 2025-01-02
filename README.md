# mini-Mini-project-Building-a-Server-less-Contact-Form-with-AWS-Lambda-DynamoDB-and-API-Gateway
Mini project Building a Server less Contact Form with AWS Lambda, DynamoDB, and API Gateway
Story: Building a Serverless Web Application with AWS
 
Project Overview:
In this project, we’re creating a serverless web application that allows users to submit inquiries through a contact form. The architecture is built entirely using AWS services to ensure scalability, flexibility, and cost efficiency. The three core components of this project are DynamoDB for data storage, Lambda for server-side processing, and API Gateway for handling incoming web requests. Together, these components create a seamless, user-friendly experience for storing and retrieving data, all without needing to manage servers.
 
Step 1: Setting Up IAM Role
The first task in setting up this project is creating an IAM role. IAM (Identity and Access Management) roles in AWS define permissions for services to access resources securely. In this case, the IAM role is created specifically for the Lambda function, allowing it to interact with other AWS resources, including DynamoDB.
•	Why is the IAM role important?
o	The IAM role ensures that the Lambda function has the proper permissions to access DynamoDB, log execution details, and interact with other necessary AWS services. Without this role, the Lambda function wouldn’t be able to perform its tasks.
o	Permissions are vital for debugging and troubleshooting because they allow AWS services to log detailed execution information, which is essential for identifying and fixing any issues.
 
Step 2: Creating the Lambda Function
Once the IAM role is created, we proceed to set up the Lambda function, which will act as the backend server for the application. The Lambda function will handle requests sent by users via the web page.
•	Lambda Configuration:
o	Name and Runtime: The Lambda function is given a name and an appropriate runtime (e.g., Node.js, Python).
o	IAM Role Association: The function is linked to the previously created IAM role, ensuring it has the necessary permissions.
o	Functionality: The Lambda function needs to handle both GET and POST requests. For a GET request, it serves the contact form, and for a POST request, it processes the submitted data.
Key Lambda Action:
When users submit the contact form, the Lambda function stores their data in DynamoDB and returns a success message to the user.
 
Step 3: Interacting with DynamoDB
DynamoDB serves as the database for this serverless application. All user data submitted via the contact form will be stored in a DynamoDB table.
•	Table Setup:
The table is created with a partition key, which is the email address of the user. This ensures that each user’s inquiry is unique and can be easily retrieved.
•	Data Management:
When a user submits their contact information (e.g., name, email, message), the Lambda function will insert this data into the DynamoDB table. Since the partition key is the email, DynamoDB ensures no duplicates can be entered, preventing the same user from submitting multiple identical entries.
 
Step 4: Setting Up API Gateway
To allow users to interact with the backend, we use API Gateway. This service acts as a bridge between the frontend (contact form) and the backend (Lambda function), enabling users to send requests and receive responses.
•	Creating the API:
An API is set up in API Gateway to expose the necessary endpoints. The API is configured with methods for both GET (to fetch the contact page) and POST (to handle the submission of data).
•	Lambda Proxy Integration:
The video stresses the importance of Lambda Proxy Integration. This setup allows API Gateway to pass the request directly to the Lambda function, which can then process the data and return the appropriate response.
•	Deployment and URL:
After configuring the API, it is deployed, and a unique invoke URL is generated. This URL is what the frontend will use to make requests to the Lambda function via API Gateway.
 
Step 5: Testing the Application
With the backend services (Lambda and DynamoDB) and API Gateway in place, the next step is to test the entire flow:
1.	User Accesses the Contact Form:
o	The user accesses the contact form by sending a GET request to the API Gateway, which retrieves the page for them.
2.	User Submits the Form:
o	When the user submits the contact form (via POST), the data is sent to API Gateway, which triggers the Lambda function.
3.	Data is Stored in DynamoDB:
o	The Lambda function processes the data and stores it in the DynamoDB table. The partition key (email) ensures that no duplicate entries are stored.
4.	Success Response:
o	After successfully saving the data, the Lambda function returns a success page to the user, letting them know their inquiry has been submitted.
 
Step 6: Benefits of Using Serverless Architecture
The project highlights the many advantages of using serverless components:
•	Scalability:
The serverless architecture, with services like Lambda and DynamoDB, automatically scales to handle varying levels of traffic without needing manual intervention.
•	Cost Efficiency:
By using serverless services, developers only pay for the exact resources consumed, making the project highly cost-effective, especially for small to medium applications.
•	Simplicity in Deployment:
Serverless components reduce the need to manage infrastructure, allowing developers to focus purely on writing code and deploying the application quickly. API Gateway and Lambda simplify the process of building and deploying RESTful APIs.
 
Conclusion
By combining Lambda, DynamoDB, and API Gateway, this project creates a fully serverless web application. Each service works together to handle incoming user data securely and efficiently. The use of IAM roles and proper permissions ensures the Lambda function operates smoothly, while DynamoDB stores user inquiries in a scalable and efficient manner. The setup enables users to submit their data through a contact form, which is then stored and processed in the backend without any server management.
This project demonstrates the power and flexibility of AWS serverless technologies in building modern web applications, providing users with a seamless and highly available experience.

