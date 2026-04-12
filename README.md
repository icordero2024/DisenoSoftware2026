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

## 1.1 Technology stack

- Application Type: Web Application
- Web Framework: Next.js v15.x (React v19.2)
- Web Server: Node.js v21
- Coding Language: TypeScript v5.9.3

- Unit Testing Framework: Jest v30.2.0
- Integration Testing Tool: Playwright v1.58.2
- Data Validation Framework: Zod v3.23.8

- Code Formatter: Prettier v3.3.3
- Code Style Framework: ESLint v9.10.0
- Code Automation Task Tool: Husky v9.1.7

- Cloud Service: Microsoft Azure
- Hosted Service within Cloud: Azure App Service

- Code Repository Service: Azure DevOps Repos
- CI/CD Pipelines Technology: Azure DevOps Pipelines

- Environments: Development, QA, Staging, Production
- Environment Deployment Tools: Azure DevOps Environments + Azure App Service Deployment Slots

- Observability Framework: Azure Application Insights SDK v3.x

## 1.2 UX UI analysis: 

### Usability Attributes

- Learnability  
The system provides a linear and guided workflow (login → configuration → monitoring → result), allowing new users to quickly understand how to use the application.

- Efficiency  
Users can complete the DUA generation process with minimal steps by selecting documents and templates within a single flow.

- Error Prevention  
The system validates documents and templates before starting the generation process, reducing the likelihood of failures.

- Feedback  
The system continuously informs the user about the process status, including validation errors, processing stages, and completion notifications.

- Consistency  
All interactions follow a consistent workflow and predictable behavior across all screens.

- Simplicity  
The interface is designed to minimize complexity and avoid unnecessary actions or decisions.

- Visibility of System Status  
The system clearly communicates processing stages and data confidence levels, ensuring users always understand the current state of the operation.

### Core Business Process

This section describes the user interaction flow across the main screens of the application. The description focuses only on user actions and system responses.

---

#### 1. Login

1. The user accesses the system and provides their login credentials and a one-time authentication token.

2. The user submits the authentication information to access the system.

3. If the authentication fails, the system informs the user that the username or password is invalid.

4. If the authentication is successful, the system grants access and redirects the user to the generator configuration process.

---

#### 2. Configure the Generator

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

#### 3. Monitoring the Progress

1. The user accesses the monitoring section to track the progress of the generation process.

2. The system continuously updates the current state of the process and informs the user about the stages of document processing, data extraction, and template population.

3. If the process encounters an error while reading or interpreting the source documents, the system informs the user that the generation process failed.

4. If the process completes successfully, the system notifies the user that the generated DUA document is ready to be obtained.

---

#### 4. Obtain the Result / Export

1. The user accesses the generated results once the process has finished.

2. The system prepares the generated DUA document and makes it available for retrieval.

3. The user requests the export of the generated results.

4. The system processes the export request and delivers the generated DUA file.

---

#### 5. Logout

1. The user decides to terminate the session.

2. The system invalidates the active session and returns the user to the initial access screen.

### Wireframes

#### Login Screen

This screen allows the user to authenticate into the system using their username, password, and one-time authentication token.

![Login Wireframe](images/login.png)

---

#### Configure Generator

This screen allows the user to configure the DUA generation process.  
The user selects the folder containing the source documents and chooses the official DUA template that will be used for the generation process.

![Configure Generator Wireframe](images/generator.png)

---

#### Monitoring Progress

This screen allows the user to monitor the progress of the document processing and information extraction process.  
The system displays the different stages involved in generating the DUA document.

![Monitoring Progress Wireframe](images/process.png)

---

#### Result / Export

This screen allows the user to retrieve the generated DUA document once the process has finished successfully.

![Result Export Wireframe](images/result.png)

---

#### Logout

This screen allows the user to confirm the termination of the active session.

![Logout Wireframe](images/logout.png)

---

### UX Testing Results

A usability test was conducted with three participants who are not familiar with software design.

