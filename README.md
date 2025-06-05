
```mermaid
flowchart LR
    A[Frontend] --> B[API Gateway]
    B --> C[Microservicios]
    C --> D[(PostgreSQL)]
    C --> E[Core Bancario]
    C --> F[Servicios Externos]
    F --> G[Identity Verification]
    F --> H[Scoring]
```


# Vista de Componentes

```mermaid
flowchart LR
    A[Frontend Web o Mobile]
    B[API Gateway]
    C[Auth Service]
    D[Credit App Service]
    E[Rules & Decision Engine]
    F[Core Banking Adapter]
    G[External Services API]
    H[Audit Logging Service]
    I[Persistence Service]
    J[(Base de Datos Principal)]

    A --> B
    B --> C
    B --> D
    D --> E
    D --> F
    D --> G
    D --> H
    D --> I
    I --> J
    H --> J
```

# Arquitectura para Plataforma de Créditos en Línea (Multipaís)

Esta arquitectura aprovecha los servicios de AWS para ofrecer una solución escalable, segura y auditable para la solicitud de créditos en línea, incluyendo integración con múltiples cores bancarios y servicios externos.

---

## 📦 Vista de Componentes

```mermaid
flowchart LR
    A[Cliente Web/Mobile]
    B[AWS API Gateway]
    C[AWS Cognito - Auth]
    D[Lambda / ECS - Servicio de Crédito]
    E[Motor de Reglas Drools / DMN]
    F[Adaptadores Core Bancario por país]
    G[API Servicios Externos Buró, AML]
    H[Audit Logging Service]
    I[Amazon RDS PostgreSQL]
    
    A --> B
    B --> C
    B --> D
    D --> E
    D --> F
    D --> G
    D --> H
    D --> I
    H --> I
```
