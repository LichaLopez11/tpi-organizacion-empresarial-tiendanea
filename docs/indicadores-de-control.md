# Indicadores de control y estándares de desempeño

El control sigue cuatro pasos: **establecer estándares → medir → comparar → corregir**. Los estándares surgen de las metas de la Entrega N°2 y las mediciones usan los datos del diccionario de la Entrega N°3.

## Auditoría técnica del sistema
| Indicador | Cálculo | Estándar | Frecuencia | Responsable |
|---|---|---|---|---|
| Tiempo de sincronización | fecha_hora_sincronizacion − fecha_hora de cada MOVIMIENTO_STOCK | ≤ 5 s en el 95% de los movimientos (Meta 1) | Diaria | Jefatura de Sistemas |
| Tiempo de respuesta | Duración de las consultas de stock (registros del servidor) | ≤ 2 s en el 95% de las consultas (Meta 2) | Semanal | Jefatura de Sistemas |
| Exactitud de inventario | Productos cuyo conteo físico coincide con stock_actual / productos contados × 100 | ≥ 98% | Mensual | Gerencia de Operaciones |
| Cancelaciones por falta de stock | Pedidos cancelados por falta de stock / pedidos totales × 100 | −80% respecto del trimestre base (Meta 3) | Mensual | Gerencia Comercial |
| Ajustes sin autorización | Movimientos AJUSTE con id_autorizante vacío | 0 | Semanal | Gerencia de Operaciones |
| Quiebres de stock | Productos activos con stock_actual = 0 / productos activos × 100 | ≤ 2% | Semanal | Compras y Proveedores |
| Disponibilidad del sistema | Horas en funcionamiento / horas del período × 100 | ≥ 99% mensual | Mensual | Jefatura de Sistemas |

## Gestión del proyecto
| Indicador | Cálculo | Estándar | Fuente |
|---|---|---|---|
| Cumplimiento del cronograma | Tareas del Gantt terminadas en fecha / tareas que debían terminar × 100 | ≥ 90%; desvío máximo de 5 días hábiles en el hito final (Meta 4) | Diagrama de Gantt |
| Avance del backlog | Historias de usuario en Listo / historias totales × 100 | 100% al 11/12/2026 | GitHub Projects |
| Cambios integrados con revisión | Pull Requests fusionados con revisión / cambios integrados a main × 100 | 100% (ningún cambio directo a main) | Historial de GitHub |
| Defectos críticos abiertos | Defectos críticos de las pruebas de aceptación sin resolver | 0 al pasar a producción | Issues del repositorio |

## Acciones correctivas previstas
- **Sincronización lenta:** revisar la cola de envíos a la tienda y los reintentos fallidos; priorizar productos con poco stock.
- **Exactitud < 98%:** aumentar la frecuencia de los conteos cíclicos e identificar en el historial qué tipo de movimiento genera las diferencias.
- **Ajuste sin autorización:** revisar los permisos del rol DEPOSITO y agregar una validación que impida guardar un AJUSTE sin `id_autorizante`.
- **Desvío del cronograma:** reprogramar tareas no críticas y evaluar reducir el alcance de la HU-03 (reportes) para proteger la puesta en producción.