The objective of the test was to evaluate how intuitive the wireframes are by analyzing where users naturally clicked when attempting to complete each task.

#### Testing Method

Participants were asked to complete tasks corresponding to the main workflow (login, configuration, monitoring, and export).

The test did not require users to click on exact interactive elements. Any click was considered as task completion. This approach allowed observation of user intuition and interaction patterns based on where they expected actions to occur.

#### Metrics

- Number of participants: 3  
- Task completion rate: 100%  
- Interaction analysis: Based on click distribution (heatmaps)  
- Misclicks: Observed through clicks outside expected interaction areas  

#### Observations

- Users consistently clicked on areas that aligned with expected interaction zones across most screens.
- The login, monitoring, and result stages were clearly understood by all participants.
- Interaction patterns indicate that the layout and structure effectively guide user actions.
- Minor variations in click behavior were observed but did not affect task completion.

#### Insights

- The overall workflow is intuitive and easy to follow, even for users without prior knowledge of the system.
- Visual hierarchy and element positioning successfully communicate possible actions.
- The interface supports natural user interaction with minimal confusion.

#### Improvements Identified

- Minor refinements can be made to further reinforce key interaction areas.
- Additional visual cues could improve clarity in edge cases without impacting the current usability.


### UX Testing Evidence

#### Heatmap - Login Screen

![Login Heatmap](images/heatmap1.jpg)

#### Heatmap - Configure Generator

![Configure Heatmap](images/heatmap2.jpg)

#### Heatmap - Monitoring Progress

![Monitoring Heatmap](images/heatmap3.jpg)

#### Heatmap - Result

![Result Heatmap](images/heatmap4.jpg)

#### Heatmap - Logout

![Logout Heatmap](images/heatmap5.jpg)

## 1.3 Component Design Strategy

The frontend component design follows a structured and reusable approach based on Atomic Design principles, combined with centralized styling, internationalization, and responsive design strategies.

---

### Component Design Technique

The application uses the Atomic Design methodology to structure UI components into hierarchical levels:

- **Atoms**  
  Basic UI elements such as buttons, inputs, labels, icons, and loaders.

- **Molecules**  
  Combinations of atoms forming functional units, such as form fields, file selectors, and status indicators.

- **Organisms**  
  Complex UI sections composed of multiple molecules, such as:
  - Login form
  - Generator configuration panel
  - Progress monitoring panel
  - Data review table

- **Templates**  
  Page-level layouts that define structure without specific data.

- **Pages**  
  Fully instantiated views connected to application state and API data.

This structure ensures scalability, separation of concerns, and maintainability.

---

### Component Reusability Strategy

Reusability is achieved through:

- Clear separation between presentational and container components  
- Stateless UI components (atoms and molecules)  
- Prop-driven configuration for flexible behavior  
- Shared hooks for logic reuse (e.g., `useAuth`, `useGenerator`, `useMonitoring`)  
- API abstraction through adapters, preventing coupling with backend structures  

---

### Styling & Branding Strategy

Styling is centralized using a design system approach:

- Tailwind CSS is used for utility-based styling  
- Global design tokens define:
  - Colors (including confidence levels: green, yellow, red)
  - Typography
  - Spacing and layout rules  

- A shared theme configuration ensures consistent branding across all components, including colors, typography, and visual identity aligned with the system purpose  

- UI states (hover, focus, error, loading) are standardized across the application  

---

### Internationalization (i18n)

Internationalization is implemented using a centralized translation system:

- All user-facing text is managed through translation files  
- Components consume translations via hooks (e.g., `useTranslation`)  
- Language switching is handled globally without affecting component structure  

This ensures scalability for multi-language support without modifying component logic.

---

### Responsiveness Strategy

The application is fully responsive and adapts to different screen sizes:

- Mobile-first design approach  
- Responsive breakpoints defined in the styling system  
- Flexible layouts using grid and flexbox  
- Components designed to adapt dynamically (e.g., tables collapse into cards on smaller screens)  

---

### State & UI Synchronization

Components remain synchronized with application state through:

