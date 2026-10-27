# Historias de usuario

Definidas en la tarea 2 del Diagrama de Gantt (*Especificación de requerimientos e historias de usuario*). Cada una es un issue del repositorio y una tarjeta del tablero de GitHub Projects.

## HU-01: Registrar el ingreso de mercadería

**Como** encargado de depósito, **quiero** registrar en el sistema el ingreso de la mercadería recibida de los proveedores, **para** que el stock se actualice automáticamente en la tienda online sin cargar planillas manuales.

**Criterios de aceptación**

- [ ] El ingreso genera un MOVIMIENTO_STOCK de tipo INGRESO con producto, cantidad y usuario.
- [ ] El stock publicado en la tienda se actualiza en menos de 5 segundos (Meta 1).
- [ ] Si hay diferencias, se puede solicitar un AJUSTE que queda pendiente hasta que la Gerencia de Operaciones lo autorice.

- **Prioridad:** Alta
- **Estado al cierre del TPI:** En progreso
- **Gantt:** tareas 7 y 8 · **BPMN:** Depósito e Inventario, Gerencia de Operaciones, Sistema · **Datos:** PRODUCTO, MOVIMIENTO_STOCK, USUARIO

## HU-02: Descontar stock con cada venta online

**Como** responsable de ventas, **quiero** que cada venta online descuente automáticamente el stock disponible, **para** no confirmar pedidos de productos que no están en el depósito.

**Criterios de aceptación**

- [ ] Antes de confirmar un pedido se verifica el stock; si no alcanza, el pedido se cancela y se avisa al cliente.
- [ ] Toda venta confirmada genera un movimiento VENTA con el número de pedido de la tienda.
- [ ] Las devoluciones reintegran el stock con un movimiento DEVOLUCION.

- **Prioridad:** Alta
- **Estado al cierre del TPI:** Por hacer
- **Gantt:** tareas 7 y 8 · **BPMN:** Sistema · **Datos:** PRODUCTO, MOVIMIENTO_STOCK

## HU-03: Alerta de stock mínimo

**Como** responsable de compras, **quiero** recibir una alerta cuando un producto llegue a su stock mínimo, **para** pedir la reposición al proveedor antes de quedarme sin mercadería.

**Criterios de aceptación**

- [ ] La alerta se genera cuando stock_actual es menor o igual a stock_minimo.
- [ ] La alerta indica el producto, el stock actual y el contacto del proveedor.
- [ ] Existe un listado de productos que están por debajo del mínimo.

- **Prioridad:** Media
- **Estado al cierre del TPI:** Por hacer
- **Gantt:** tareas 9 · **BPMN:** Sistema, Compras y Proveedores · **Datos:** PRODUCTO, PROVEEDOR
