# Arquitectura - Plataforma de Créditos en Línea Multicountry

```mermaid
graph TD
    %% Capa Frontend
    A[Clientes Web/Móvil] -->|HTTPS| B[CDN Global]
    B --> C[API Gateway]

    %% Capa Backend
    C --> D[Microservicio: Solicitud de Créditos]
    C --> E[Microservicio: Auditoría]
    C --> F[Microservicio: Core Bancario Adapter]
    
    %% Conexión a Core Bancario
    F --> G[Core Bancario País 1 (ej: FlexCube)]
    F --> H[Core Bancario País 2 (ej: Banorte)]

    %% Capa de Datos
    D --> I[(PostgreSQL: Solicitudes)]
    E --> J[(Elasticsearch: Logs)]
    D --> K[(Redshift: Reporting)]

    %% Servicios Externos
    D --> L[Identity Verification]
    D --> M[Scoring Crediticio]
    D --> N[Notificaciones]

    %% Seguridad
    C --> O[WAF]
    O --> P[KMS: Encriptación]

    %% Monitorización
    subgraph Observabilidad
        Q[Datadog]
        R[Alertas de Fraude]
    end
    I --> Q
    J --> Q