- Server state handled by React Query (data fetching, caching, polling)  
- Client state handled via lightweight global stores  
- Real-time UI updates for:
  - Processing status
  - Data confidence visualization
  - Error and success feedback  

---

### Key Design Principles

- Separation of concerns  
- High cohesion and low coupling  
- Reusability and scalability  
- Predictable state management  
- Clear visual communication (especially for AI confidence levels)  

---

### Implementation Conventions

The component design follows specific implementation conventions to ensure consistency and alignment with project standards:

- **Atomic Design Usage**  
Components follow the previously defined Atomic Design structure.

- **CSS Centralization**  
Each component type maintains a single centralized style file to ensure consistency and avoid style duplication.

- **CSS Naming Convention**  
CSS class names follow a structured pattern:  
`ComponentName-StyleName`  

- **Responsive Units**  
All positional and layout units use `em` to ensure consistent scalability and responsiveness across devices.

- **Internationalization Support**  
All components are compatible with `react-i18next v16.5.8`, ensuring that text content is fully externalized and translatable.

- **Accessibility**  
Accessibility requirements are not considered within the scope of this implementation.

## 1.4 Security

The frontend security design defines authentication, authorization, and session management mechanisms, including the responsible technologies, techniques, and classes within the project structure.

---

### Authentication

- Identity Provider: Microsoft Entra ID  
- Authentication Model: Single Sign-On (SSO)  
- Multi-Factor Authentication (MFA): Enabled via mobile authenticator  
- Protocol: OAuth 2.0 / OpenID Connect  

Authentication is fully delegated to Microsoft Entra ID using:

- `@azure/msal-browser`
- `@azure/msal-react`

---

### Authorization

The system uses Role-Based Access Control (RBAC).

#### Roles

- **Manager**
- **Customs Agent**

#### Permissions by Role

**Manager**
- `MANAGE_USERS` → Manage user CRUD operations  
- `VIEW_REPORTS` → Access operational and performance reports  
- `EDIT_TEMPLATES` → Modify DUA templates  

**Customs Agent**
- `LOAD_FILES` → Upload and configure document folders  
- `GENERATE_DUA` → Start DUA generation process  
- `DOWNLOAD_DUA` → Export generated DUA document  

---

### Frontend Authorization Strategy

Authorization is enforced through:

- Protected routes  
- Permission-based UI rendering  
- Route guards validating user roles and scopes  

---

### Session Management

- Token acquisition and caching handled by MSAL  
- Storage strategy:
  - `sessionStorage` for session persistence  
  - `memoryStorage` (optional for higher security)  

- Session lifecycle:
  - Session starts after successful authentication  
  - Session is invalidated on logout  
  - Cached data is cleared after session termination  

---

### Security Classes and Location

Security responsibilities are encapsulated in dedicated classes located within the frontend project structure:

#### `/src/security/AuthService.ts`
- Handles login, logout, and token acquisition  
- Wraps MSAL functionality  

#### `/src/security/SessionManager.ts`
- Manages session lifecycle  
- Handles token storage and cleanup  

#### `/src/security/AuthorizationService.ts`
- Validates user roles and permissions  
- Provides helper methods such as:
  - `hasRole(role)`
  - `hasPermission(permission)`

#### `/src/security/AuthGuard.tsx`
- Protects routes and components  
- Redirects unauthorized users  

---

### Data Storage Strategy

#### Public Configuration (Frontend)

Stored as environment variables:

- API base URL  
- Environment name  
- Entra ID tenant ID and client ID  

---

#### Sensitive Data

Stored in:

- **Azure Key Vault**

Includes:
- API keys  
- Secrets  
- Certificates  

Sensitive data is never exposed to the frontend.

---

### Secure Storage Service

- Azure Key Vault  

Used for secure storage of:
- Secrets  
- Keys  
- Certificates  

Access controlled through Azure RBAC.

---

### Environment Configuration Flow

