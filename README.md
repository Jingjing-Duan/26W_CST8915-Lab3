# 26W_CST8915-Lab3

Demo Video
https://youtu.be/IB8b0ySXBBE

Reflection Questions
1. What challenges did you encounter when configuring environment variables in the GitHub Actions workflow?

One of the main challenges was understanding that front-end applications cannot read environment variables at runtime once deployed as static files. The API URLs must be injected during the build stage. At first, I forgot to set the RABBITMQ_CONNECTION_STRING in my order-service App Service, which caused the “Failed to place order” error because the service was trying to connect to localhost instead of the RabbitMQ VM. I also encountered an Azure policy violation when attempting to create the Static Web App, which prevented the automatic generation of the GitHub Actions workflow file. These issues helped me better understand how environment variables and CI/CD configuration work in cloud deployments.

2. How does deploying microservices on Azure Web App Service differ from running them locally?

When running services locally, everything works on localhost and configuration is usually simple. However, when deploying to Azure Web App Service, environment variables must be explicitly configured in the Azure Portal. Networking, ports, CORS, and service-to-service communication also become important. For example, I had to configure the RabbitMQ connection string correctly and ensure that the correct port (5672) was open. In the cloud environment, services are separated and communicate over public endpoints, which makes deployment more realistic but also more complex.

3. Why is it important to use environment variables for configurations in a cloud environment?

Environment variables allow applications to remain flexible and secure. Instead of hardcoding sensitive information like connection strings or service URLs, they can be configured differently for development, testing, and production environments. In this lab, environment variables were essential for connecting the order-service to RabbitMQ and for allowing the store-front to communicate with backend services. This approach follows the 12-Factor App methodology and makes the application more portable and easier to manage in a cloud environment.

Service Repositories

order-service: https://github.com/Jingjing-Duan/order-service

product-service: https://github.com/Jingjing-Duan/product-service

store-front: https://github.com/Jingjing-Duan/store-front

Optional Notes

During this lab, I encountered issues related to CORS configuration, RabbitMQ connectivity, and Azure policy restrictions when attempting to deploy the Static Web App. Troubleshooting these problems helped me better understand how cloud infrastructure, networking, and environment configuration work together in a microservices architecture.
