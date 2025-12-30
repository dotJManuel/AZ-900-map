---
title: AZ-900 Azure Fundamentals (Mapa Mental Detallado)
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
---

## Azure Infrastructure
- Regiones (60+): ubicación geográfica de recursos
- Availability Zones: datacenters aislados con redundancia
- Pares de regiones (Region Pairs)
- Data Centers centralizados y seguros

## Azure Compute
- **Azure Virtual Machines (VMs)**
  - IaaS: control total
  - Imágenes, tamaño, discos
  - Load Balancer
  - Scale Sets: autoescalado
  - Availability Sets y Zones (Virtual Machine Scale Sets)
    - create and manage a group of Azure VMs
    - Distribute across Multiple AZs
    - load balancer - Manual Scaling and Auto Scaling
    - 1,000 VM instances
  - Spot & Reserved Instances
    - Reserved VM Instances (1 or 3 years)
    - Spot Instances -  Create cheaper, temporary instances for non critical workloads
  - Availability
    - Premium SSD or Ultra Disk: 99.9%
    - Standard SSD Managed Disks: 99.5%
    - Standard HDD Managed Disks: 95%
    - Two or more instances in same Availability Set: 99.95%
    - Two or more instances in two or more Availability Zones in the same Azure region: 99.99%
  - Static IP Address
    - Assign a fixed IP address to your VM
    - Public IP addresses are charged per IP per hour
  - Scaling
    - Vertical Scaling
      - Deploying application/database to bigger instance
      - A larger hard drive - A faster CPU - More RAM, CPU, I/O, or networking capabilities
    - Horizontal Scaling
      -  Deploying multiple instances of application/database
      -  needs additional infrastructure - Scaling Sets, Load Balancers etc.
      -  has limits, can be expensive,increases availability

