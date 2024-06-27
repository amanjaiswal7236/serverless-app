# Serverless Email Service

This project is a serverless REST API built using the Serverless Framework, AWS Lambda, and AWS SES (Simple Email Service). The API allows you to send emails by providing the recipient's email address, subject, and body text.

## Prerequisites

- Node.js
- AWS CLI (configured with appropriate permissions)
- Serverless Framework

## Setup

1. **Install Serverless Framework:**
    - Run `npm install -g serverless`

2. **Initialize the Project:**
    - Run `serverless create --template aws-nodejs --path serverless-email`
    - Navigate to the project directory: `cd serverless-email`

3. **Install Dependencies:**
    - Run `npm init -y`
    - Run `npm install aws-sdk`

4. **Update `serverless.yml` File:**
    - Define the service, provider, functions, events, plugins, and IAM role statements required for sending emails using SES.

5. **Create `handler.js`:**
    - Implement the Lambda function code to send an email using AWS SES, including input validation and error handling.

6. **Deploy the Service:**
    - Run `serverless deploy`

## Running Locally

To test the service offline:

1. **Start Serverless Offline:**
    - Run `serverless offline`

2. **Test with Postman:**

    - **URL:** `http://localhost:3000/send-email`
    - **Method:** POST
    - **Headers:**
        - `Content-Type: application/json`
    - **Body:**
        ```json
        {
          "receiver_email": "recipient@example.com",
          "subject": "Test Email",
          "body_text": "This is a test email."
        }
        ```

    - **Expected Responses:**
        - **200 OK:**
            ```json
            {
              "message": "Email sent successfully"
            }
            ```
        - **400 Bad Request:**
            ```json
            {
              "message": "receiver_email, subject, and body_text are required."
            }
            ```
        - **500 Internal Server Error:**
            ```json
            {
              "message": "Internal Server Error"
            }
            ```

## Notes

- Ensure the `Source` email in `handler.js` is verified in AWS SES.
- Modify the `region` in `serverless.yml` if using a different AWS region.
- Check the console for detailed error messages if issues arise.

## License

This project is licensed under the MIT License.