1. Secrets stored in Azure Key Vault  
2. Azure DevOps retrieves secrets securely  
3. Deployment injects configuration into Azure App Service  
4. Frontend consumes only non-sensitive variables  
5. Backend securely accesses sensitive data  


## 1.5 Layered Design

The frontend application follows a layered architecture to ensure separation of concerns, scalability, and maintainability.

---

### Rendering Flow

The frontend performs Server-Side Rendering (SSR) using Node.js and React in Azure App Service.

- If no authenticated session exists, the Authentication Layer is invoked  
- If authentication is successful, the visual resource is rendered through the Components Layer  

---

### Authentication Layer

Responsible for handling user authentication and session validation.

- Integrates with Microsoft Entra ID using MSAL  
- Manages authentication state and session lifecycle  
- Controls access to protected resources before rendering UI components

--- 

### Components Layer

Responsible for rendering the user interface.

- Follows Atomic Design:
  - Atoms → Molecules → Organisms → Templates → Pages  
- Handles user interaction and visual representation  

Within this layer, a **Hooks Layer** is used to connect UI actions with business logic.

---

### Hooks Layer

Acts as the connection between UI components and application logic.

- Captures user interactions  
- Manages local UI state and side effects  
- Delegates operations to the Services Layer  

---

### Services Layer

Contains the core application operations.

- Handles DUA generation, monitoring, and export processes  
- Orchestrates business logic  
- Coordinates API interactions  

Services may access:

- Utils  
- ApiClients  
- Settings  

---

### ApiClients Layer

Responsible for communication with external APIs.

- Implements HTTP calls using axios  
- Encapsulates endpoints and request logic  
- Reads API URLs and keys from the Settings Layer  

All requests and responses use Models validated by the Data Validation Layer.

---

### Settings Layer

Manages application configuration.

- Reads environment variables from Azure App Service  
- Provides configuration values injected at build or runtime, sourced from Azure Key Vault through secure backend and deployment pipelines.
- Provides API URLs, environment settings, and identifiers  

---

### Data Validation Layer

Ensures data integrity across the system.

- Implemented using Zod  
- Validates all API requests and responses  
- Enforces data contracts using Models  

---

### Models Layer

Defines shared data structures.

- Used across Services, ApiClients, and Components  
- Represents domain entities such as DUA data and process results  

---

### State Management Layer

Manages application state.

- Server state handled by React Query  
- Client state handled by Zustand  

All layers can access state when required.

---

### Notification Service Layer

Handles asynchronous communication.

- Allows layers to subscribe to events  
- Supports callback-based updates from external APIs  
- Used for long-running processes such as DUA generation  

All asynchronous API interactions are handled via callbacks through this layer.

---

### Utils Layer

Provides reusable helper functions.

- Shared across all layers  
- Includes formatting, parsing, and common logic  

---

### Logging Layer

Responsible for system monitoring.

- Registers events and errors  
- Sends logs to Azure Application Insights via ApiClients  

---

### Exception Handling Layer

Provides centralized error handling.

- Standardizes error responses  
- Prevents application crashes  
- Shared across all layers  

---

### Layer Interaction Rules

- Components interact only with Hooks  
- Hooks interact with Services  
- Services interact with ApiClients, Utils, and Settings  
- ApiClients interact with external APIs  
- All layers can access Models, Utils, and State Management  
- Asynchronous communication is handled through the Notification Service Layer  

---

### High-Level Flow

User → Browser → Azure App Service → SSR → Authentication → Components → Hooks → Services → ApiClients → External APIs  

External APIs → Notification Service → Services → Hooks → Components → UI Update  

## 1.6 Design Patterns

The frontend applies object-oriented design patterns to ensure scalability, maintainability, and clear separation of responsibilities across the application.

---

### Adapter Pattern

Used to decouple frontend logic from backend API structures.

#### Purpose
- Transform API responses into frontend-friendly models  
- Isolate changes in backend contracts  

#### Classes and Location

