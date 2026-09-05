# Arquitectura de PULSEFLEET

## Alcance de esta versión

PULSEFLEET 1.0 es un simulador funcional ejecutado en el navegador. El motor de
simulación, el estado de la flota y la interfaz se encuentran en una sola aplicación
modular para facilitar su uso en GitHub Codespaces.

```text
Interfaz de operación
        │
        ├── Mission Control
        ├── Fleet Overview
        ├── Mission Board
        ├── Incident Center
        ├── Map Editor
        └── Scenario Simulator
        │
Motor PULSEFLEET
        ├── Robot Registry
        ├── Mission Scheduler
        ├── Route Planner
        ├── Traffic Reservation
        ├── Charging Manager
        └── Exception Handler
        │
AMR Simulator + almacenamiento local
```

## Decisiones de diseño

- El mapa se representa como un grafo de nodos y segmentos.
- La planificación utiliza el camino más corto evitando segmentos bloqueados.
- Las asignaciones consideran disponibilidad, batería, capacidad y distancia.
- Los segmentos se reservan por ciclo para evitar que dos robots los ocupen a la vez.
- Las cargas se identifican por pallet y SSCC.
- Los cambios se guardan en `localStorage` para mantener el laboratorio autocontenido.

## Límites de seguridad

El proyecto no implementa frenado, PLC de seguridad, control de motores, SLAM ni
percepción LiDAR. Esas funciones deben permanecer en el robot y su controlador
certificado. PULSEFLEET envía objetivos y recibe estados.

## Evolución prevista

1. Sustituir el estado local por APIs Spring Boot y PostgreSQL.
2. Incorporar MQTT para comandos y telemetría.
3. Publicar eventos de negocio en Redpanda/Kafka.
4. Añadir un adaptador VDA 5050 o Open-RMF.
5. Conectar LOGISTPULSE mediante órdenes de misión.
6. Reemplazar el AMR simulado por Gazebo/ROS 2 o una flota real.

La interfaz puede conservarse durante estas etapas porque depende del modelo de
misiones y telemetría, no del motor físico del robot.
