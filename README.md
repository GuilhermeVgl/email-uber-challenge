# Coding Challenge Guidelines

This is a description of a challenge have been done, old challenge for developers in Uber.

## Functional spec

Email Service

*1. Email Service*
* Create a service that accepts the necessary information and sends emails. It should provide an abstraction between two different email service providers. 

Amazon SES - Simple Send Documentation

# Technical spec

Back-end track: Write, document and test your API as if it will be used by other services.

I decided to follow the Back-end track, because it is just an example and training code.

Email Service Backend Project
Overview
This project is a Java application for sending emails, following the principles of Clean Architecture, which emphasizes the separation of concerns into distinct layers. Here's an overview of how it works:

*1. Infrastructure Layer (AWS SES Configuration):*
* The AwsSesConfig class is a Spring configuration that defines a bean to create an instance of the Amazon Simple Email Service (Amazon SES) client.
* This instance is injected into the SesEmailSender class to enable email sending through the Amazon service.

*2. Presentation Layer (Controller):*
* The EmailSenderController class is a Spring MVC controller that handles HTTP requests to send emails.
* It defines an endpoint /api/email to send emails via a POST request.
* It utilizes the EmailSenderService class to process the business logic and send the email.

*3. Domain Layer (Entity and Exception):*
* The EmailRequest class is a simple entity that represents an email request, using Java's record concept.
* The EmailServiceException class is a custom exception that can be thrown in case of errors in the email service.

*5. omain Layer (Service):*
* The EmailSenderUseCase interface defines a contract for the email sending service, promoting abstraction between the presentation and infrastructure layers.
* The EmailSenderService class implements this interface and contains the business logic to send emails.
* It's responsible for validating the received data, calling the email sending gateway, and handling exceptions.

*5. Infrastructure Layer (Gateway):*
* The EmailSenderGateway interface defines a contract for sending emails, allowing the implementation of different email providers without modifying the service code.
* The SesEmailSender class is a concrete implementation of this gateway, using Amazon SES to send emails.

Testing the API

You can test the API using an API testing tool like Postman or by simply making an HTTP request. 

You'll need to create a POST request to url: localhost:8080/api/email.

You'll need to do the request using a JSON body for request

Here's how you can do it using cURL:
<br>
{<br>
    "to":"yourmail@mail.com",<br>
    "subject":"subject",<br>
    "body":"body message text"<br>
}<br>
