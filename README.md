# TPI Organización Empresarial – TiendaNEA

**Módulo de Gestión de Inventario y Stock en Tiempo Real**

Trabajo Práctico Integrador y Progresivo de la asignatura **Organización Empresarial** – Tecnicatura Universitaria en Programación a Distancia (TUPaD) – Universidad Tecnológica Nacional.

| | |
|---|---|
| 📋 **Tablero de gestión (GitHub Projects)** | https://github.com/users/LichaLopez11/projects/1 |
| 📄 **Documento final consolidado (PDF)** | [docs/TPI_Final_OrganizacionEmpresarial_Iturri.pdf](docs/TPI_Final_OrganizacionEmpresarial_Iturri.pdf) |
| 🔀 **Proceso BPMN editable** | [docs/bpmn/proceso-gestion-stock.bpmn](docs/bpmn/proceso-gestion-stock.bpmn) |

## Descripción del sistema

TiendaNEA es una empresa ficticia de comercio electrónico que vende online productos regionales del Nordeste Argentino (yerba mate, artesanías, alimentos y textiles). Hoy el stock se controla con planillas manuales entre el depósito y ventas, lo que provoca ventas de productos sin disponibilidad y reposiciones tardías.

El **Módulo de Gestión de Inventario y Stock en Tiempo Real** registra cada movimiento de mercadería (ingresos, ventas, devoluciones y ajustes autorizados), mantiene sincronizado el stock del depósito con el de la tienda online y avisa a Compras cuando un producto llega a su stock mínimo.

## Integrante