## Support & SLA
- SLA:
  - 99.9% → 43 min/mes
  - 99.95% 22 min/mes
  - 99.99% → 4.5 min/mes
    -  Most online apps aim for 99.99% (four 9's)
  - 99.999% → 26 seg/mes

## Managed Services
- **IAAS (Infrastructure as a Service)**
  - Use only infrastructure from cloud provider
  - Example: Using VM to deploy your applications or databases
  -  You are responsible for:
      - Application Code and Runtime
      - Configuring load balancing
      - Auto scaling
      - OS upgrades and patches
      - Availability, etc.
- **PAAS (Platform as a Service)**
  - Use a platform provided by cloud
  - Cloud provider is responsible for:
    - OS (incl. upgrades and patches)
    - Application Runtime
    - Auto scaling, Availability & Load balancing etc..
  - You are responsible for:
    - Configuration (of Application and Services)
    - Application code (if needed)
  - Examples
    - **Azure App Service (PaaS)**
      - Web apps, APIs, backends
      - Escalado automático, balanceo de carga
    - **Microservices**
    - **Containers**
      - Azure Container Instances (ACI) (CaaS)
        - Manage and run simple container based applications
      - Container Orchestration
        -  Auto Scaling
        -  Service Discovery - Help microservices find one another
        -  Load Balancer
        -  Self Healing (Autorecuperación) - Do health checks and replace failing instances
        -  Zero Downtime Deployments - Release new versions without downtime
        - Azure Kubernetes Service (AKS) (CaaS)
          - aplicaciones que necesitan escalabilidad, balanceo de carga y administración centralizada
          - estándar de código abierto para la orquestación de contenedores
          - microservicios en contenedores, inteligencia artificial, big data y desarrollo ágil
        - Azure Service Fabric (CaaS)
          - manejo más granular de los microservicios -  on premises and in the cloud
          - Microsoft's container orchestrator
          - Aplicaciones empresariales con lógica compleja
    - **Serverless (FaaS)**
      - Pay for use
      - Azure Functions
      - Ejecuta código, paga solo por uso
- **SaaS (Soware as a Service)**
  - Centrally hosted soware (mostly on the cloud) - Offered on a subscription basis (pay-as-you-go)
  -  Email, calendaring & office tools 
  -  Cloud provider is responsible for:
     - OS (incl. upgrades and patches)
     - Application Runtime
     - Auto scaling, Availability & Load balancing etc..
     - Application code and/or
     - Application Configuration (How much memory? How many instances? ..)
  - Customer is responsible for:
    - Configuring the soware!

## Responsibilities
| **Responsibility** | **SaaS**     | **PaaS**     | **IaaS**     | **On-prem**  |
| - | - | - | - | - |
| **Responsabilidad siempre de cliente** | | | | |
| Información y datos | Customer | Customer | Customer | Customer |
| Dispositivos (móviles y PCs) | Customer | Customer | Customer | Customer |
| Cuentas e identidades | Customer | Customer | Customer | Customer |
| **Responsabilidad compartida o variable** | | | | |
| Infraestructura de identidad y directorio | Shared | Shared | Customer | Customer |
| Aplicaciones | Microsoft | Shared | Customer | Customer |
| Controles de red | Microsoft | Shared | Customer | Customer |
| Sistema operativo | Microsoft | Microsoft | Customer | Customer |
| **Responsabilidad del proveedor cloud** | | | | |
| Hosts físicos | Microsoft | Microsoft | Microsoft | Customer |
| Red física | Microsoft | Microsoft | Microsoft | Customer |
| Centro de datos físico | Microsoft | Microsoft | Microsoft | Customer |

## ⌯⌲ Azure Storage
- Tipos:
  - Block Storage
  - File Storage
  - Object Storage
- **Azure Disk**
  - Types
    - Standard HDD - Backup, non-critical, infrequent access
    - Standard SSD - Web servers, lightly used enterprise applications and dev/test environments
    - Premium SSD disks - production and performance sensitive workloads
    - Ultra disks (SSD) - IO-intensive workloads, top tier databases (SQL, Oracle)
- **Azure Files**
  - Protocols
    - Server Message Block (SMB) 
    - Network File System (NFS)
  - Azure File Sync
    - SMB, NFS, and FTPS
- **⌯⌲ Azure Blobs**
  - Three Types
    - Block Blobs: Store text or binary files (videos, archives etc)
    - Append Blobs: Store log files (Ideal for append operations)
    - Page Blobs: Foundation for Azure IaaS Disks (512-byte pages up to 8 TB)
  - Azure Data Lake Storage Gen2
  - ⌯⌲ Tiers
    - Hot: Store frequently accessed data
    - Cool: Infrequently for min 30 days
    - Cold: Infrequently for min 90 days
    - Archive: Rarely for min 180 days
- **Azure Queues**
  - Decouple applications using messaging
- **Azure Tables**
  - Azure Cosmos DB for NoSQL
- **Redundancia:**
  -  Locally redundant storage (LRS)
     -  Three synchronous copies in same data center
  - Zone-redundant storage (ZRS) 
    - Three synchronous copies in three AZs in the primary region
  - Geo-redundant storage (GRS)
    - LRS + Asynchronous copy to secondary region (three more copies using LRS)
  - Geo-zone-redundant storage (GZRS)
    - ZRS + Asynchronous copy to secondary region (three more copies using LRS)
  - RA-GRS - Read-access geo-redundant storage
  - RA-GZRS - Read-access geo-zone-redundant storage
- **Region pairs**
  - Data copies across regions => high availability + high durability
  -  Examples: Central India & South India, East US & West US
- Herramientas:
  - Azure Storage Explorer: GUI
  - AzCopy: Command-line utility
- Premium Storage Account
  -  high-performance storage with low latency and high throughput

## Azure Databases
- Relacionales:
  - OLTP (Online Transaction Processing)
    - Transactional usecases needing predefined schema and very strong transactional
    - databases use row storage
    - Azure SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL
  - OLAP (Online Analytics Processing)
    - to analyze petabytes of data Datawarehousing & BigData workloads
    - databases use columnar storage with predefined schema
    - Azure Synapse Analytics
- NoSQL = not only SQL
  - quickly evolving structure (schema-less)
  - Azure Cosmos DB
    - Supports APIs
      - MongoDB (document)
      - Cassandra (key/value)
      - Gremlin (graph)
- En memoria:
  - Applications needing microsecond responses - persistent data in memory
  - Azure Cache for Redis
  - Use cases: Caching, session management, gaming leader boards, geospatial applications
- Conceptos clave:
  - Durabilidad (11 9’s)
    - Multiple copies of data (standbys, snapshots, transaction logs and replicas)
  - Disponibilidad (4-5 9’s)
    - multiple standbys o distribute the database (Zones, Regions)
  - RPO (Recovery Point Objective): Maximum acceptable period of data loss
  - RTO (Recovery Time Objective): Maximum acceptable downtime
  - Consistencia: fuerte, eventual, read-after-write
    - Strong consistency - Synchronous replication to all replicas
    - Eventual consistency - Asynchronous replication. A little lag few seconds

## Networking
- **VNet (Red Virtual)**
  - Subnets públicas y privadas
  - IPs privadas/públicas
  - Azure Virtual Network
    - Your own isolated network in Azure - asociada con una región.
    - Every VM in a VNet is assigned a private IP address
    - VMs in the same VNet can communicate using private IP addresses
    - **Network peering** can be use to connect resources in different Virtual Networks, potentially in different regions
- **Seguridad**
  - Azure DDoS
    - (DDoS) attack: Large scale attacks to bring your apps down
    - DDoS Protection Basic: Protects against common network layer attacks
    - DDoS Protection Standard: Mitigates 60 different DDoS attack types
  - Azure Firewall
    - Managed network security service to control traffic in and out of a Azure Virtual Network
    - Azure Firewall is an external firewall - outside your Virtual Network
    - Web application firewall (WAF): Restrict traffic into web applications
  - NSG (Network Security Group)
    - is like a internal firewall inside your Virtual Network right before your resources
    - Multiple inbound and outbound security rules
      - Allow or block traffic based on source/destination IP address, protocol and port
      - Restrict traffic between resources
      - Attached with subnets and network interfaces
- **Acceso privado**
  - Azure Private Link
    - Setup private link and connect using private endpoint
  - Azure Bastion
    - A special-purpose server designed to provide secure access to a private network from an external network
    - Acts as a gateway

## Hybrid Cloud
- **Cloud Computing**
  - Public Cloud
  - Private Cloud
  - Hybrid Cloud 
    - Connecting Azure with on-premises
    - Azure VPN 
      - Encrypted connection from on-premises to Azure over internet
      - Point-to-site VPN: From a computer to Azure
      - Site-to-site VPN: From your on-premises VPN device or gateway to the Azure VPN gateway in a virtual network
    - Azure ExpressRoute
      - Private connectivity to Azure VNet
      - Does NOT use internet
  - Azure Arc
    - Manage multi cloud and on-premise infrastructure from one place
  - VMWare
    - A leading provider of virtualization software
    - multiple virtual machines (VMs) to run on a single physical server
## Organizing and Managing Azure Resources 
  - Hierarchy
    - **Management groups**
      - can have a hierarchy
      - All under a Management Group inherit all constraints applied to it
        - access  
        - policies
        - compliance 
    - **Subscriptions**
      - An Azure Account can have 
        - multiple subscriptions
        - multiple account administrators
      -  Two Subscriptions CANNOT be merged into one
         -  move resources from one to another
         -  transfer ownership of a subscription
    - **Resource groups**
      - can access resources in other Resource Groups
    - **Resources** 
  - Naming and Tagging Strategy
    - Helps in quickly locating and managing resources
    - Naming Pattern
    - Assign Multiple Tags
      - Assign tags to identify
        - Business unit
        - Application
        - Workload
        - Environment
    - Implementation
      - **Azure Resource Manager (ARM) templates** to assign tags
      - **Azure Policy** to enforce tagging rules and conventions

## Core Azure identity services
- **Active Directory**
  - Authentication and Authorization
  - Supports groups
  - Primarily used in on-premises
- **Active Directory Federation Services (AD FS)**
  - Single Sign-On (SSO)
    -  logging into multiple apps and services with the same credentials
  - Convenience
    - reducing the need to remember multiple passwords
- **Microsoft Entra ID (Azure AD)**
  - Active Directory Service in Azure
  - Autenticación y autorización
    - Single Sign-On (SSO)
    - MFA (Multi Factor Authentication)
      - Something you know, typically a password.
      - Something you have, trusted device
      - Something you are, fingerprint or face scan
    - Passwordless (Windows Hello, Microsoft Authenticator app, FIDO2(Fast IDentity Online) security keys)
      - FIDO - open standard for passwordless authentication
      - FIDO2 - enables users to use common devices to authenticate to online
 services (mobile and desktop)
    - Microso Entra self-service password reset
  - Extra
    - Multiple subscriptions can trust the same Microsoft Entra ID directory
    - each subscription can only trust only one directory
    - Microsoft Entra ID Connect (NOT Microsoft Entra ID Conditional Access) can be used synchronize on-premises Active Directory with Microsoft Entra ID
- **Role-Based Access Control (RBAC)**
  - Rol, Alcance, Asignación
  - Scope: recurso → grupo → suscripción → grupo de gestión
- **Conditional Access**
- **Entra Connect**
  - Synchronize on-premises Active Directory with Microsoft Entra ID
  - User Details Synchronization
  - Unified Identity
  - Seamless Integration
  - Hybrid Identity

<!-- 139 -->
## ⌯⌲ Security
- **Microsoft Defender for Cloud**
  - Cloud security posture management (CSPM)
    - Automate identification & remediation of security risks of your cloud configuration
  - Cloud workload protection (CWP)
    - Continuously monitor and fix threats to workloads deployed in the cloud
  - Protect your multicloud and hybrid cloud environments
  - Features
    - Continuous assessment: Understand your current security posture
    - Secure: Harden all connected resources and services
    - Defend: Detect and resolve threats to resources and services
  - Formerly called Azure Security Center
- **Just-in-Time (JIT) VM Access**
  - Reduce the attack surface of your virtual machines
  - User Access Verification
  - Dynamic Configuration by Defender for Cloud
    - Network Security Groups (NSGs) and Azure Firewall
      - Permit access to the specified ports
      - Restrict access to the relevant IP address
      - Grant access for a specified amount of time
- **Microsoft Sentinel**
  - Security information and event management (SIEM)
    -  Collect and analyze log data from various sources to identify potential threats
  - Security orchestration, automation, and response (SOAR)
    - Prioritizes alerts based on threat levels
  - Scalable and Flexible
  - Event Storage
  - Automation and Playbooks 
    -  Automated Response - Automatically fix issues with built-in automation capabilities
    -  Playbooks - Use playbooks to automate and orchestrate response actions
- **Azure Key Vault**
  - Securely store and access secrets: API keys, passwords, certificates
- **Zero Trust**
  - Microsoft's modern security strategy
  - Verificación explícita: Use all info - identity, location, device, resource, data classification, time
  - Menor privilegio
  - Asumir brecha
- **⌯⌲ Defense in Depth**
  - Physical security, Identity and access, Perimeter, Network, Compute, Application, Data

## Resource Management
- Jerarquía:
  - Management Groups > Subscriptions > Resource Groups > Resources
- **Resource Groups**
  - Lógica organizativa
  - Contiene recursos de múltiples regiones
- **Tags & Naming**
  - Organización por BU, entorno, aplicación
- **Azure Policy**
  - Enforce reglas
- **Plantillas ARM**
  - Infraestructura como código

<!-- 150 -->
## Azure management tools
- **Azure support plans**
  - Basic, Developer, Standard, Professional Direct
- **Azure Monitor**
  - Analiza y visualiza Logs, métricas, alertas
  - Application Insights
  - VM/container insights
- **Log Analytics**
  - Consultas avanzadas
  - Collects log and performance data from monitored resources
- **Azure Advisor**
  - Recomendaciones automatizadas para:
    - Costos
    - Seguridad
    - Fiabilidad
    - Rendimiento
- **Azure Service Health**
  - Personalized alerts and guidance for Azure *service* issues
  - Hierarchy
    - Azure Status: Global view of the health of Azure services and regions
    - Azure Service Health: Personalized dashboard based on your Azure usage
    - Azure Resource Health: individual cloud resources
- **Reliability (Fiabilidad)**
  - Ensuring continuous operation & automatic recovery from failures
- **Predictability (Previsibilidad)**
  - Ensuring consistent performance and costs
  - Performance Predictability
    - Autoscaling, Load Balancing
  - Cost Predictability
    - Cost Estimation Tools, Resource Monitoring

<!-- 160 -->
## Azure governance features
- Azure Policy
  - Governance for resource consistency, regulatory compliance security cost and management
  - It is applied to a new resources, it does not impact existing resources.
- Azure Blueprints
  - One or more of (Policy + Role + ARM template + Resource Group) configurations
  - compliance with organizational standards
    - Australian Government, UK OFFICIAL, Azure Security Benchmark, Basic Networking, FedRAMP, HIPAA etc
- Resource Locks
  - Prevent accidental deletion/modification of resources. multiple locks at different levels
    - ReadOnlyLock
    - CannotDelete
- The Need for Data Governance
  - Data Proliferation, Regulatory Compliance, Data Security, Data Quality, Data Lineage and Auditing
- Microsoft Purview
  - Unified Data Governance,  Data Discovery and Classification, Data Catalog, Data Access Policies, Integration

## Privacy and Compliance
- Privacy & Information Protection
  - Microsoft Privacy Statement
    - how Microsoft processes it, and for what purposes
  - Product Terms Site
    - Terms and conditions for software and online services
  - Data Protection Addendum (DPA)
    - Your and Microsoft's obligations with respect to the processing and security of Customer Data and Personal Data in connection with Azure
      - Covers Data transfer, Data retention, Data deletion and Data Security
  - Azure Information Protection
     - Classify and protect your documents and emails
        - independent of the location, networks, file servers, and applications
    -  Uses Azure Rights Management (Azure RMS) 
       - Integrates with Office 365, Azure Active Directory etc
- Compliance & Azure
  - adhere to several industry and security standards
    - Service Trust Portal
  - Azure Compliance Hub
    - Azure Security and Compliance Blueprints - ISO:27001, PCI DSS etc
  - Azure Compliance Manager - Part of Service Trust Portal
    - Automates complete compliance lifecycle
      - Manage Risks, Implement Controls, Check compliance against regulations and standards,Reporting to Auditors
  - 90+ Azure compliance offerings
    -  grouped into: Global, US government, industry specific, and region/country specific
       - 50+ global regions and countries (the US, the European Union, Germany, etc.)
       - 35+ key industries ( health, government, finance etc)
  -  Important Standards
     - International Organization for Standardization (ISO): ISO:27001 (Security controls), ISO:27017(Security controls for use of cloud services), ISO:27701 (privacy standard), ISO:27018 (privacy on cloud)
     - Service Organization Compliance (SOC): SOC-1 (Auditing standard), SOC-2 (Assessment of service provider controls)
     - General Data Protection Regulation (GDPR): Strengthens personal data protection in Europe
     - Health Insurance Portability & Accountability Act (HIPAA): Data privacy & security requirements for organizations handling PHI
     - Payment Card Industry - Data Security Standards (PCI-DSS)
   - Azure Sovereign Regions
     -  Azure global, Azure Government (US), Azure China, Azure Germany
  
<!-- 174 -->
## Azure cost management
  - Consumption-based
    - You are billed for only what you use
      - Azure Functions - You pay for num of invocations!
  - Fixed-price
    - You are billed for instances irrespective of whether they are used or not
      - You provision a VM instance - You pay for its lifetime irrespective of whether you use it or NOT
 - Expenditure Models
   - Capital Expenditure (CapEx)
     - Money spent to buy infrastructure
       -  Purchasing Azure Reserved VM Instances | (renta) Leasing Software
   - Operational Expenditure (OpEx)
     - Money spent to use a service or a product
       - Provisioning VMs as you need them
 - Total Cost of Ownership (TCO) calculator
   - on-premises deployments and Azure
   - Estimate the cost savings you get by migrating your workloads to Azure
 - Pricing calculator
   - Estimate the costs for Azure services and resources
 - Azure Cost Management
   - Analyze and optimize cloud costs
   - Control and optimize costs
 - Requesting a Credit from Microsoft
   - Service Level Agreement (SLA): Describe Microsoft’s commitments for uptime and connectivity for Azure Services

<!-- 184 -->
## ⌯⌲ More Azure
- Tags
  -  Identify applications, environments or business units that a specific resource is associated with
     - Report and track costs by assigning them with the same tag
     - Group resources based on their SLA, security or compliance requirements
  - Tags for Resources are not inherited by default from their Resource Group
- Azure Virtual Desktop
  - Desktop & application virtualization service
  -  Windows Operating Systems
     -  Windows 11, Windows 10, Windows Server 2022, 2019, 2016, etc.
  - Ultimate Device Compatibility 
    - almost any device and operating system
  - Integration
    -  Microsoft Entra ID for role-based access control(RBAC)
   - Advantages
     - Multi-Session Deployment
     - Cost Efficiency
     - Enhanced Security
- Azure Marketplace
  - Customized and certified solutions optimized for Azure, provided by Microsoft partners and other software vendors
  - Hourly Billing
- ⌯⌲ Azure Migrate
  - Central hub to manage your Azure migration
  - Azure Migrate: Server Migration
  - Azure Database Migration Service
  - Web app migration assistant
  - ⌯⌲ Azure Data Box: Physical migration to Azure
    - Data Box Disk: 8-TB SSD. Comes in packs of 5 for a total of 40 TB.
    - Data Box: 100-TB capacity
    - Data Box Heavy: Designed to lift 1 PB of data
- Azure DNS
  - Helps you route requests to in28minutes.com to my website host server
  -  TTL (Time To Live): How long is your mapping cached at the routers and the client?
- Content Delivery Network (CDN)
  - System of distributed servers that deliver content to users based on their geographic location
    - Global Distribution
    - Caching
  -  Azure Front Door
     -  Microsoft’s modern (CDN)
     -  Fast, reliable, and secure access
     -  Uses Microsoft’s global edge network
        -  global and local points of presence (PoPs) distributed around the world

<!-- 196 -->
## DevOps
- Communication, Feedback, Automation
- CI, CD
  - Continuous Integration
    - Continuously run your tests and packaging
  - Continuous Deployment
    - Continuously deploy to test environments
  - Continuous Delivery
    - Continuously deploy to production
  - Azure DevOps Tools
    - Azure Repos:  Private source control (Git)
    - Azure Pipelines: Orchestrate CI/CD pipelines
    - Azure Boards - Scrum, Agile and Kanban boards
    - Azure Artifacts - Artifact repository to store artifacts
    - Azure Test Plans - Automation Test tool to check software quality
- IaC (Infrastructure as Code)
  - Treat infrastructure the same way as application code
  - todo se define a través de archivos de configuración.
    - permite automatizar, versionar y replicar fácilmente los entornos.
  - Infrastructure Provisioning
    - Provisioning compute, database, storage and networking
    - Open source cloud neutral - Terraform
    - Azure Service - Azure Resource Manager Templates (can also use Powershell or Azure CLI automation)
  - Configuration Management
    - Install right software and tools on the provisioned resources
    - Open Source Tools - Chef, Puppet, Ansible
  - Azure Resource Manager (ARM) templates
    - Define resources in a JSON file
    - Advantages
      - Avoid configuration drift
      - Avoid mistakes with manual configuration
      - Think of it as version control for your environments
    - PowerShell and Bash scripts can also be used for IaC
  - Bicep
    - It don't use the verbosity of JSON ARM Templates
    - Domain-specific language (DSL) that uses declarative syntax to deploy Azure resources
    - Advantages
      - Concise syntax
      - Support for code reuse
      - First-class authoring experience
  - Azure Resource Manager (ARM)
    - Deployment and management service for Azure
    - All actions to any resource in Azure go through ARM
      - Azure portal OR Powershell OR CLI or ARM template or ...
  - Herramientas para interactuar con Azure
    - Azure Portal
      - Interfaz web
      - Ideal para comenzar
      - ❌ No permite automatización
      - Compatible con navegadores modernos (escritorio y tabletas)
    
    - Azure Mobile App
      - Aplicación para iOS y Android
      - Subconjunto de funcionalidades del portal
      - Conveniente para gestionar desde cualquier lugar

    - Azure PowerShell
      - Ejecuta cmdlets y scripts de PowerShell
      - Recomendado para equipos familiarizados con administración en Windows
      - Compatible con Windows, Linux y macOS

    - Azure CLI
      - Similar a PowerShell, pero con sintaxis diferente (scripts Bash)
      - Recomendado para equipos con experiencia en Linux/Bash
      - Compatible con Windows, Linux y macOS

    - Azure Cloud Shell
      - Consola interactiva en el navegador (desde Azure Portal)
      - Herramientas comunes de Azure preinstaladas
      - Compatible con PowerShell y CLI
      - Accesible desde navegadores modernos

  - DevTest Labs
    - Quickly provision development and test environments
    - Uses ARM templates
    - Can be integrated into your CI/CD pipelines

## ⌯⌲ Azure Quick Review
- Compute
  - **Azure VMs**
    - Windows o Linux VMs (IaaS)
    - Control total sobre el SO o para ejecutar software personalizado
  - **Azure VM Scale Sets**
    - Escalado automático para Azure VMs
  - **Azure Load Balancer**
    - Balancea carga entre múltiples instancias
    - (Categoría Networking)
  - **Azure App Service**
    - PaaS
    - Despliegue rápido de apps web, backends móviles y APIs RESTful
  - **Azure Container Instances**
    - Ejecuta contenedores aislados sin orquestación
    - Sin necesidad de administrar VMs
  - **Azure Kubernetes Service (AKS)**
    - Servicio gestionado de Kubernetes
    - Orquestación de contenedores
  - **Azure Service Fabric**
    - Orquestador de contenedores de Microsoft
    - Microservicios escalables y confiables en la nube o en local
  - **Azure Functions**
    - Computación serverless para aplicaciones basadas en eventos

- Networking
  - **Azure Virtual Network**
    - Red privada en la nube
  - **Azure Firewall**
    - Firewall con estado para proteger recursos
  - **Azure DDoS Protection**
    - Protección contra ataques DDoS
  - **Azure ExpressRoute**
    - Conexión privada dedicada con entornos on-premises
  - **Azure VPN Gateway**
    - Cifra tráfico entre red virtual y on-premises
    - Tráfico viaja por Internet (público)
  - **Azure DNS**
    - Gestiona registros DNS
    - Asocia nombres de dominio con IPs
  - **Azure Content Delivery Network**
    - Cacheo en servidores perimetrales globales (POPs)
    - Reduce latencia para usuarios globales

- Storage
  - **Azure Disk Storage**
    - Almacenamiento de discos para VMs
  - **Azure Blob Storage**
    - Almacenamiento de datos no estructurados (videos, backups)
  - **Azure File Storage**
    - Compartir archivos o servidores de archivos en la nube
  - **Azure Queue Storage**
    - Comunicación asincrónica entre aplicaciones
  - **Azure Table Storage**
    - Almacenamiento NoSQL sin esquema (clave/atributo)

- Databases
  - **Azure Cosmos DB**
    - Base de datos NoSQL distribuida globalmente
  - **Azure SQL Database**
    - Base de datos relacional
  - **Azure Database for MySQL**
    - MySQL totalmente gestionado
  - **Azure Database for PostgreSQL**
    - PostgreSQL totalmente gestionado
  - **Azure Database Migration Service**
    - Migración de bases de datos a la nube
  - **Azure Cache for Redis**
    - Servicio gestionado de Redis

- ⌯⌲ Key Cloud Benefits (Beneficios Clave de la Nube)
  - **Elasticity (Elasticidad)**
    - Escalado automático según la demanda
  - **Agility (Agilidad)**
    - Rápida adaptación a necesidades de negocio
  - **Availability (Disponibilidad)**
    - Disponibilidad de apps cuando los usuarios las necesitan
  - **Scalability (Escalabilidad)**
    - Soporte al crecimiento sin degradación de rendimiento
  - **Geo-distribution (Distribución Geográfica)**
    - Distribución de apps por regiones/zonas geográficas
  - **Predictability (Previsibilidad)**
    - Rendimiento y costos predecibles
  - **Reliability (Confiabilidad / Fiabilidad)**
    - Recuperación automática ante fallos
  - **Disaster Recovery (Recuperación ante Desastres)**
    - Continuidad del sistema ante desastres


