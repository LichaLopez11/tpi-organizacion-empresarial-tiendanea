# Diccionario de datos – Módulo de Inventario

Datos mínimos que necesita el módulo para saber cuánto stock hay de cada producto, de dónde proviene, quién lo modificó y si el cambio ya se reflejó en la tienda online.

**Convenciones:** nombres en minúscula con guion bajo. Tipos: String, Integer, Decimal, Boolean y DateTime. PK = clave primaria, FK = clave foránea.

> **Actualización (Entrega N°4):** se agregó el campo `fecha_hora_sincronizacion` a MOVIMIENTO_STOCK. Al diseñar el indicador de tiempo de sincronización se detectó que solo se registraba *si* un movimiento estaba sincronizado, pero no *cuándo*, por lo que la Meta 1 no se podía medir.

## PRODUCTO
| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| `id_producto` | Integer | PK | Identificador único del producto, generado automáticamente por el sistema. |
| `codigo_sku` | String | — | Código interno del artículo (por ejemplo, YER-001). Debe ser único y es el que se usa en el depósito para identificar la mercadería. |
| `nombre` | String | — | Nombre comercial del producto tal como se muestra en la tienda online. |
| `categoria` | String | — | Rubro del producto: yerba mate, artesanías, alimentos o textiles. |
| `precio_venta` | Decimal | — | Precio de venta al público en pesos argentinos, con dos decimales. |
| `stock_actual` | Integer | — | Unidades disponibles en el depósito. Se actualiza con cada movimiento de stock y es el valor que se publica en la tienda. |
| `stock_minimo` | Integer | — | Cantidad por debajo de la cual el sistema genera una alerta de reposición. |
| `id_proveedor` | Integer | FK | Proveedor que abastece el producto (referencia a PROVEEDOR). |
| `activo` | Boolean | — | Indica si el producto está a la venta (true) o fue dado de baja del catálogo (false). |

## PROVEEDOR
| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| `id_proveedor` | Integer | PK | Identificador único del proveedor. |
| `razon_social` | String | — | Nombre o razón social del productor o empresa proveedora. |
| `cuit` | String | — | CUIT del proveedor (11 dígitos). Se guarda como texto porque no se usa en cálculos y así se conservan ceros iniciales. |
| `localidad` | String | — | Localidad de origen del proveedor dentro del NEA. |
| `provincia` | String | — | Provincia de origen: Corrientes, Chaco, Misiones o Formosa. |
| `telefono` | String | — | Teléfono de contacto para coordinar pedidos de reposición. |
| `email` | String | — | Correo electrónico al que se envían los pedidos de reposición. |
| `activo` | Boolean | — | Indica si el proveedor sigue trabajando con TiendaNEA. |

## USUARIO
| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| `id_usuario` | Integer | PK | Identificador único del usuario del sistema. |
| `nombre_apellido` | String | — | Nombre y apellido del empleado. |
| `email` | String | — | Correo electrónico, utilizado como nombre de usuario para ingresar al sistema. Debe ser único. |
| `contrasena_hash` | String | — | Contraseña cifrada. Por seguridad nunca se almacena la contraseña en texto plano. |
| `rol` | String | — | Perfil de acceso según la unidad del organigrama a la que pertenece: DEPOSITO, VENTAS, COMPRAS, GERENCIA_OPERACIONES o SISTEMAS. |
| `activo` | Boolean | — | Indica si el usuario puede ingresar al sistema; se desactiva cuando el empleado deja la empresa. |

## MOVIMIENTO_STOCK
| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| `id_movimiento` | Integer | PK | Identificador único del movimiento. |
| `id_producto` | Integer | FK | Producto afectado por el movimiento (referencia a PRODUCTO). |
| `id_usuario` | Integer | FK | Usuario que registró el movimiento (referencia a USUARIO). Las ventas que llegan automáticamente desde la tienda se asignan a un usuario de sistema con rol SISTEMAS. |
| `tipo_movimiento` | String | — | Tipo de operación: INGRESO (compra a proveedor), VENTA, DEVOLUCION o AJUSTE (corrección por rotura, pérdida o error de conteo). |
| `cantidad` | Integer | — | Unidades movidas. Siempre es un número positivo; el tipo de movimiento define si suma o resta al stock. |
| `fecha_hora` | DateTime | — | Fecha y hora exacta en que se registró el movimiento. |
| `id_pedido_tienda` | String | — | Número del pedido en la tienda online. Solo se completa en ventas y devoluciones. |
| `id_autorizante` | Integer | FK | Usuario con rol GERENCIA_OPERACIONES que aprobó el movimiento. Obligatorio solo en los ajustes. |
| `sincronizado` | Boolean | — | Indica si el cambio ya se reflejó en el stock publicado en la tienda online. |
| `fecha_hora_sincronizacion` | DateTime | — | Fecha y hora en que el cambio se reflejó en la tienda. Permite medir el tiempo de sincronización (Meta 1). Campo incorporado en la Parte IV. |

## Relaciones
- PROVEEDOR 1 → N PRODUCTO
- PRODUCTO 1 → N MOVIMIENTO_STOCK
- USUARIO 1 → N MOVIMIENTO_STOCK (en los ajustes, un segundo usuario actúa como autorizante mediante `id_autorizante`)

## Roles y permisos (vínculo con el organigrama)
| Rol | Unidad del organigrama | Puede |
|---|---|---|
| DEPOSITO | Depósito e Inventario | Registrar ingresos y devoluciones, solicitar ajustes |
| GERENCIA_OPERACIONES | Gerencia de Operaciones | Autorizar ajustes |
| VENTAS | Ventas y Atención al Cliente | Consultar stock (no modificarlo) |
| COMPRAS | Compras y Proveedores | Recibir alertas de stock mínimo y gestionar proveedores |
| SISTEMAS | Desarrollo y Soporte | Administrar usuarios y la sincronización con la tienda |