- `/src/api/adapters/AuthApiAdapter.ts`
- `/src/api/adapters/GeneratorApiAdapter.ts`
- `/src/api/adapters/MonitoringApiAdapter.ts`
- `/src/api/adapters/ExportApiAdapter.ts`

#### Responsibilities

- Delegate HTTP communication to the ApiClients layer  
- Map responses to Models  
- Handle API errors consistently  

---

### Observer Pattern (Notification Service)

Used for event-driven communication and asynchronous updates.

#### Purpose
- Notify components about long-running processes  
- Enable subscription to backend events  

#### Classes and Location

- `/src/services/NotificationService.ts`

#### Responsibilities

- Manage event subscriptions  
- Dispatch updates to subscribers  
- Handle callback-based communication for async processes  

---

### Singleton Pattern

Used to ensure a single shared instance of critical services.

#### Purpose
- Centralize shared logic  
- Avoid duplicated instances across the application  

#### Classes and Location

- `/src/security/AuthService.ts`
- `/src/security/SessionManager.ts`
- `/src/services/NotificationService.ts`
- `/src/services/TelemetryService.ts`
- `/src/config/SettingsService.ts`
- `/src/utils/Logger.ts`

#### Responsibilities

- Maintain global state consistency  
- Provide shared access to configuration and services  

---

### Strategy Pattern

Used to define interchangeable behaviors for processing operations.

#### Purpose
- Allow different strategies for handling workflows such as:
  - File validation  
  - Data processing  
  - Export behavior  

#### Classes and Location

- `/src/services/strategies/GenerationStrategy.ts`
- `/src/services/strategies/ValidationStrategy.ts`
- `/src/services/strategies/ExportStrategy.ts`

#### Responsibilities

- Define interchangeable algorithms  
- Allow runtime selection of behavior  

---

### Factory Pattern

Used for controlled object creation.

#### Purpose
- Centralize instantiation logic  
- Avoid direct dependency on concrete implementations  

#### Classes and Location

- `/src/factories/ServiceFactory.ts`

#### Responsibilities

- Create service instances  
- Provide configured objects based on context  

---

### State Management Pattern

Implements centralized state handling.

#### Purpose
- Maintain predictable application state  
- Synchronize UI with backend data  

#### Implementation

- React Query → Server state  
- Zustand → Client state  

#### Location

- `/src/state/`

---

### Guard Pattern (Security)

Used to protect routes and components.

#### Purpose
- Restrict access based on authentication and authorization  

#### Classes and Location

- `/src/security/AuthGuard.tsx`

#### Responsibilities

- Validate user session  
- Check roles and permissions  
- Redirect unauthorized users  

---

### Interceptor Pattern

Used for cross-cutting concerns in API communication.

#### Purpose
- Automatically attach tokens to requests  
- Handle global API errors  

#### Classes and Location

- `/src/api/interceptors/AxiosInterceptor.ts`

#### Responsibilities

- Inject authentication tokens  
- Handle response errors globally  

---

### Error Handling Pattern

Provides centralized exception management.

#### Purpose
- Standardize error handling across the application  
- Prevent UI crashes  

#### Classes and Location

- `/src/core/ExceptionHandler.ts`

---

### Event-Driven Programming

The system follows an event-driven approach for asynchronous operations.

#### Purpose
- Handle long-running processes (DUA generation)  
- Update UI without blocking execution  

#### Implementation

- NotificationService (Observer pattern)  
- React Query polling and cache invalidation  

---

### Summary

The combination of these patterns ensures:

- Loose coupling between layers  
- Reusable and scalable components  
- Clear separation of concerns  
- Robust handling of asynchronous workflows  

## 1.7 Project Scaffold (/src)

The following folder structure represents the frontend scaffold derived from the defined technology stack, layered architecture, component strategy, and design patterns.



- [app](./src/app)
- [api](./src/api)
- [components](./src/components)
- [config](./src/config)
- [core](./src/core)
- [factories](./src/factories)
- [hooks](./src/hooks)
- [i18n](./src/i18n)
- [models](./src/models)
- [security](./src/security)
- [services](./src/services)
- [state](./src/state)
- [styles](./src/styles)
- [types](./src/types)
- [utils](./src/utils)
- [validation](./src/validation)

