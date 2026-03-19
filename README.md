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
- Accesses secure configuration from Azure Key Vault  
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

## 1.6 Design Patterns: Design of classes and their respective locations in the project structure where object-oriented design patterns are applied when necessary. Examples include: security, UI refresh, notification handling, state storage, API calls, asynchronous operations, session invalidation, event-driven programming, and object creation.

## 1.7 Project Scaffold: A folder in /src containing the project scaffold, generated based on the full specification defined in sections 1.1 through 1.6.
