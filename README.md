# Northwind database - MongoDB

## Spis treści
1. [Description](#description)
2. [Technologies](#technologies)
 - [Swagger](#swagger)
 - [Project Lombok](#project-lombok)
3. [Document-oriented database and relations](#document-oriented-database-and-relations)
4. [MongoDB database configuration](#mongodb-database-configuration)
5. [Containerization](#containerization)
6. [Addresses](#addresses)
7. [Documentation](#documentation)
8. [Authors](#authors)

## Description
The project purpose was to implement system executing basic operations on Northwind database in the selected technology.

### Database diagram
<img width="630" alt="129492965-a82a59f0-1ac1-4239-a86e-fd1f3c32f29c" src="https://user-images.githubusercontent.com/34041060/135817429-81c646f6-8139-455d-9f5c-a051b4197c2e.png">

## Document-oriented database and relations
There are two approaches to simulate relations in document-oriented datbase:
- **Embedded** - one document is embedded inside another document.
- **Reference** - documents are maintained separately, but one document contains a field that references to another document's id field.

In Northwind representation, relations between documents are simulated using embedded and reference approach:
- **Embedded** - saves complexity of queries, usually to one document.
- **Reference** - saves redundation of data in each query. It also ensures that size of the document won't be higher than 16MB.

Associative tables: Order Details, Employee Territories, CustomerCustomerDemo are included in the database.

## Technologies
- **MongoDB** – non SQL database management system
- **Spring Boot + Java11** – service executing basic database operations serwis realizujący podstawowe operacje na bazie Northwind.
- **Swagger** – automated documentation for describing RESTful APIs expressed using JSON.
- **Docker** – app containerization.

### Swagger
Dependecies from pom.xml:

<img width="300" alt="Screen Shot 2021-08-23 at 00 56 12 AM" src="https://user-images.githubusercontent.com/34041060/130372643-b7ebaec0-5fd8-45b7-8904-d0554adade24.png">

Configuration in SwaggerConfig class:

<img width="450" alt="Screen Shot 2021-08-16 at 00 40 35 AM" src="https://user-images.githubusercontent.com/34041060/129494798-7ec21a96-0105-4a89-9ee0-5eea783cf4d7.png">

### Project Lombok
Java library that automatically plugs into your editor and build tools. It replaces boilerplate code with easy to use annotations (constructors, getters, setters etc.).

Dependencies from pom.xml:

<img width="250" alt="Screen Shot 2021-08-23 at 00 55 47 AM" src="https://user-images.githubusercontent.com/34041060/130372630-4725e7a6-ed2e-406e-9798-117f4c284660.png">

## MongoDB database configuration
Dependencies from pom.xml:

<img width="350" alt="Screenshot 2021-08-24 at 00 45 21" src="https://user-images.githubusercontent.com/34041060/130528918-2db761f6-c156-46c2-a4bf-005c9aefa441.png">

Configuration file which is supported by Spring Boot - `application.properties`:

<img width="450" alt="Screenshot 2021-08-15 at 23 44 41" src="https://user-images.githubusercontent.com/34041060/129493705-194af92d-f823-4334-9ec0-bb02e05270eb.png">

## Containerization
App is containerized using Docker - two containers are highlighted:
- Container with configured MongoDB database - `mongo`
- Container with server service - `northwind-service`

<img width="300" alt="Screen Shot 2021-08-16 at 00 35 05 AM" src="https://user-images.githubusercontent.com/34041060/129494676-5b738e5c-37e5-4dec-9f45-808291d83a8e.png">

`docker-compose up -d` - building containers.

`docker-compose down` - deleting containers.

## Addresses
- **Server:** http://localhost:8080
- **Swagger:** http://localhost:8080/swagger-ui/index.html

## Documentation
- [App description (in Polish):](https://github.com/igordzie97/mongodb-databases-project/blob/main/documentation/documentation.pdf)

## Authors:
- Igor Dzierwa
- Adrian Nędza
- Konrad Makuch
