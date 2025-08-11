[# testEmployeeCrud

proyecto para manejo de ramas

# 📊 Diagrama de Arquitectura - Sistema de Microservicios con Discord

## 🏗️ Arquitectura General del Sistema

```mermaid
graph TB
    subgraph "👤 Usuario/DevOps"
        A[Usuario ejecuta script]
        B[Configura variables de entorno]
    end
    
    subgraph "🔄 Scripts de Automatización"
        C[create_microservice.sh]
        D[discord_notification.py]
        E[test_discord_notification.py]
    end
    
    subgraph "📋 Template Cookiecutter"
        F[cookiecutter.json]
        G[Estructura del proyecto]
    end
    
    subgraph "🐳 Contenedores Docker"
        H[Go Application]
        I[PostgreSQL]
        J[Redis]
        K[Kafka]
        L[Grafana]
        M[Prometheus]
    end
    
    subgraph "📱 Discord"
        N[Canal DevOps]
        O[Webhook]
    end
    
    subgraph "🌐 GitHub"
        P[Repositorio creado]
        Q[CI/CD Pipeline]
    end
    
    A --> C
    B --> D
    C --> F
    C --> G
    G --> H
    H --> I
    H --> J
    H --> K
    H --> L
    H --> M
    C --> D
    D --> O
    O --> N
    C --> P
    P --> Q
    E --> D
```

## 🔄 Flujo de Creación de Microservicio

```mermaid
sequenceDiagram
    participant U as 👤 Usuario
    participant S as 🔧 Script
    participant C as 📋 Cookiecutter
    participant G as 🐳 Docker
    participant D as 📱 Discord
    participant GH as 🌐 GitHub
    
    U->>S: Ejecuta create_microservice.sh
    S->>U: Solicita información del proyecto
    U->>S: Proporciona datos
    S->>C: Ejecuta cookiecutter
    C->>S: Crea estructura del proyecto
    S->>G: Configura Docker Compose
    S->>GH: Crea repositorio (opcional)
    S->>D: Envía notificación
    D->>U: Muestra notificación en Discord
    S->>U: Proporciona guía de próximos pasos
```

## 🎯 Estructura de Archivos del Sistema

```mermaid
graph LR
    subgraph "📁 Scripts de Automatización"
        A1[create_microservice.sh]
        A2[discord_notification.py]
        A3[test_discord_notification.py]
    end
    
    subgraph "⚙️ Configuración"
        B1[discord_config.env]
        B2[cookiecutter.json]
        B3[.env]
    end
    
    subgraph "📚 Documentación"
        C1[README_SCRIPTS.md]
        C2[RESUMEN_IMPLEMENTACION.md]
        C3[proposal_go_hexagonal_architecture.md]
        C4[create_docx.py]
    end
    
    subgraph "🏗️ Proyecto Generado"
        D1[domain/]
        D2[application/]
        D3[infrastructure/]
        D4[docker-compose.yml]
        D5[Makefile]
        D6[go.mod]
    end
    
    A1 --> B1
    A2 --> B1
    A3 --> A2
    A1 --> B2
    A1 --> D1
    A1 --> D2
    A1 --> D3
    A1 --> D4
    A1 --> D5
    A1 --> D6
```

## 🔧 Arquitectura Hexagonal del Microservicio

```mermaid
graph TB
    subgraph "🌐 Infrastructure Layer"
        A1[GraphQL API]
        A2[PostgreSQL DB]
        A3[Redis Cache]
        A4[Kafka Events]
        A5[Prometheus Metrics]
    end
    
    subgraph "🎯 Application Layer"
        B1[Use Cases]
        B2[DTOs]
        B3[Interfaces]
    end
    
    subgraph "💼 Domain Layer"
        C1[Entities]
        C2[Repositories]
        C3[Services]
    end
    
    A1 --> B1
    A2 --> B2
    A3 --> B2
    A4 --> B1
    A5 --> B1
    B1 --> C1
    B2 --> C2
    B3 --> C3
```

## 📱 Flujo de Notificación Discord

```mermaid
flowchart TD
    A[Inicio] --> B{¿Existe DISCORD_WEBHOOK_URL?}
    B -->|No| C[⚠️ Mostrar advertencia]
    B -->|Sí| D[📝 Crear payload]
    D --> E[🎨 Configurar embed]
    E --> F[📤 Enviar a Discord]
    F --> G{¿Éxito?}
    G -->|No| H[❌ Mostrar error]
    G -->|Sí| I[✅ Confirmar envío]
    C --> J[Fin]
    H --> J
    I --> J
```

## 🐳 Arquitectura de Contenedores

```mermaid
graph TB
    subgraph "🏠 Local Environment"
        A[Go App :8080]
        B[PostgreSQL :5432]
        C[Redis :6379]
        D[Kafka :9092]
        E[Grafana :3000]
        F[Prometheus :9090]
    end
    
    subgraph "🚀 Staging Environment"
        G[Go App :8080]
        H[PostgreSQL :5432]
        I[Redis :6379]
        J[Kafka :9092]
        K[Grafana :3000]
        L[Prometheus :9090]
    end
    
    subgraph "🌍 Production Environment"
        M[Go App :8080]
        N[PostgreSQL :5432]
        O[Redis :6379]
        P[Kafka :9092]
        Q[Grafana :3000]
        R[Prometheus :9090]
    end
    
    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
    
    G --> H
    G --> I
    G --> J
    G --> K
    G --> L
    
    M --> N
    M --> O
    M --> P
    M --> Q
    M --> R
```

## 🎨 Ejemplo de Notificación Discord

```mermaid
graph LR
    subgraph "📱 Discord Embed"
        A[🚀 Nuevo Microservicio Creado]
        B[📁 Proyecto: Mi Microservicio]
        C[👤 Autor: Tu Nombre]
        D[📋 Template: go-hexagonal-template]
        E[🔗 Repositorio: GitHub Link]
        F[⏰ Timestamp: 2024-01-01T00:00:00Z]
    end
    
    A --> B
    A --> C
    A --> D
    A --> E
    A --> F
```

## 🔄 CI/CD Pipeline

```mermaid
graph LR
    A[Git Push] --> B[GitHub Actions]
    B --> C[Build & Test]
    C --> D[Deploy to Staging]
    D --> E[Run Integration Tests]
    E --> F[Deploy to Production]
    F --> G[Health Checks]
    G --> H[Discord Notification]
```

## 📊 Monitoreo y Observabilidad

```mermaid
graph TB
    subgraph "📈 Métricas"
        A[Prometheus]
        B[Custom Metrics]
        C[Business Metrics]
    end
    
    subgraph "📊 Visualización"
        D[Grafana Dashboards]
        E[Custom Panels]
        F[Alerting Rules]
    end
    
    subgraph "🔍 Logging"
        G[Application Logs]
        H[System Logs]
        I[Error Tracking]
    end
    
    A --> D
    B --> E
    C --> F
    G --> I
    H --> I
```

## 🎯 Casos de Uso del Sistema

```mermaid
graph TD
    A[Inicio] --> B{¿Qué quiere hacer?}
    
    B -->|Crear Microservicio| C[Ejecutar create_microservice.sh]
    B -->|Probar Discord| D[Ejecutar test_discord_notification.py]
    B -->|Notificación Manual| E[Ejecutar discord_notification.py]
    B -->|Ver Documentación| F[Leer README_SCRIPTS.md]
    
    C --> G[Proyecto creado + Notificación Discord]
    D --> H[Prueba completada]
    E --> I[Notificación enviada]
    F --> J[Documentación consultada]
    
    G --> K[Fin]
    H --> K
    I --> K
    J --> K
```

---

## 📋 Resumen del Diagrama

### 🎯 **Componentes Principales:**
1. **Scripts de Automatización** - Manejan todo el proceso
2. **Template Cookiecutter** - Genera la estructura del proyecto
3. **Contenedores Docker** - Ejecutan los servicios
4. **Discord** - Recibe notificaciones
5. **GitHub** - Almacena el código

### 🔄 **Flujo Principal:**
1. Usuario ejecuta script
2. Se crea proyecto con Cookiecutter
3. Se configuran contenedores Docker
4. Se envía notificación a Discord
5. Se crea repositorio en GitHub

### 🎨 **Características Destacadas:**
- **Arquitectura Hexagonal** - Separación clara de responsabilidades
- **Multi-entorno** - Local, Staging, Producción
- **Monitoreo Completo** - Prometheus + Grafana
- **Notificaciones Automáticas** - Discord en tiempo real
- **Automatización Total** - Un comando para todo

**¡El sistema está completamente diagramado y listo para implementar! 🚀**



# 📁 Diagrama de Estructura de Archivos - Sistema Completo

## 🗂️ Estructura de Directorios del Sistema

```mermaid
graph TB
    subgraph "📂 Directorio Raíz"
        Root[📁 Cryptospace-card-holder/]
    end
    
    subgraph "🔄 Scripts de Automatización"
        Scripts[📁 Scripts/]
        Scripts --> A1[📄 create_microservice.sh]
        Scripts --> A2[📄 discord_notification.py]
        Scripts --> A3[📄 test_discord_notification.py]
    end
    
    subgraph "⚙️ Configuración"
        Config[📁 Config/]
        Config --> B1[📄 discord_config.env]
        Config --> B2[📄 cookiecutter.json]
        Config --> B3[📄 .env]
    end
    
    subgraph "📚 Documentación"
        Docs[📁 Documentation/]
        Docs --> C1[📄 README_SCRIPTS.md]
        Docs --> C2[📄 RESUMEN_IMPLEMENTACION.md]
        Docs --> C3[📄 proposal_go_hexagonal_architecture.md]
        Docs --> C4[📄 create_docx.py]
        Docs --> C5[📄 diagrama_arquitectura.md]
        Docs --> C6[📄 diagrama_flujo_completo.md]
        Docs --> C7[📄 diagrama_estructura_archivos.md]
    end
    
    subgraph "🏗️ Proyecto Generado"
        Project[📁 mi-microservicio/]
        Project --> D1[📁 domain/]
        Project --> D2[📁 application/]
        Project --> D3[📁 infrastructure/]
        Project --> D4[📄 docker-compose.yml]
        Project --> D5[📄 Makefile]
        Project --> D6[📄 go.mod]
        Project --> D7[📄 .env.example]
    end
    
    Root --> Scripts
    Root --> Config
    Root --> Docs
    Root --> Project
    
    A1 -.->|Usa| B1
    A2 -.->|Lee| B1
    A3 -.->|Prueba| A2
    A1 -.->|Genera| Project
```

## 🔗 Relaciones entre Archivos

```mermaid
graph LR
    subgraph "🔄 Scripts Principales"
        A[create_microservice.sh]
        B[discord_notification.py]
        C[test_discord_notification.py]
    end
    
    subgraph "⚙️ Configuración"
        D[discord_config.env]
        E[cookiecutter.json]
        F[.env]
    end
    
    subgraph "📚 Documentación"
        G[README_SCRIPTS.md]
        H[RESUMEN_IMPLEMENTACION.md]
        I[proposal_go_hexagonal_architecture.md]
    end
    
    subgraph "🏗️ Output"
        J[Proyecto Generado]
        K[Notificación Discord]
    end
    
    A -->|Lee| D
    A -->|Usa| E
    A -->|Genera| J
    A -->|Llama| B
    B -->|Lee| D
    B -->|Envía| K
    C -->|Prueba| B
    C -->|Lee| D
    
    G -->|Documenta| A
    G -->|Documenta| B
    H -->|Resume| A
    H -->|Resume| B
    I -->|Describe| A
    I -->|Describe| B
```

## 📋 Flujo de Dependencias

```mermaid
flowchart TD
    A[discord_config.env] --> B[discord_notification.py]
    A --> C[test_discord_notification.py]
    
    B --> D[create_microservice.sh]
    C --> E[Pruebas de notificación]
    
    F[cookiecutter.json] --> G[create_microservice.sh]
    G --> H[Proyecto generado]
    
    I[README_SCRIPTS.md] --> J[Guía de uso]
    K[RESUMEN_IMPLEMENTACION.md] --> L[Resumen completo]
    M[proposal_go_hexagonal_architecture.md] --> N[Documentación técnica]
    
    D --> O[Notificación Discord]
    H --> P[Estructura del microservicio]
    
    style A fill:#e1f5fe
    style B fill:#fff3e0
    style C fill:#fff3e0
    style D fill:#fff3e0
    style F fill:#f3e5f5
    style H fill:#c8e6c9
    style O fill:#f3e5f5
```

## 🎯 Estructura del Proyecto Generado

```mermaid
graph TB
    subgraph "🏗️ mi-microservicio/"
        Root[📁 mi-microservicio/]
        
        subgraph "💼 Domain Layer"
            Domain[📁 domain/]
            Domain --> D1[📁 entities/]
            Domain --> D2[📁 repositories/]
            Domain --> D3[📁 services/]
        end
        
        subgraph "🎯 Application Layer"
            App[📁 application/]
            App --> A1[📁 usecases/]
            App --> A2[📁 dto/]
            App --> A3[📁 interfaces/]
        end
        
        subgraph "🌐 Infrastructure Layer"
            Infra[📁 infrastructure/]
            Infra --> I1[📁 database/]
            Infra --> I2[📁 api/]
            Infra --> I3[📁 messaging/]
            Infra --> I4[📁 monitoring/]
        end
        
        subgraph "🐳 Docker & Config"
            Docker[📁 docker/]
            Docker --> DC1[📄 docker-compose.yml]
            Docker --> DC2[📄 Dockerfile]
            Docker --> DC3[📄 .env.example]
        end
        
        subgraph "🔧 Build & Tools"
            Tools[📁 tools/]
            Tools --> T1[📄 Makefile]
            Tools --> T2[📄 go.mod]
            Tools --> T3[📄 go.sum]
        end
        
        subgraph "📚 Documentation"
            Doc[📁 docs/]
            Doc --> DOC1[📄 README.md]
            Doc --> DOC2[📄 API.md]
            Doc --> DOC3[📄 DEPLOYMENT.md]
        end
    end
    
    Root --> Domain
    Root --> App
    Root --> Infra
    Root --> Docker
    Root --> Tools
    Root --> Doc
```

## 🔄 Flujo de Ejecución de Archivos

```mermaid
sequenceDiagram
    participant U as 👤 Usuario
    participant S as 🔧 Script
    participant C as 📋 Config
    participant T as 🏗️ Template
    participant P as 📁 Proyecto
    participant D as 📱 Discord
    
    U->>S: Ejecuta create_microservice.sh
    S->>C: Lee discord_config.env
    S->>C: Lee cookiecutter.json
    S->>T: Ejecuta template
    T->>P: Genera estructura del proyecto
    S->>P: Crea archivos adicionales
    S->>D: Envía notificación
    D->>U: Muestra notificación
    S->>U: Muestra resumen
```

## 📊 Mapa de Archivos por Función

```mermaid
graph LR
    subgraph "🚀 Automatización"
        A1[create_microservice.sh]
        A2[discord_notification.py]
        A3[test_discord_notification.py]
    end
    
    subgraph "⚙️ Configuración"
        B1[discord_config.env]
        B2[cookiecutter.json]
        B3[.env]
    end
    
    subgraph "📚 Documentación"
        C1[README_SCRIPTS.md]
        C2[RESUMEN_IMPLEMENTACION.md]
        C3[proposal_go_hexagonal_architecture.md]
        C4[create_docx.py]
        C5[diagrama_*.md]
    end
    
    subgraph "🏗️ Template"
        D1[cookiecutter.json]
        D2[Estructura del proyecto]
        D3[Archivos de configuración]
    end
    
    subgraph "📱 Notificaciones"
        E1[discord_notification.py]
        E2[Webhook Discord]
        E3[Embeds personalizados]
    end
    
    A1 --> B1
    A1 --> B2
    A2 --> B1
    A3 --> A2
    A1 --> D1
    A1 --> E1
    E1 --> E2
    E2 --> E3
```

## 🎨 Estructura de Configuración

```mermaid
graph TB
    subgraph "🔧 Variables de Entorno"
        A[DISCORD_WEBHOOK_URL]
        B[DISCORD_CHANNEL_ID]
        C[DISCORD_BOT_TOKEN]
        D[LOG_LEVEL]
        E[LOG_FILE]
    end
    
    subgraph "📋 Template Config"
        F[project_name]
        G[project_description]
        H[author_name]
        I[author_email]
        J[github_username]
        K[go_version]
        L[graphql_enabled]
        M[monitoring_enabled]
        N[use_postgresql]
        O[use_redis]
        P[use_kafka]
        Q[app_port]
        R[grafana_port]
        S[prometheus_port]
    end
    
    subgraph "📄 Archivos de Config"
        T[discord_config.env]
        U[cookiecutter.json]
        V[.env]
    end
    
    T --> A
    T --> B
    T --> C
    T --> D
    T --> E
    
    U --> F
    U --> G
    U --> H
    U --> I
    U --> J
    U --> K
    U --> L
    U --> M
    U --> N
    U --> O
    U --> P
    U --> Q
    U --> R
    U --> S
    
    V --> A
    V --> B
    V --> C
```

## 🔄 Flujo de Datos entre Archivos

```mermaid
flowchart LR
    A[Usuario] --> B[create_microservice.sh]
    B --> C[discord_config.env]
    B --> D[cookiecutter.json]
    B --> E[cookiecutter]
    E --> F[Proyecto generado]
    B --> G[discord_notification.py]
    G --> H[Discord Webhook]
    H --> I[Notificación en Discord]
    
    J[test_discord_notification.py] --> G
    J --> C
    
    K[README_SCRIPTS.md] --> L[Documentación de uso]
    M[RESUMEN_IMPLEMENTACION.md] --> N[Resumen del sistema]
    O[proposal_go_hexagonal_architecture.md] --> P[Documentación técnica]
    
    style A fill:#e1f5fe
    style B fill:#fff3e0
    style G fill:#f3e5f5
    style H fill:#f3e5f5
    style I fill:#f3e5f5
    style F fill:#c8e6c9
```

---

## 📋 Resumen de la Estructura

### 🎯 **Archivos Principales:**

1. **Scripts de Automatización**
   - `create_microservice.sh` - Script principal
   - `discord_notification.py` - Notificaciones Discord
   - `test_discord_notification.py` - Pruebas

2. **Configuración**
   - `discord_config.env` - Variables Discord
   - `cookiecutter.json` - Template config
   - `.env` - Variables locales

3. **Documentación**
   - `README_SCRIPTS.md` - Guía de uso
   - `RESUMEN_IMPLEMENTACION.md` - Resumen
   - `proposal_go_hexagonal_architecture.md` - Documentación técnica
   - `diagrama_*.md` - Diagramas visuales

### 🔄 **Flujo de Dependencias:**

- Los scripts leen la configuración
- El script principal genera el proyecto
- Se envía notificación automática
- La documentación explica el proceso

### 🎨 **Características:**

- **Modular** - Cada archivo tiene una función específica
- **Configurable** - Variables de entorno flexibles
- **Documentado** - Guías completas
- **Probable** - Scripts de testing incluidos
- **Visual** - Diagramas explicativos

**¡La estructura está completamente organizada y documentada! 🚀**



# 🔄 Diagrama de Flujo Completo - Sistema de Microservicios

## 🎯 Flujo Principal de Creación de Microservicio

```mermaid
flowchart TD
    Start([🚀 Inicio]) --> Config{⚙️ Configurar Discord?}
    
    Config -->|No| Manual[📝 Modo Manual]
    Config -->|Sí| Setup[🔧 Configurar Webhook]
    
    Setup --> Webhook[📱 Crear Webhook en Discord]
    Webhook --> EnvVar[🔑 Configurar DISCORD_WEBHOOK_URL]
    EnvVar --> Script[🔄 Ejecutar create_microservice.sh]
    
    Manual --> Script
    
    Script --> Input[📝 Solicitar información del proyecto]
    Input --> Validate{✅ Datos válidos?}
    
    Validate -->|No| Input
    Validate -->|Sí| Cookiecutter[📋 Ejecutar Cookiecutter]
    
    Cookiecutter --> Project[🏗️ Crear estructura del proyecto]
    Project --> Docker[🐳 Configurar Docker Compose]
    Docker --> Git[📁 Inicializar repositorio Git]
    
    Git --> GitHub{🌐 Crear en GitHub?}
    GitHub -->|Sí| CreateRepo[🔗 Crear repositorio GitHub]
    GitHub -->|No| Notify[📤 Enviar notificación Discord]
    
    CreateRepo --> Notify
    Notify --> Success[✅ Proyecto creado exitosamente]
    Success --> Guide[📚 Mostrar guía de próximos pasos]
    Guide --> End([🎉 Fin])
    
    style Start fill:#e1f5fe
    style End fill:#c8e6c9
    style Script fill:#fff3e0
    style Notify fill:#f3e5f5
    style Success fill:#e8f5e8
```

## 🔧 Proceso Detallado de Automatización

```mermaid
sequenceDiagram
    participant U as 👤 Usuario
    participant S as 🔧 Script
    participant C as 📋 Cookiecutter
    participant D as 🐳 Docker
    participant G as 📁 Git
    participant GH as 🌐 GitHub
    participant DC as 📱 Discord
    
    Note over U,DC: Fase 1: Configuración
    U->>S: ./create_microservice.sh
    S->>U: Verificar dependencias
    S->>U: Solicitar información del proyecto
    
    Note over U,DC: Fase 2: Creación del Proyecto
    U->>S: Proporcionar datos del proyecto
    S->>C: Ejecutar cookiecutter
    C->>S: Estructura del proyecto creada
    S->>D: Configurar docker-compose.yml
    S->>G: git init && git add .
    S->>G: git commit -m "Initial commit"
    
    Note over U,DC: Fase 3: Integración con GitHub
    S->>U: ¿Crear repositorio en GitHub?
    U->>S: Sí/No
    alt Crear en GitHub
        S->>GH: gh repo create (si gh CLI disponible)
        GH->>S: Repositorio creado
        S->>G: git remote add origin
        S->>G: git push -u origin main
    end
    
    Note over U,DC: Fase 4: Notificación Discord
    S->>DC: Enviar notificación con detalles del proyecto
    DC->>U: Mostrar notificación en canal
    
    Note over U,DC: Fase 5: Finalización
    S->>U: Mostrar URLs de acceso
    S->>U: Mostrar comandos útiles
    S->>U: Proporcionar guía de próximos pasos
```

## 🎨 Estructura de la Notificación Discord

```mermaid
graph TB
    subgraph "📱 Discord Webhook"
        A[Webhook URL]
        B[Payload JSON]
        C[Embed Object]
    end
    
    subgraph "🎨 Embed Content"
        D[Title: 🚀 Nuevo Microservicio Creado]
        E[Color: 0x00ff00]
        F[Fields Array]
        G[Footer: Go Hexagonal Architecture Template]
        H[Timestamp: ISO 8601]
    end
    
    subgraph "📋 Fields"
        I[📁 Proyecto: project_name]
        J[👤 Autor: author_name]
        K[📋 Template: template_name]
        L[🔗 Repositorio: github_url]
    end
    
    A --> B
    B --> C
    C --> D
    C --> E
    C --> F
    C --> G
    C --> H
    F --> I
    F --> J
    F --> K
    F --> L
```

## 🐳 Arquitectura de Servicios por Entorno

```mermaid
graph TB
    subgraph "🏠 Local Development"
        L1[Go App :8080]
        L2[PostgreSQL :5432]
        L3[Redis :6379]
        L4[Kafka :9092]
        L5[Grafana :3000]
        L6[Prometheus :9090]
    end
    
    subgraph "🚀 Staging Environment"
        S1[Go App :8080]
        S2[PostgreSQL :5432]
        S3[Redis :6379]
        S4[Kafka :9092]
        S5[Grafana :3000]
        S6[Prometheus :9090]
    end
    
    subgraph "🌍 Production Environment"
        P1[Go App :8080]
        P2[PostgreSQL :5432]
        P3[Redis :6379]
        P4[Kafka :9092]
        P5[Grafana :3000]
        P6[Prometheus :9090]
    end
    
    L1 -.->|Optional| L2
    L1 -.->|Optional| L3
    L1 -.->|Optional| L4
    L1 --> L5
    L1 --> L6
    
    S1 --> S2
    S1 --> S3
    S1 --> S4
    S1 --> S5
    S1 --> S6
    
    P1 --> P2
    P1 --> P3
    P1 --> P4
    P1 --> P5
    P1 --> P6
```

## 🔄 Flujo de Decisiones del Script

```mermaid
flowchart TD
    A[Inicio] --> B{¿Cookiecutter instalado?}
    B -->|No| C[Instalar cookiecutter]
    B -->|Sí| D[Solicitar información del proyecto]
    C --> D
    
    D --> E[Configurar opciones del template]
    E --> F{¿Usar PostgreSQL?}
    F -->|Sí| G[Incluir PostgreSQL]
    F -->|No| H[Saltar PostgreSQL]
    
    E --> I{¿Usar Redis?}
    I -->|Sí| J[Incluir Redis]
    I -->|No| K[Saltar Redis]
    
    E --> L{¿Usar Kafka?}
    L -->|Sí| M[Incluir Kafka]
    L -->|No| N[Saltar Kafka]
    
    G --> O[Crear proyecto]
    H --> O
    J --> O
    K --> O
    M --> O
    N --> O
    
    O --> P{¿Crear en GitHub?}
    P -->|Sí| Q[Crear repositorio]
    P -->|No| R[Saltar GitHub]
    
    Q --> S[Enviar notificación Discord]
    R --> S
    
    S --> T[Mostrar resumen]
    T --> U[Fin]
```

## 📊 Monitoreo y Observabilidad

```mermaid
graph LR
    subgraph "📈 Data Collection"
        A[Application Metrics]
        B[System Metrics]
        C[Business Metrics]
        D[Custom Metrics]
    end
    
    subgraph "📊 Storage & Processing"
        E[Prometheus]
        F[Time Series DB]
        G[Alert Manager]
    end
    
    subgraph "📱 Visualization"
        H[Grafana Dashboards]
        I[Custom Panels]
        J[Alerting Rules]
    end
    
    subgraph "🔔 Notifications"
        K[Discord Alerts]
        L[Email Notifications]
        M[Slack Integration]
    end
    
    A --> E
    B --> E
    C --> E
    D --> E
    E --> F
    E --> G
    F --> H
    F --> I
    G --> J
    J --> K
    J --> L
    J --> M
```

## 🎯 Casos de Uso y Escenarios

```mermaid
graph TD
    A[Usuario quiere crear microservicio] --> B{¿Tiene experiencia?}
    
    B -->|Experto| C[Modo avanzado]
    B -->|Novato| D[Modo guiado]
    
    C --> E[Configuración manual]
    D --> F[Script interactivo]
    
    E --> G[Crear proyecto]
    F --> G
    
    G --> H{¿Necesita base de datos?}
    H -->|Sí| I[Incluir PostgreSQL]
    H -->|No| J[Saltar base de datos]
    
    G --> K{¿Necesita cache?}
    K -->|Sí| L[Incluir Redis]
    K -->|No| M[Saltar cache]
    
    G --> N{¿Necesita eventos?}
    N -->|Sí| O[Incluir Kafka]
    N -->|No| P[Saltar eventos]
    
    I --> Q[Proyecto configurado]
    J --> Q
    L --> Q
    M --> Q
    O --> Q
    P --> Q
    
    Q --> R[Notificación Discord]
    R --> S[Proyecto listo]
```

## 🔧 Arquitectura Técnica Detallada

```mermaid
graph TB
    subgraph "🌐 External Interfaces"
        A1[GraphQL API]
        A2[REST API]
        A3[gRPC API]
    end
    
    subgraph "🎯 Application Services"
        B1[Use Case Handlers]
        B2[Command Handlers]
        B3[Query Handlers]
        B4[Event Handlers]
    end
    
    subgraph "💼 Domain Layer"
        C1[Entities]
        C2[Value Objects]
        C3[Domain Services]
        C4[Repository Interfaces]
    end
    
    subgraph "🏗️ Infrastructure"
        D1[PostgreSQL Repository]
        D2[Redis Cache]
        D3[Kafka Producer/Consumer]
        D4[Prometheus Metrics]
        D5[Logging Service]
    end
    
    A1 --> B1
    A2 --> B2
    A3 --> B3
    B1 --> C1
    B2 --> C2
    B3 --> C3
    B4 --> C4
    C4 --> D1
    C1 --> D2
    C3 --> D3
    B1 --> D4
    B1 --> D5
```

---

## 📋 Resumen del Flujo Completo

### 🎯 **Fases del Proceso:**

1. **Configuración** - Preparar entorno y Discord
2. **Entrada de Datos** - Información del proyecto
3. **Generación** - Crear estructura con Cookiecutter
4. **Configuración** - Docker, Git, GitHub
5. **Notificación** - Enviar a Discord
6. **Finalización** - Guía y resumen

### 🔧 **Componentes Clave:**

- **Scripts Automatizados** - Manejan todo el flujo
- **Template Cookiecutter** - Genera estructura estándar
- **Docker Compose** - Orquesta servicios
- **Discord Webhook** - Notificaciones en tiempo real
- **GitHub Integration** - Control de versiones

### 🎨 **Características Destacadas:**

- **Flexibilidad** - Servicios opcionales (PostgreSQL, Redis, Kafka)
- **Automatización** - Un comando para todo
- **Notificaciones** - Feedback inmediato
- **Multi-entorno** - Local, Staging, Producción
- **Monitoreo** - Observabilidad completa

**¡El flujo está completamente diagramado y optimizado! 🚀**
