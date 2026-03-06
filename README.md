# DUA Streamliner

## Problem Statement

The preparation of the DUA is a critical step in import and export operations in Costa Rica. The DUA consolidates key information about the importer or exporter, consignee, goods description, customs regime, declared values, taxes, transportation details, and supporting documentation.

Currently, the DUA is completed manually by interpreting multiple source documents such as commercial invoices, packing lists, certificates of origin, bills of lading, insurance policies, and special permits. These documents may come in different formats including Excel files, Word documents, PDFs, and scanned images.

Because these documents do not follow a standardized structure and may vary significantly between suppliers or companies, the interpretation process requires specialized domain knowledge. As a result, the preparation of the DUA becomes:

- Time-consuming and operationally repetitive  
- Highly dependent on expert interpretation  
- Prone to human errors and inconsistencies  
- Vulnerable to delays, penalties, or customs rejections  

In addition, extracting relevant data from heterogeneous document formats requires manual reading, cross-checking values, validating totals, and mapping information into the official DUA template defined by the Costa Rican customs authority.

This project aims to design an intelligent system capable of automating the reading, semantic extraction, validation, and mapping of information from multiple document sources into the official DUA template. The goal is not to replace customs experts, but to transform their role from manual data entry operators into strategic validators, reducing operational workload and minimizing errors.

---

## Authors

- Andrés Ramírez Madrigal  
- Ignacio Cordero Chinchilla

# 1. Frontend Design

## 1.1 Technology stack:

## 1.1 Technology Stack

- Application Type: Web Application

- Web Framework: React.js v19.2
- Web Server: Node.js v21
- Coding Language: TypeScript v5.9.3

- Unit Testing Framework: Jest v30.2.0
- Integration Testing Tool: Playwright v1.58.2

- Data Validation Framework: Zod v3.23.8
- Code Prettier Framework: Prettier v3.3.3
- Code Style Framework: ESLint v9.10.0

- Cloud Service: Microsoft Azure
- Hosted Service within Cloud: Azure App Service

- Code Repository Service: Azure DevOps Repos
- Code Automation Task Tool: Husky v9.1.7

- CI/CD Pipelines Technology: Azure DevOps Pipelines

- Environments: Development, QA, Staging, Production
- Environment Deployment Tools: Azure DevOps Environments + Azure App Service Deployment Slots

- Observability Framework: Azure Application Insights SDK v3.x

## 1.2 UX UI analysis: 

### Core Business Process

This section describes the user interaction flow across the main screens of the application. The description focuses only on user actions and system responses.

---

### 1. Login

1. The user accesses the system and provides their login credentials and a one-time authentication token.

2. The user submits the authentication information to access the system.

3. If the authentication fails, the system informs the user that the username or password is invalid.

4. If the authentication is successful, the system grants access and redirects the user to the generator configuration process.

---

### 2. Configure the Generator

1. The user accesses the generator configuration section to prepare a new DUA generation process.

2. The user selects the folder that contains the source documents required to extract the necessary information.

3. The system reads the folder and verifies that supported document formats are present.

4. If no valid documents are detected, the system informs the user that the selected folder does not contain supported files.

5. The user selects the official DUA template that will be used to generate the final document.

6. The system verifies that the selected template is valid and compatible with the generation process.

7. The user confirms the configuration in order to start the generation process.

8. The system validates the provided information and configuration parameters.

9. If the configuration contains invalid or incomplete information, the system informs the user that the configuration must be corrected.

10. If the configuration is valid, the system stores the configuration and initializes the document processing and information extraction process.

11. Once the generation process begins, the user is redirected to the monitoring section.

---

### 3. Monitoring the Progress

1. The user accesses the monitoring section to track the progress of the generation process.

2. The system continuously updates the current state of the process and informs the user about the stages of document processing, data extraction, and template population.

3. If the process encounters an error while reading or interpreting the source documents, the system informs the user that the generation process failed.

4. If the process completes successfully, the system notifies the user that the generated DUA document is ready to be obtained.

---

### 4. Obtain the Result / Export

1. The user accesses the generated results once the process has finished.

2. The system prepares the generated DUA document and makes it available for retrieval.

3. The user requests the export of the generated results.

4. The system processes the export request and delivers the generated DUA file.

---

### 5. Logout

1. The user decides to terminate the session.

2. The system invalidates the active session and returns the user to the initial access screen.

## 1.3 Component design strategy: Define la técnica y los principios de diseño de componentes del frontend, cómo se logra la reutilización de componentes, cómo se logra centralizar los estilos, el branding, la internacionalización y la responsividad.

## 1.4 Security: Tecnologías, técnicas y classes con su respectiva ubicación en la estructura del proyecto responsables de la autenticación y la autorización de permisos y sesiones. 

## 1.5 Layered design: diseño y explicación de las diversas capas de la aplicación en el frontend. 

## 1.6  Design patterns: Diseño de classes con su respectiva ubicación en la estructura del proyecto, donde sea necesario aplicar patrones de diseño orientado a objetos, como por ejemplo: seguridad, refrescado de UI, recepción de notificaciones, almacenamiento de estados, llamadas a api, operaciones asíncronas, invalidación de sesiones, programación por eventos, creación de objetos. 

## 1.7 un folder en /src que contiene el scaffold del proyecto, el cual se genera a partir de toda la especificación de los puntos del 1.1 al 1.6. 