| Nombre | Usuario de GitHub | Rol en el proyecto |
|---|---|---|
| Lisandro Iturri | [@LichaLopez11](https://github.com/LichaLopez11) | Análisis, diseño, documentación y desarrollo |

**Cátedra:** Prof. Gabriela Martínez (titular); Prof. Carolina Bruno, Prof. Mario Raúl López y Prof. Andrea Ramos (adjuntos).

## Contenido del repositorio

```
├── README.md                       Portada del proyecto y Declaración de Uso de IA
├── .github/                        Plantillas de Pull Request e historias de usuario
└── docs/
    ├── entregas/                   PDF de las Entregas 1, 2 y 3
    ├── bpmn/                       Proceso BPMN (.bpmn editable, .svg y .png)
    ├── img/                        Organigrama
    ├── diccionario-de-datos.md
    ├── historias-de-usuario.md
    ├── indicadores-de-control.md
    └── TPI_Final_OrganizacionEmpresarial_Iturri.pdf
```

| Entrega | Tema | Dónde está |
|---|---|---|
| N°1 | La organización y su enfoque sistémico (TGS) | [PDF](docs/entregas/Entrega1_OrganizacionEmpresarial_Iturri.pdf) |
| N°2 | Diagnóstico FODA, metas y Diagrama de Gantt | [PDF](docs/entregas/Entrega2_OrganizacionEmpresarial_Iturri.pdf) |
| N°3 | Organigrama y diccionario de datos | [PDF](docs/entregas/Entrega3_OrganizacionEmpresarial_Iturri.pdf) · [Diccionario](docs/diccionario-de-datos.md) |
| N°4 | BPMN, Git/GitHub, backlog ágil y control | [BPMN](docs/bpmn/) · [Historias](docs/historias-de-usuario.md) · [Indicadores](docs/indicadores-de-control.md) |

## Proceso de negocio (BPMN)

![Proceso de gestión de stock](docs/bpmn/proceso-gestion-stock.png)

## Historias de usuario

| ID | Historia | Estado |
|---|---|---|
| HU-01 | **Como** encargado de depósito, **quiero** registrar en el sistema el ingreso de la mercadería recibida de los proveedores, **para** que el stock se actualice automáticamente en la tienda online sin cargar planillas manuales. | En progreso |
| HU-02 | **Como** responsable de ventas, **quiero** que cada venta online descuente automáticamente el stock disponible, **para** no confirmar pedidos de productos que no están en el depósito. | Por hacer |
| HU-03 | **Como** responsable de compras, **quiero** recibir una alerta cuando un producto llegue a su stock mínimo, **para** pedir la reposición al proveedor antes de quedarme sin mercadería. | Por hacer |

Detalle y criterios de aceptación en [docs/historias-de-usuario.md](docs/historias-de-usuario.md).

## Flujo de trabajo con Git

- **`main`**: solo contiene la versión revisada. Los cambios entran únicamente por Pull Request.
- **`docs/entregas-anteriores`**: incorporación de las Entregas 1, 2 y 3.
- **`feature/entrega-4-procesos-control`**: BPMN, historias de usuario, indicadores y documento final.
- **Commits:** formato [Conventional Commits](https://www.conventionalcommits.org/es/) en español e imperativo (`docs:`, `fix:`, `chore:`).
- **Revisión:** cada Pull Request usa una lista de control. Al ser un trabajo individual, GitHub no permite aprobar el propio PR, por lo que se realizó una autorrevisión documentada con comentarios en *Files changed*.

## Declaración de Uso de IA

Durante todo el TPI se utilizó **Claude** (Anthropic), un asistente de IA generativa, en una misma conversación que acompañó las cuatro entregas. En cada caso se le proporcionaron la consigna oficial y la plantilla de la cátedra.

### Para qué se usó
- Proponer el contenido inicial de cada consigna: caso TiendaNEA, módulo, FODA, metas, cronograma, organigrama, entidades de datos, proceso BPMN, historias de usuario e indicadores.
- Generar las figuras y calcular las fechas del cronograma en días hábiles.
- Revisar la coherencia entre entregas, el estilo y el formato de la plantilla.
- Preparar los archivos de este repositorio y una guía de pasos de Git y GitHub. **Los commits, ramas, Pull Requests, issues y el tablero fueron creados por el autor desde su propia cuenta**, para que el historial refleje su propio trabajo.

### Prompts utilizados y análisis crítico
| Entrega | Prompt (textual) | Análisis crítico |
|---|---|---|
| N°1 | «holaa, me ayudas con la primera entrega del tpi de organizacion emprsarial para la tecnicatura? aca esta la consigna general, lo de la 1ra entrega […] y la plantilla que nos dijeron que tenemos que utilizar» | Prompt breve y sin restricciones de contenido: lo que orientó el resultado fue el contexto adjunto (consignas y plantilla). Ante la pregunta de la IA sobre qué organización usar, el autor eligió «una empresa ficticia de e-commerce/retail». El nombre, el rubro regional y el módulo fueron propuestos por la IA. |
| N°1 (corrección) | «pone Lisandro Iturri que es mi nombre y apellido y sacale lo de la fecha nomas y ya estaria» | Corrección de datos de la portada que la IA había dejado incompletos. |
| N°2 | «me ayudas con la entrega 2?» | Al no indicar restricciones, la IA asumió supuestos propios (trabajo individual, inicio el 05/10/2026, duración de cada tarea y valores de las metas). Son estimaciones razonables, pero no surgen de datos reales, por lo que deben poder justificarse en el coloquio. |
| N°3 | «me ayudas con la entrega 3 ahora?» | El prompt no pedía relacionar organigrama y datos; esa relación (campo rol e id_autorizante) fue una propuesta de la IA que el autor aceptó por su coherencia con el enfoque sistémico. |
| N°4 | «m ayudas ahora si con la entrega 4 y final?» | Ante las preguntas de la IA, el autor decidió realizar personalmente los commits, ramas y Pull Requests para que el historial de GitHub refleje su propio trabajo y no figure como generado por IA; realizar la revisión del PR en forma individual; y usar GitHub Projects. |

### Correcciones y decisiones humanas
- Elección del tipo de organización (empresa ficticia de comercio electrónico) entre las opciones planteadas.
- Corrección del nombre del autor y eliminación de la fecha en la portada de la Entrega N°1.
- Decisión de ejecutar personalmente todas las operaciones de Git y GitHub en lugar de delegarlas, para garantizar la autoría del historial.
- Decisión de documentar la revisión del Pull Request como autorrevisión, reconociendo su limitación.

### Revisiones de coherencia en la versión final
Al consolidar el TPI se corrigieron dos inconsistencias del contenido generado: la referencia a la **AFIP** en la Entrega N°1 (reemplazada por **ARCA**) y la falta del campo `fecha_hora_sincronizacion`, necesario para medir la Meta 1 (ver el commit `fix(datos)`). Estos casos muestran el principal riesgo observado: la IA produce contenido que parece correcto y bien redactado, pero que puede contener datos desactualizados o supuestos no verificados (por ejemplo, las duraciones del Gantt y los valores de las metas son estimaciones, no datos reales).

**Responsabilidad intelectual:** el autor asume la responsabilidad por la veracidad y coherencia conceptual de todo el trabajo, incluidos los posibles errores del modelo.
