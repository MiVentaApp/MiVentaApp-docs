# Proyecto Mobile MiVenta
## Modelo de Datos - Diagrama Entidad-Relación

![Diagrama Entidad-Relación](Diagramas/Diagrama%20Entidad-Relacion%20MiVenta.png)

---

## Diccionario de Datos

### Tabla: Usuario

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `google_id` | VARCHAR(255) | ID único de Google | NOT NULL, UNIQUE |
| `nombre_completo` | VARCHAR(100) | Nombre del vendedor | NOT NULL |
| `email` | VARCHAR(100) | Email de la cuenta de Google | NOT NULL, UNIQUE |
| `foto_perfil_url` | VARCHAR(255) | URL de foto de perfil de Google | NULL |
| `nombre_negocio` | VARCHAR(100) | Nombre del negocio (opcional) | NULL |
| `moneda` | VARCHAR(10) | Código de moneda (USD, MXN, etc.) | DEFAULT 'USD' |
| `ultima_sincronizacion` | TIMESTAMP | Última sincronización con servidor | NULL |
| `fecha_registro` | TIMESTAMP | Fecha de creación de cuenta | NOT NULL, DEFAULT CURRENT_TIMESTAMP |
| `activo` | BOOLEAN | Estado de la cuenta | NOT NULL, DEFAULT TRUE |

---

### Tabla: Producto

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `usuario_id` | INT | Referencia al vendedor | FK → Usuario(id), NOT NULL |
| `nombre` | VARCHAR(150) | Nombre del producto | NOT NULL |
| `descripcion` | TEXT | Descripción detallada | NULL |
| `categoria` | VARCHAR(50) | Categoría del producto | NULL |
| `costo_compra` | DECIMAL(10,2) | Costo de adquisición | NOT NULL, >= 0 |
| `precio_venta` | DECIMAL(10,2) | Precio de venta | NOT NULL, >= 0 |
| `stock` | INT | Cantidad disponible | NOT NULL, DEFAULT 0 |
| `margen_dinero` | DECIMAL(10,2) | Ganancia en dinero | CALCULATED |
| `margen_porcentaje` | DECIMAL(5,2) | Ganancia en porcentaje | CALCULATED |
| `fecha_registro` | TIMESTAMP | Fecha de creación | NOT NULL, DEFAULT CURRENT_TIMESTAMP |
| `fecha_actualizacion` | TIMESTAMP | Última modificación | ON UPDATE CURRENT_TIMESTAMP |
| `activo` | BOOLEAN | Producto activo | NOT NULL, DEFAULT TRUE |

---

### Tabla: Cliente

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `usuario_id` | INT | Referencia al vendedor | FK → Usuario(id), NOT NULL |
| `nombre_completo` | VARCHAR(100) | Nombre del cliente | NOT NULL |
| `telefono` | VARCHAR(20) | Teléfono de contacto | NULL |
| `email` | VARCHAR(100) | Email del cliente | NULL |
| `direccion` | TEXT | Dirección de entrega | NULL |
| `saldo_pendiente` | DECIMAL(10,2) | Deuda acumulada | DEFAULT 0 |
| `fecha_ultima_compra` | TIMESTAMP | Fecha de última venta | NULL |
| `fecha_registro` | TIMESTAMP | Fecha de registro | NOT NULL, DEFAULT CURRENT_TIMESTAMP |
| `activo` | BOOLEAN | Cliente activo | NOT NULL, DEFAULT TRUE |

---

### Tabla: Venta

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `usuario_id` | INT | Referencia al vendedor | FK → Usuario(id), NOT NULL |
| `cliente_id` | INT | Referencia al cliente | FK → Cliente(id), NOT NULL |
| `fecha_venta` | TIMESTAMP | Fecha de la venta | NOT NULL |
| `total` | DECIMAL(10,2) | Monto total de la venta | NOT NULL, >= 0 |
| `estado_pago` | ENUM | Estado del pago | 'Pendiente' o 'Pagada' |
| `total_pagado` | DECIMAL(10,2) | Total abonado | DEFAULT 0 |
| `saldo_pendiente` | DECIMAL(10,2) | Monto por cobrar | CALCULATED |
| `notas` | TEXT | Observaciones | NULL |
| `fecha_registro` | TIMESTAMP | Fecha de creación | NOT NULL, DEFAULT CURRENT_TIMESTAMP |
| `fecha_actualizacion` | TIMESTAMP | Última modificación | ON UPDATE CURRENT_TIMESTAMP |

