# PULSEFLEET

Simulador interactivo de gestión de flotas AMR para el ecosistema LOGISTPULSE.

## Funcionalidades

- Mission Control con mapa 2D y telemetría en tiempo real.
- Fleet Overview con estado, batería, capacidad y acciones por robot.
- Mission Board con asignación, ejecución y trazabilidad SSCC.
- Incident Center con reconocimiento y resolución de excepciones.
- Map Editor para añadir nodos y bloquear segmentos.
- Scenario Simulator con fallos, prioridad, congestión y velocidad variable.
- Persistencia local automática en el navegador.

## Ejecutar en GitHub Codespaces

1. Crear un repositorio nuevo y cargar el contenido de este proyecto.
2. Abrir **Code → Codespaces → Create codespace on main**.
3. Esperar que finalice la instalación automática.
4. Ejecutar:

```bash
npm run dev
```

5. Abrir el puerto `5173` cuando Codespaces lo anuncie.

## Ejecutar localmente

Requiere Node.js 22 o superior.

```bash
npm install
npm run dev
```

## Construir

```bash
npm run build
```

## Alcance

Esta versión implementa la lógica de simulación en el navegador. No controla motores,
sensores ni funciones certificadas de seguridad. La integración futura con ROS 2,
Open-RMF o un Fleet Manager comercial debe realizarse mediante adaptadores.

## Restablecer los datos

Use **Scenario Simulator → Reiniciar**. Esto restaura robots, mapa, misiones e
incidentes iniciales.