## 2. Backend Design

### 2.1 Technology Stack

- Architecture Style: Modular Monolith (Service-based architecture)

- API Type: REST API over HTTPS

- Cloud Provider: Microsoft Azure

- API Gateway: Azure API Management

- Hosting Service: Azure App Service

- API Standard: OpenAPI Specification (Swagger)

- Asynchronous Processing & Notifications: Azure Notification Hubs

- Load Balancing: Not required for current scope

- Backend Runtime: Node.js v21

- Programming Language: TypeScript v5.9.3

- Web Framework: Express.js

- Repository Strategy: Monorepo (shared with frontend)

- Backend Folder: /duabusiness

### 2.2 Security

The backend security design is aligned with the frontend authentication and authorization strategy, ensuring secure communication, data protection, and controlled access to resources.

---

#### Communication Security

- All API communication is secured using HTTPS (TLS 1.2 or higher)
- Data in transit is encrypted end-to-end between client and backend services

---

#### Authentication & Authorization

- Authentication is handled using Microsoft Entra ID (OAuth 2.0 / OpenID Connect)
- Access tokens (JWT) are required for all protected endpoints
- Token validation is performed in the backend before processing any request
- Role-based access control (RBAC) is enforced for protected operations

---

#### Data Encryption

- Sensitive data stored in the database is encrypted using AES-256 encryption
- Encryption keys are managed through Azure Key Vault
- No sensitive data is stored in plain text

---

#### Payload Size Limits

- Default maximum payload size: 10 MB
- Exceptions allowed for document upload endpoints (up to 50 MB)
- Payload limits are enforced at API Gateway (Azure API Management) level

---

#### Rate Limiting

- Rate limiting is applied to prevent abuse and ensure availability
- Maximum requests per client: 100 requests per minute
- Concurrent request limit: 20 active requests per client
- Policies enforced through Azure API Management

---

#### Data Retention Policy

- Operational data is stored in production for up to 30 days
- After this period, data is moved to an archive storage
- Archived data is stored in a lower-cost storage tier (Azure Blob Storage Archive)
- Data retention policies comply with audit and traceability requirements

---

#### Secure Configuration Management

- Secrets and sensitive configurations are stored in Azure Key Vault
- API keys, connection strings, and credentials are never hardcoded
- Environment variables are injected during deployment via Azure DevOps

---

#### Logging and Monitoring Security

- Security events and access logs are recorded using Azure Application Insights
- Suspicious activity (e.g., failed authentication attempts) is monitored
- Logs are protected and access-controlled


### 2.3 Observability

The backend observability strategy is aligned with the frontend, enabling end-to-end monitoring, traceability, and system diagnostics.

---

#### Event Logging

The system records the following types of events:

- Authentication events (login success, login failure, token validation)
- API request lifecycle (request received, response sent, response time)
- DUA generation process events (start, progress, completion, failure)
- File processing events (document read, validation success/failure)
- External API calls (request, response, errors)
- Error and exception events
- Rate limiting and security events
- User actions related to core workflows (configuration, export)

---

#### Observability Platform

- Azure Application Insights is used as the central observability platform
- Integrated with both frontend and backend
- Collects logs, metrics, traces, and performance data
- Supports distributed tracing across services

---

#### Dashboards and Monitoring

- Azure Monitor is used to create dashboards and visualize system metrics
- Key dashboards include:
  - API performance (latency, throughput)
  - Error rates and failure analysis
  - DUA processing status and success rate
  - User activity and interaction patterns

- Custom queries are created using Kusto Query Language (KQL) for advanced analysis

---

#### Alerting

- Alerts are configured based on:
  - High error rates
  - API latency thresholds
  - Failed DUA generation processes
  - Unusual traffic patterns

- Alerts are managed through Azure Monitor

---

#### Traceability

- Each request is assigned a unique correlation ID
- Correlation IDs are propagated across all layers
- Enables full traceability from frontend to backend and external services