---

### Tabla: DetalleVenta

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `venta_id` | INT | Referencia a la venta | FK → Venta(id), NOT NULL |
| `producto_id` | INT | Referencia al producto | FK → Producto(id), NOT NULL |
| `cantidad` | INT | Unidades vendidas | NOT NULL, > 0 |
| `precio_unitario` | DECIMAL(10,2) | Precio al momento de venta | NOT NULL |
| `costo_unitario` | DECIMAL(10,2) | Costo al momento de venta | NOT NULL |
| `subtotal` | DECIMAL(10,2) | Precio × Cantidad | CALCULATED |
| `ganancia_unitaria` | DECIMAL(10,2) | Ganancia por unidad | CALCULATED |
| `ganancia_total` | DECIMAL(10,2) | Ganancia total del item | CALCULATED |

---

### Tabla: Pago

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `venta_id` | INT | Referencia a la venta | FK → Venta(id), NOT NULL |
| `cliente_id` | INT | Referencia al cliente | FK → Cliente(id), NOT NULL |
| `monto` | DECIMAL(10,2) | Cantidad abonada | NOT NULL, > 0 |
| `metodo_pago` | ENUM | Forma de pago | 'Efectivo', 'Transferencia', 'Tarjeta', 'Otro' |
| `fecha_pago` | TIMESTAMP | Fecha del pago | NOT NULL |
| `notas` | TEXT | Observaciones | NULL |
| `fecha_registro` | TIMESTAMP | Fecha de registro | NOT NULL, DEFAULT CURRENT_TIMESTAMP |

---

