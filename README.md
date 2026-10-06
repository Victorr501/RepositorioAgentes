# Repositorio de Agentes - Desarrollo con IA

Este repositorio es una plantilla y guía para implementar un flujo de trabajo basado en **Spec-Driven Development (SDD)** y **Sistemas Multiagente** utilizando herramientas de IA (como OpenCode). Define un entorno completo con memoria, guardarraíles (harness engineering) y roles delegados.

## Estructura del Repositorio

La arquitectura del proyecto está diseñada para organizar el contexto, las reglas y las herramientas que utilizan los agentes de Inteligencia Artificial para desarrollar software.

### `.opencode/`
Contiene la configuración específica, comandos, habilidades y agentes personalizados.
- **`agents/`**: Define el sistema multiagente que coordina el proyecto.
  - `coordinator.md`: Dirige el flujo de desarrollo y transmite el contexto, repartiendo el trabajo.
  - `planner.md`: Redacta especificaciones, planes y tareas sin tocar código.
  - `implementer.md`: Ejecuta de forma aislada las tareas programando y pasando tests.
  - `reviewer.md`: Actúa como un QA para validar las especificaciones y el código generado.
- **`commands/`**: Comandos personalizados (como `feature.md`) para automatizar prompts y tareas repetitivas en el chat.
- **`skills/`**: Habilidades reutilizables (`SKILL.md`) que dotan a los agentes de conocimientos técnicos concretos para el proyecto (ej. reglas de fechas locales).

### `docs/`
- **`constitution.md`**: Los principios innegociables del proyecto. Establece las reglas base (política de tests, separación lógica/interfaz, simplicidad) que toda especificación y agente debe cumplir obligatoriamente.

### `specs/`
Carpeta principal para el desarrollo guiado por especificaciones (SDD). Cada nueva funcionalidad se organiza en una subcarpeta (ej. `001-nombre-spec`) que contiene:
- `spec.md`: La especificación con el "Qué" y el "Por qué" (historias de usuario, requisitos en notación EARS, casos límite).
- `plan.md`: El plan técnico con el "Cómo" (archivos a modificar, lógica, diseño de la solución).
- `task.md`: La división del plan en tareas pequeñas, secuenciales y verificables.

### `test/`
Directorio destinado a las pruebas automáticas del proyecto para garantizar que las implementaciones cumplen con la especificación.

### Archivos Raíz de Contexto
- **`AGENTS.md`**: Instrucciones principales, stack tecnológico, convenciones y límites globales para orientar a cualquier agente que interactúe con el repositorio.
- **`MEMORY.md`**: Archivo de memoria a largo plazo que registra el estado actual del proyecto, decisiones técnicas clave y aprendizajes entre sesiones.
- **`opencode.json`**: Configuración del proyecto para la herramienta OpenCode, incluyendo la integración con servicios externos a través del protocolo MCP (Model Context Protocol).
- **`README.md`**: Este archivo, que documenta la estructura del proyecto.

## Flujo de Trabajo
El desarrollo fluye a través de un ciclo claro bajo supervisión humana continua:
1. **Constitución**: Se establecen las reglas en `docs/`.
2. **Especificación y Planificación**: A través del agente planificador en la carpeta `specs/`.
3. **Implementación**: El implementador escribe el código tarea por tarea.
4. **Validación**: El revisor comprueba rigurosamente que el código cumple con los requisitos de la especificación original.