### 2.4 Infrastructure (DevOps)

The infrastructure and DevOps strategy is based on Microsoft Azure and Azure DevOps, enabling automated builds, deployments, and environment management.

---

#### CI/CD Automation

- CI/CD processes are managed using Azure DevOps Pipelines
- Pipelines are triggered automatically on code changes (push, pull requests)
- Includes:
  - Build validation
  - Automated testing (unit and integration)
  - Code quality checks (ESLint, Prettier)
  - Artifact generation

---

#### Code Repository Integration

- Source code is managed in Azure DevOps Repos
- Monorepo structure shared between frontend and backend
- Branching strategy:
  - main (production)
  - develop (integration)
  - feature branches

---

#### Deployment Strategy

- Deployments are automated using Azure DevOps Pipelines
- Backend is deployed to Azure App Service

Environment strategy:

- Development:
  - Continuous deployment enabled
  - Used for active development and testing

- QA / Staging:
  - Deployment triggered after successful validation
  - Used for integration testing and validation

- Production:
  - Manual approval required before deployment
  - Stable and validated releases only

---

#### Environment Management

- Environments are managed using Azure DevOps Environments
- Azure App Service Deployment Slots are used:
  - staging slot for pre-production validation
  - production slot for live environment
- Enables safe deployments and rollback strategies

---

#### Infrastructure as Code (IaC)

- Infrastructure provisioning can be managed using:
  - Azure Resource Manager (ARM) templates or Bicep

- Defines:
  - App Service configuration
  - API Management
  - Key Vault
  - Monitoring resources

---

#### Secrets and Configuration Management

- Secrets are stored in Azure Key Vault
- Integrated with Azure DevOps through variable groups
- No sensitive data is stored in the repository

---

#### Release Strategy

- Incremental deployments through CI/CD pipelines
- Version-controlled releases
- Rollback supported via deployment slots

### 2.5 Availability

The system is designed to achieve high availability with a target uptime of 99.99%.

---

#### Availability Target

- Target uptime: 99.99% annually
- Maximum allowed downtime: ~52 minutes per year

---

#### High Availability Strategy

The system leverages managed Azure services with built-in high availability:

- Azure App Service:
  - Provides automatic scaling and fault tolerance within a region
  - SLA: 99.95% (single region)

- Azure API Management:
  - Ensures reliable API gateway availability
  - Supports multi-region deployment (optional for higher availability)

- Azure Key Vault:
  - High availability for secrets and configuration management

- Azure Application Insights:
  - Monitoring and diagnostics for proactive issue detection

---

#### Single Points of Failure

Potential single points of failure identified:

- Single-region deployment of Azure App Service
- API Management deployed in a single region
- External API dependencies

---

#### Recovery and Mitigation Strategies

To achieve the target availability, the following strategies are applied:

- Multi-region deployment (optional enhancement):
  - Deploy backend services in multiple Azure regions
  - Use traffic routing (Azure Front Door) for failover

- Deployment Slots:
  - Zero-downtime deployments using staging and production slots

- Retry and Resilience Policies:
  - Implement retries and timeouts for external API calls

- Health Checks:
  - Continuous monitoring of service health

- Backup and Recovery:
  - Regular backups of configuration and critical data
  - Fast recovery procedures for service restoration

---

#### Failure Handling

- Failures are detected using Azure Monitor and Application Insights
- Alerts are triggered for critical issues
- Automated and manual recovery procedures are defined

---

#### Summary

Although some Azure services provide 99.95% SLA by default, the system can achieve higher availability through redundancy, failover strategies, and proper monitoring and recovery mechanisms.

### 2.6 Scalability

The system is designed to handle increasing request loads by scaling key components of the architecture.

---

#### Scalable Components

The following elements scale as the number of requests per minute increases:

- Azure App Service:
  - Supports horizontal scaling (scale-out by adding instances)
  - Handles increased API traffic and concurrent requests