### Tabla: Categoria

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `usuario_id` | INT | Referencia al vendedor | FK → Usuario(id), NOT NULL |
| `nombre` | VARCHAR(50) | Nombre de categoría | NOT NULL |
| `descripcion` | TEXT | Descripción | NULL |
| `color` | VARCHAR(20) | Color en hex (#RRGGBB) | NULL |
| `fecha_registro` | TIMESTAMP | Fecha de creación | NOT NULL, DEFAULT CURRENT_TIMESTAMP |

---

### Tabla: MovimientoInventario

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `producto_id` | INT | Referencia al producto | FK → Producto(id), NOT NULL |
| `venta_id` | INT | Venta que generó movimiento | FK → Venta(id), NULL |
| `tipo` | ENUM | Tipo de movimiento | 'Entrada', 'Salida', 'Ajuste' |
| `cantidad` | INT | Cantidad del movimiento | NOT NULL |
| `stock_anterior` | INT | Stock antes del movimiento | NOT NULL |
| `stock_nuevo` | INT | Stock después del movimiento | NOT NULL |
| `motivo` | VARCHAR(100) | Razón del movimiento | NULL |
| `fecha_movimiento` | TIMESTAMP | Fecha del movimiento | NOT NULL, DEFAULT CURRENT_TIMESTAMP |

---

### Tabla: SyncQueue (Solo Android Local)

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `tipo_operacion` | ENUM | Tipo de cambio | 'INSERT', 'UPDATE', 'DELETE' |
| `tabla` | VARCHAR(50) | Nombre de la tabla afectada | NOT NULL |
| `registro_id` | INT | ID del registro afectado | NOT NULL |
| `datos_json` | TEXT | Datos a sincronizar en JSON | NULL |
| `estado` | ENUM | Estado de sincronización | 'Pendiente', 'Sincronizando', 'Completado', 'Error' |
| `intentos` | INT | Número de intentos fallidos | DEFAULT 0 |
| `mensaje_error` | TEXT | Descripción del error si falla | NULL |
| `fecha_creacion` | TIMESTAMP | Cuándo se creó la operación | NOT NULL, DEFAULT CURRENT_TIMESTAMP |
| `fecha_sincronizacion` | TIMESTAMP | Cuándo se sincronizó | NULL |

**Nota:** Esta tabla existe solo en la base de datos local de Android (Room) y no en el servidor.

---

### Tabla: ProductoImagen (Nueva)

| Campo | Tipo | Descripción | Restricciones |
|-------|------|-------------|---------------|
| `id` | INT | Identificador único | PK, AUTO_INCREMENT |
| `producto_id` | INT | Referencia al producto | FK → Producto(id), NOT NULL |
| `url_local` | VARCHAR(255) | Ruta local en dispositivo | NULL |
| `url_remota` | VARCHAR(255) | URL en servidor/cloud | NULL |
| `orden` | INT | Orden de visualización | DEFAULT 1 |
| `sincronizado` | BOOLEAN | Si está en servidor | DEFAULT FALSE |
| `fecha_registro` | TIMESTAMP | Fecha de creación | NOT NULL, DEFAULT CURRENT_TIMESTAMP |

---

## Índices Recomendados

```sql
-- Índices para mejorar rendimiento de consultas

-- Usuario
CREATE UNIQUE INDEX idx_usuario_email ON Usuario(email);
CREATE UNIQUE INDEX idx_usuario_google_id ON Usuario(google_id);

-- Producto
CREATE INDEX idx_producto_usuario ON Producto(usuario_id);
CREATE INDEX idx_producto_categoria ON Producto(categoria);
CREATE INDEX idx_producto_activo ON Producto(activo);

-- Cliente
CREATE INDEX idx_cliente_usuario ON Cliente(usuario_id);
CREATE INDEX idx_cliente_nombre ON Cliente(nombre_completo);
CREATE INDEX idx_cliente_saldo ON Cliente(saldo_pendiente);

-- Venta
CREATE INDEX idx_venta_usuario ON Venta(usuario_id);
CREATE INDEX idx_venta_cliente ON Venta(cliente_id);
CREATE INDEX idx_venta_fecha ON Venta(fecha_venta);
CREATE INDEX idx_venta_estado ON Venta(estado_pago);

-- DetalleVenta
CREATE INDEX idx_detalle_venta ON DetalleVenta(venta_id);
CREATE INDEX idx_detalle_producto ON DetalleVenta(producto_id);

-- Pago
CREATE INDEX idx_pago_venta ON Pago(venta_id);
CREATE INDEX idx_pago_cliente ON Pago(cliente_id);
CREATE INDEX idx_pago_fecha ON Pago(fecha_pago);

-- MovimientoInventario
CREATE INDEX idx_movimiento_producto ON MovimientoInventario(producto_id);
CREATE INDEX idx_movimiento_fecha ON MovimientoInventario(fecha_movimiento);

-- SyncQueue (solo Room/Android)
CREATE INDEX idx_sync_estado ON SyncQueue(estado);
CREATE INDEX idx_sync_tabla ON SyncQueue(tabla);
CREATE INDEX idx_sync_fecha ON SyncQueue(fecha_creacion);

-- ProductoImagen
CREATE INDEX idx_producto_imagen_producto ON ProductoImagen(producto_id);
CREATE INDEX idx_producto_imagen_sincronizado ON ProductoImagen(sincronizado);
```

---

## Reglas de Negocio Implementadas en BD

### 1. Calcular márgenes automáticamente al insertar/actualizar producto

```sql
DELIMITER //
CREATE TRIGGER trg_producto_calcular_margenes
BEFORE INSERT OR UPDATE ON Producto
FOR EACH ROW
BEGIN
    SET NEW.margen_dinero = NEW.precio_venta - NEW.costo_compra;
    SET NEW.margen_porcentaje = ((NEW.precio_venta - NEW.costo_compra) / NEW.costo_compra) * 100;
END//
DELIMITER ;
```

### 2. Actualizar stock al registrar venta

```sql
DELIMITER //
CREATE TRIGGER trg_detalle_venta_actualizar_stock
AFTER INSERT ON DetalleVenta
FOR EACH ROW
BEGIN
    UPDATE Producto 
    SET stock = stock - NEW.cantidad 
    WHERE id = NEW.producto_id;
    
    -- Registrar movimiento de inventario
    INSERT INTO MovimientoInventario (producto_id, venta_id, tipo, cantidad, stock_anterior, stock_nuevo, motivo)
    VALUES (
        NEW.producto_id, 
        NEW.venta_id, 
        'Salida', 
        NEW.cantidad,
        (SELECT stock + NEW.cantidad FROM Producto WHERE id = NEW.producto_id),
        (SELECT stock FROM Producto WHERE id = NEW.producto_id),
        'Venta registrada'
    );
END//
DELIMITER ;
```

### 3. Actualizar saldo pendiente al registrar pago

```sql
DELIMITER //
CREATE TRIGGER trg_pago_actualizar_venta
AFTER INSERT ON Pago
FOR EACH ROW
BEGIN
    UPDATE Venta 
    SET 
        total_pagado = total_pagado + NEW.monto,
        saldo_pendiente = total - (total_pagado + NEW.monto),
        estado_pago = IF(total <= (total_pagado + NEW.monto), 'Pagada', 'Pendiente')
    WHERE id = NEW.venta_id;
    
    -- Actualizar saldo del cliente
    UPDATE Cliente
    SET saldo_pendiente = (
        SELECT COALESCE(SUM(saldo_pendiente), 0)
        FROM Venta
        WHERE cliente_id = NEW.cliente_id AND estado_pago = 'Pendiente'
    )
    WHERE id = NEW.cliente_id;
END//
DELIMITER ;
```

### 4. Actualizar fecha última compra del cliente

```sql
DELIMITER //
CREATE TRIGGER trg_venta_actualizar_cliente
AFTER INSERT ON Venta
FOR EACH ROW
BEGIN
    UPDATE Cliente 
    SET fecha_ultima_compra = NEW.fecha_venta
    WHERE id = NEW.cliente_id;
END//
DELIMITER ;
```

---

## Relaciones entre Tablas

### Relaciones Principales:

1. **Usuario → Producto** (1:N)
   - Un usuario puede tener múltiples productos
   - Cada producto pertenece a un solo usuario

2. **Usuario → Cliente** (1:N)
   - Un usuario puede tener múltiples clientes
   - Cada cliente pertenece a un solo usuario

3. **Usuario → Categoria** (1:N)
   - Un usuario puede crear múltiples categorías
   - Cada categoría pertenece a un solo usuario

4. **Cliente → Venta** (1:N)
   - Un cliente puede tener múltiples ventas
   - Cada venta pertenece a un solo cliente

5. **Venta → DetalleVenta** (1:N)
   - Una venta puede tener múltiples detalles (productos)
   - Cada detalle pertenece a una sola venta

6. **Venta → Pago** (1:N)
   - Una venta puede tener múltiples pagos (abonos)
   - Cada pago pertenece a una sola venta

7. **Producto → DetalleVenta** (1:N)
   - Un producto puede estar en múltiples ventas
   - Cada detalle referencia a un solo producto

8. **Producto → MovimientoInventario** (1:N)
   - Un producto puede tener múltiples movimientos
   - Cada movimiento pertenece a un solo producto

9. **Producto → ProductoImagen** (1:N)
   - Un producto puede tener múltiples imágenes (máximo 3)
   - Cada imagen pertenece a un solo producto

---

## Consideraciones de Diseño

### Campos Calculados:
- **Producto.margen_dinero**: Calculado automáticamente via trigger
- **Producto.margen_porcentaje**: Calculado automáticamente via trigger
- **Venta.saldo_pendiente**: Calculado como `total - total_pagado`
- **DetalleVenta.subtotal**: Calculado como `precio_unitario × cantidad`
- **DetalleVenta.ganancia_unitaria**: Calculado como `precio_unitario - costo_unitario`
- **DetalleVenta.ganancia_total**: Calculado como `ganancia_unitaria × cantidad`

### Integridad Referencial:
- Todas las claves foráneas deben configurarse con `ON DELETE RESTRICT` para evitar eliminaciones accidentales de datos con referencias
- Excepción: `MovimientoInventario.venta_id` puede ser NULL para movimientos no relacionados con ventas

### Auditoría:
- Todas las tablas principales incluyen campos de timestamp para rastreo
- La tabla `MovimientoInventario` funciona como log de auditoría para cambios en el inventario

### Arquitectura Android:
- **Base de datos local:** Room Database (SQLite) en el dispositivo
- **Sincronización:** WorkManager para tareas en segundo plano
- **Autenticación:** Google Sign-In con tokens JWT
- **Almacenamiento seguro:** EncryptedSharedPreferences para tokens
- **Caché de imágenes:** Glide o Coil para optimizar carga
- **Offline-first:** Todas las operaciones funcionan sin conexión
- **Resolución de conflictos:** Last-write-wins con timestamps

---

*Documento generado para el proyecto Mobile MiVenta*  
*Fecha: Enero 2026*
