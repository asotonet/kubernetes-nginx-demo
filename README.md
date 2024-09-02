[Convertir manifiestos de Docker Compose a Kubernetes][https://kompose.io/]
````mermaid
graph TD
    A[Desarrollador hace push a GitHub] -->|Trigger| B[GitHub Actions inicia workflow]
    B --> C{Ejecutar pruebas}
    C -->|Fallan| D[Notificar al desarrollador]
    D --> A
    C -->|Pasan| E[Construir imagen Docker]
    E --> F[Subir imagen a DockerHub]
    F --> G[Actualizar manifiesto de Kubernetes en GitHub]
    G --> H[ArgoCD detecta cambios]
    H --> I[ArgoCD compara estado deseado vs actual]
    I --> J[ArgoCD aplica cambios en cluster Kubernetes]
    J --> K[Monitorear despliegue]
    K -->|Éxito| L[Notificar equipo]
    K -->|Fallo| M[Rollback automático y notificar]
    M --> A
````