- Azure API Management:
  - Scales to handle increased API gateway traffic
  - Manages request routing, throttling, and caching

- Asynchronous Processing (Notification Hubs):
  - Decouples long-running processes from user requests
  - Allows the system to handle high loads without blocking operations

- React Query (Frontend - Server State):
  - Reduces backend load through caching and request deduplication
  - Minimizes unnecessary API calls

---

#### Scaling Strategy

- Horizontal scaling is preferred over vertical scaling
- Auto-scaling rules can be configured based on:
  - CPU usage
  - Memory consumption
  - Request count

---

#### Performance Optimization

- Use of asynchronous processing for DUA generation tasks
- Caching strategies to reduce repeated requests
- Efficient API design to minimize payload size and processing time

---

#### Summary

The system scales dynamically by increasing the number of service instances and optimizing request handling, ensuring consistent performance under higher loads.

### 2.7 Backend Key Workflows

This section defines the main backend workflows for the DUA Streamliner system, describing the sequence of operations performed by the backend services.

---

#### Upload Files to Generate DUA

1. The backend receives a request containing the list of files to be uploaded.

2. The backend validates the request metadata and authentication token.

3. A streaming process is initiated to receive each file in raw binary format.

4. Each file is processed sequentially or in parallel depending on size and configuration.

5. The backend stores each file in Azure Blob Storage.

6. Metadata for each file is recorded in the database (file name, type, size, upload date, and reference ID).

7. The backend validates supported formats (PDF, DOCX, XLSX, images).

8. If any file is invalid, the system flags it and continues processing the remaining files.

9. Once all files are uploaded, the backend confirms successful storage.

10. A processing job is created to start document analysis and DUA generation.

11. The workflow triggers an asynchronous process for document reading and data extraction.

---

#### Setup DUA Template

1. The backend receives a request to configure the DUA template.

2. The system validates the template format and structure.

3. The template is stored in Azure Blob Storage.

4. Template metadata is registered in the database (version, format, upload date).

5. The backend associates the selected template with the current DUA generation process.

6. The system validates compatibility between uploaded documents and the selected template.

7. If inconsistencies are detected, the system flags them for review.

8. The configuration is stored and marked as ready for processing.

---

#### DUA Generation Process (Asynchronous)

1. The backend starts the document processing job.

2. Files are retrieved from Azure Blob Storage.

3. Text extraction is performed:
   - Structured data (Excel, Word)
   - Unstructured data (PDF)
   - OCR processing for images

4. Extracted data is processed using semantic analysis.

5. Relevant fields are identified (importer, goods, values, transport, etc.).

6. Data is validated and normalized.

7. Extracted information is mapped to the DUA template structure.

8. Confidence levels are assigned to each field.

9. The generated DUA document is created in .docx format.

10. The result is stored in Azure Blob Storage.

11. The process status is updated (completed / failed).

12. A notification event is triggered to inform the frontend.

---

#### Export Generated DUA

1. The backend receives a request to export the generated DUA.

2. The system validates user authorization.

3. The generated file is retrieved from Azure Blob Storage.

4. The file is prepared for download.

5. The backend returns the file to the client.

6. The export event is logged for auditing purposes.


### 2.8 Architecture Diagrams (C4 Model)

The system architecture is described using the C4 model, including Context, Container, and Code diagrams.

---

## 2.8.1 Context Diagram

This diagram shows the system boundaries and its interaction with external actors and systems.

**Actors:**
- End User (Importer / Exporter)
- External Authentication Provider (Microsoft Entra ID)

**External Systems:**
- Azure Blob Storage
- External Document Processing / OCR Services (optional)

```mermaid
graph TD

User[End User]
FE[Frontend Application (React)]
BE[DUA Streamliner Backend]
Auth[Microsoft Entra ID]
Storage[Azure Blob Storage]

User -->|Uses| FE
FE -->|HTTPS REST API| BE
FE -->|Authentication (OAuth2)| Auth
BE -->|Validate Token| Auth
BE -->|Store/Retrieve Files| Storage
