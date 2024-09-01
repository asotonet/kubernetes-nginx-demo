````mermaid
  graph TD
    A[Desarrollador hace push a Git] -->|Trigger| B[Jenkins detecta cambios]
    B --> C{Ejecutar pruebas}
    C -->|Fallan| D[Notificar al desarrollador]
    D --> A
    C -->|Pasan| E[Construir imagen Docker]
    E --> F[Subir imagen a registro Docker]
    F --> G[Actualizar manifiesto de Kubernetes]
    G --> H[Aplicar cambios en cluster Kubernetes]
    H --> I[Monitorear despliegue]
    I -->|Éxito| J[Notificar equipo]
    I -->|Fallo| K[Rollback y notificar]
    K --> A
````