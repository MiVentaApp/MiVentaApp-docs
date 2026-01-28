# Proyecto Mobile MiVenta
## Criterios de Aceptación por User Story

---

## EPIC 1: Gestión de Autenticación y Usuarios

### Feature 1.1: Registro de Usuarios

#### Story 1.1.1: Como vendedor independiente quiero crear una cuenta de usuario para acceder a la plataforma

**Criterios de Aceptación:**
- El formulario debe solicitar: nombre completo, email y contraseña
- El email debe tener formato válido (contener @ y dominio)
- La contraseña debe tener mínimo 8 caracteres
- El email no puede estar registrado previamente
- Todos los campos son obligatorios
- Se debe mostrar mensaje de error si falta algún campo
- Se debe mostrar mensaje de error si el email ya existe
- Al registrarse exitosamente, se redirige al usuario a la pantalla de inicio de sesión o dashboard
- La contraseña debe almacenarse encriptada en la base de datos

#### Story 1.1.2: Como vendedor independiente quiero recibir confirmación de mi registro para saber que mi cuenta fue creada exitosamente

**Criterios de Aceptación:**
- Se muestra un mensaje de confirmación después del registro exitoso
- El mensaje debe indicar claramente que la cuenta fue creada
- Opcionalmente, se envía un email de bienvenida (futuro)

---

### Feature 1.2: Inicio de Sesión

#### Story 1.2.1: Como vendedor independiente quiero iniciar sesión con mi email y contraseña para acceder a mi información personal del negocio

**Criterios de Aceptación:**
- El formulario debe solicitar email y contraseña
- Ambos campos son obligatorios
- Se valida que el email exista en el sistema
- Se valida que la contraseña sea correcta
- Se muestra mensaje de error si las credenciales son incorrectas
- Al iniciar sesión correctamente, se redirige al dashboard
- Se crea una sesión que persiste mientras el usuario no cierre sesión
- La sesión debe expirar después de 7 días de inactividad

#### Story 1.2.2: Como vendedor independiente quiero cerrar sesión para proteger mi información cuando no esté usando la aplicación

**Criterios de Aceptación:**
- Existe un botón de "Cerrar Sesión" visible en la interfaz
- Al hacer clic, la sesión se cierra inmediatamente
- El usuario es redirigido a la pantalla de inicio de sesión
- No se puede acceder a páginas protegidas sin iniciar sesión nuevamente
- Se muestra confirmación de que la sesión fue cerrada

#### Story 1.2.3: Como vendedor independiente quiero recuperar mi contraseña para poder acceder nuevamente si la olvido

**Criterios de Aceptación:**
- Existe un enlace "¿Olvidaste tu contraseña?" en la pantalla de inicio de sesión
- Se solicita el email registrado
- Se valida que el email exista en el sistema
- Se envía un email con instrucciones de recuperación (o link temporal)
- Se muestra mensaje confirmando que se envió el email
- El link de recuperación expira después de 24 horas
- El usuario puede establecer una nueva contraseña desde el link

---

### Feature 1.3: Perfil de Usuario

#### Story 1.3.1: Como vendedor independiente quiero ver mi información de perfil para verificar mis datos personales

**Criterios de Aceptación:**
- Se muestra nombre completo y email del usuario
- Se muestra fecha de registro en la plataforma
- La información se carga desde la base de datos del usuario autenticado
- La interfaz es clara y organizada

#### Story 1.3.2: Como vendedor independiente quiero editar mi información de perfil para mantener mis datos actualizados

**Criterios de Aceptación:**
- Se puede editar nombre completo
- Se puede cambiar la contraseña (solicitando la actual)
- El email no se puede modificar (o requiere verificación adicional)
- Se valida que la nueva contraseña tenga mínimo 8 caracteres
- Se muestra mensaje de confirmación al guardar cambios
- Los cambios se reflejan inmediatamente en la base de datos
- Se muestra mensaje de error si la contraseña actual es incorrecta

---

## EPIC 2: Gestión de Productos

### Feature 2.1: Catálogo de Productos

#### Story 2.1.1: Como vendedor independiente quiero registrar un nuevo producto con nombre, descripción, costo de compra y precio de venta para tener un catálogo de mis productos

**Criterios de Aceptación:**
- El formulario solicita: nombre, descripción (opcional), categoría, costo de compra, precio de venta, cantidad inicial
- Nombre, costo de compra y precio de venta son obligatorios
- Costo de compra y precio de venta deben ser números positivos
- La cantidad debe ser un número entero no negativo
- Se muestra mensaje de error si falta algún campo obligatorio
- Al guardar, el producto se registra asociado al usuario actual
- Se muestra mensaje de confirmación al crear el producto exitosamente
- Se redirige a la lista de productos o muestra el margen de ganancia calculado

#### Story 2.1.2: Como vendedor independiente quiero ver una lista de todos mis productos para conocer mi inventario actual

**Criterios de Aceptación:**
- Se muestra una tabla/lista con todos los productos del usuario
- Cada producto muestra: nombre, categoría, costo de compra, precio de venta, margen de ganancia, stock
- La lista se ordena por fecha de creación (más recientes primero) por defecto
- Se puede ordenar por nombre, precio, o margen
- Si no hay productos, se muestra un mensaje indicándolo
- Se incluye un botón para agregar nuevo producto

#### Story 2.1.3: Como vendedor independiente quiero buscar productos por nombre o categoría para encontrarlos rápidamente

**Criterios de Aceptación:**
- Existe un campo de búsqueda en la lista de productos
- La búsqueda filtra por nombre de producto (sin distinción de mayúsculas/minúsculas)
- Opcionalmente se puede filtrar por categoría mediante un selector
- Los resultados se actualizan en tiempo real mientras se escribe
- Si no hay resultados, se muestra mensaje indicándolo
- Se puede limpiar el filtro para ver todos los productos nuevamente

#### Story 2.1.4: Como vendedor independiente quiero editar la información de un producto para actualizar precios o descripciones

**Criterios de Aceptación:**
- Cada producto tiene un botón/ícono de "Editar"
- Se abre un formulario con los datos actuales del producto
- Se pueden modificar todos los campos (nombre, descripción, categoría, costo, precio, stock)
- Se validan los mismos criterios que al crear un producto
- Los cambios se guardan en la base de datos
- Se muestra mensaje de confirmación al actualizar
- El margen de ganancia se recalcula automáticamente si cambian los precios

#### Story 2.1.5: Como vendedor independiente quiero eliminar un producto para mantener mi catálogo limpio de artículos que ya no vendo

**Criterios de Aceptación:**
- Cada producto tiene un botón/ícono de "Eliminar"
- Se solicita confirmación antes de eliminar ("¿Estás seguro?")
- Si el producto tiene ventas asociadas, no se permite eliminar (o se marca como inactivo)
- Si no tiene ventas, se elimina permanentemente de la base de datos
- Se muestra mensaje de confirmación al eliminar exitosamente
- La lista se actualiza automáticamente después de eliminar

---

### Feature 2.2: Cálculo de Márgenes

#### Story 2.2.1: Como vendedor independiente quiero ver el margen de ganancia calculado automáticamente (en dinero y porcentaje) para saber cuánto ganaré por cada producto

**Criterios de Aceptación:**
- El margen en dinero se calcula como: Precio de venta - Costo de compra
- El margen en porcentaje se calcula como: ((Precio venta - Costo compra) / Costo compra) × 100
- Ambos valores se muestran al crear/editar un producto
- Los valores se actualizan automáticamente al cambiar costo o precio
- Se muestran con formato adecuado (moneda y porcentaje con 2 decimales)
- Si el margen es negativo, se resalta en color rojo

#### Story 2.2.2: Como vendedor independiente quiero simular diferentes precios de venta para decidir el precio óptimo antes de vender

**Criterios de Aceptación:**
- Existe una calculadora de margen en la pantalla de productos
- Se puede ingresar costo de compra y diferentes precios de venta
- Se muestra el margen resultante (dinero y porcentaje) en tiempo real
- Se pueden probar múltiples escenarios sin guardar
- Opcionalmente se muestra una tabla con rangos de precios sugeridos
- La simulación no afecta los datos guardados hasta que se confirme

#### Story 2.2.3: Como vendedor independiente quiero recibir una alerta si mi precio de venta es menor al costo de compra para evitar vender con pérdidas

**Criterios de Aceptación:**
- Si Precio de venta < Costo de compra, se muestra mensaje de advertencia
- El mensaje indica claramente que se está vendiendo con pérdida
- El margen negativo se resalta en color rojo
- Se permite guardar de todos modos (puede ser liquidación intencional)
- La advertencia es visible y clara en el formulario

---

### Feature 2.3: Control de Inventario

#### Story 2.3.1: Como vendedor independiente quiero registrar la cantidad disponible de cada producto para llevar control de mi stock

**Criterios de Aceptación:**
- Al crear un producto se puede ingresar cantidad inicial
- Se puede editar manualmente la cantidad en cualquier momento
- La cantidad debe ser un número entero no negativo
- Se muestra la cantidad actual en la lista de productos
- Se puede filtrar productos por stock disponible

#### Story 2.3.2: Como vendedor independiente quiero que el stock se actualice automáticamente al hacer una venta para tener inventario en tiempo real

**Criterios de Aceptación:**
- Al registrar una venta, se descuenta la cantidad vendida del stock
- Si no hay stock suficiente, se muestra advertencia pero se permite continuar
- El stock actualizado se refleja inmediatamente en el catálogo
- Se lleva registro de movimientos de stock (entrada/salida)
- Si se elimina una venta, el stock se restaura

#### Story 2.3.3: Como vendedor independiente quiero ver productos con stock bajo para saber cuándo debo reabastecerme

**Criterios de Aceptación:**
- Se resaltan productos con stock = 0 (en rojo)
- Se resaltan productos con stock <= 5 (en amarillo/naranja)
- Existe un filtro para ver solo productos con stock bajo
- Opcionalmente se muestra notificación en el dashboard
- Se puede configurar el umbral de "stock bajo" por producto

---

## EPIC 3: Gestión de Clientes

### Feature 3.1: Registro de Clientes

#### Story 3.1.1: Como vendedor independiente quiero registrar un nuevo cliente con nombre, teléfono y dirección para tener un directorio de mis compradores

**Criterios de Aceptación:**
- El formulario solicita: nombre completo, teléfono, email (opcional), dirección (opcional)
- El nombre es obligatorio
- El teléfono debe tener formato válido (números)
- Se valida que no exista otro cliente con el mismo nombre y teléfono
- Se muestra mensaje de error si falta el nombre
- Al guardar, el cliente se asocia al usuario actual
- Se muestra mensaje de confirmación al crear exitosamente

#### Story 3.1.2: Como vendedor independiente quiero ver una lista de todos mis clientes para acceder rápidamente a su información

**Criterios de Aceptación:**
- Se muestra una tabla/lista con todos los clientes del usuario
- Cada cliente muestra: nombre, teléfono, saldo pendiente, última compra
- La lista se ordena alfabéticamente por defecto
- Se puede ordenar por saldo pendiente o última compra
- Si no hay clientes, se muestra mensaje indicándolo
- Se incluye botón para agregar nuevo cliente

#### Story 3.1.3: Como vendedor independiente quiero buscar clientes por nombre o teléfono para encontrarlos fácilmente

**Criterios de Aceptación:**
- Existe un campo de búsqueda en la lista de clientes
- La búsqueda filtra por nombre (sin distinción de mayúsculas)
- También filtra por teléfono parcial
- Los resultados se actualizan en tiempo real
- Si no hay resultados, se muestra mensaje indicándolo
- Se puede limpiar el filtro fácilmente

#### Story 3.1.4: Como vendedor independiente quiero editar la información de un cliente para mantener sus datos actualizados

**Criterios de Aceptación:**
- Cada cliente tiene botón de "Editar"
- Se abre formulario con datos actuales
- Se pueden modificar todos los campos
- Se validan los mismos criterios que al crear
- Los cambios se guardan en la base de datos
- Se muestra mensaje de confirmación

#### Story 3.1.5: Como vendedor independiente quiero eliminar un cliente para limpiar mi base de datos de contactos inactivos

**Criterios de Aceptación:**
- Cada cliente tiene botón de "Eliminar"
- Se solicita confirmación antes de eliminar
- Si el cliente tiene ventas asociadas, no se elimina (se marca como inactivo)
- Si no tiene ventas, se elimina permanentemente
- Se muestra mensaje de confirmación
- La lista se actualiza automáticamente

---

### Feature 3.2: Historial de Clientes

#### Story 3.2.1: Como vendedor independiente quiero ver el historial de compras de un cliente para conocer su comportamiento de compra

**Criterios de Aceptación:**
- Se puede acceder al detalle del cliente desde la lista
- Se muestra lista de todas las ventas realizadas al cliente
- Cada venta muestra: fecha, productos, total, estado de pago
- Las ventas se ordenan de más reciente a más antigua
- Se puede ver el detalle completo de cada venta
- Se muestra total comprado histórico

#### Story 3.2.2: Como vendedor independiente quiero ver el saldo pendiente de cada cliente para saber quién me debe dinero

**Criterios de Aceptación:**
- En la lista de clientes se muestra el saldo pendiente
- El saldo se calcula sumando todas las ventas pendientes de pago
- Los clientes con saldo > 0 se resaltan visualmente
- Se puede ordenar la lista por saldo pendiente (mayor a menor)
- El saldo se actualiza automáticamente al registrar pagos
- Se muestra con formato de moneda

#### Story 3.2.3: Como vendedor independiente quiero ver la fecha de la última compra de un cliente para identificar clientes activos e inactivos

**Criterios de Aceptación:**
- En la lista se muestra la fecha de última compra
- Si no ha comprado nunca, se indica claramente
- Se puede filtrar por clientes activos (compra reciente) o inactivos
- Se define "inactivo" como sin compras en los últimos 30 días
- Se puede ordenar por fecha de última compra

---

## EPIC 4: Gestión de Ventas

### Feature 4.1: Registro de Ventas

#### Story 4.1.1: Como vendedor independiente quiero crear una nueva venta seleccionando un cliente para asociar la transacción al comprador correcto

**Criterios de Aceptación:**
- El formulario de nueva venta incluye selector de cliente
- Se muestra lista desplegable con todos los clientes
- Se puede buscar cliente por nombre en el selector
- Opcionalmente se puede crear cliente nuevo desde el formulario
- El cliente seleccionado se asocia a la venta
- El campo cliente es obligatorio

#### Story 4.1.2: Como vendedor independiente quiero agregar múltiples productos a una venta con sus cantidades para registrar ventas de varios artículos

**Criterios de Aceptación:**
- Se puede agregar uno o más productos a la venta
- Cada producto incluye selector de producto y campo de cantidad
- Se muestra precio unitario automáticamente al seleccionar producto
- Se calcula subtotal por producto (precio × cantidad)
- Se puede eliminar un producto de la venta antes de guardar
- La cantidad debe ser un número entero positivo
- Se muestra advertencia si la cantidad excede el stock disponible

#### Story 4.1.3: Como vendedor independiente quiero ver el total de la venta calculado automáticamente para saber el monto exacto a cobrar

**Criterios de Aceptación:**
- El total se calcula sumando todos los subtotales de productos
- El total se actualiza automáticamente al agregar/quitar productos
- El total se actualiza al cambiar cantidades
- Se muestra con formato de moneda
- El cálculo es preciso con 2 decimales

#### Story 4.1.4: Como vendedor independiente quiero registrar la fecha de la venta para llevar un historial cronológico

**Criterios de Aceptación:**
- El formulario incluye campo de fecha
- Por defecto se establece la fecha actual
- Se puede modificar la fecha si es necesario (venta registrada con retraso)
- La fecha se guarda en formato estándar
- No se permiten fechas futuras

#### Story 4.1.5: Como vendedor independiente quiero guardar una venta para mantener el registro en el sistema

**Criterios de Aceptación:**
- Existe botón "Guardar venta"
- Se valida que haya al menos un producto agregado
- Se valida que haya cliente seleccionado
- Se guarda la venta con estado "Pendiente" por defecto
- Se actualiza el stock de productos vendidos
- Se muestra mensaje de confirmación
- Se redirige a detalle de venta o lista de ventas

---

### Feature 4.2: Listado y Consulta de Ventas

#### Story 4.2.1: Como vendedor independiente quiero ver una lista de todas mis ventas para tener un historial completo

**Criterios de Aceptación:**
- Se muestra tabla con todas las ventas del usuario
- Cada venta muestra: fecha, cliente, total, estado de pago
- Las ventas se ordenan por fecha (más recientes primero)
- Se puede acceder al detalle de cada venta
- Se muestra resumen: total de ventas, monto total vendido
- Si no hay ventas, se muestra mensaje indicándolo

#### Story 4.2.2: Como vendedor independiente quiero filtrar ventas por fecha para analizar períodos específicos

**Criterios de Aceptación:**
- Existe filtro con rango de fechas (desde - hasta)
- Se pueden seleccionar fechas mediante calendario
- Existen atajos: "Hoy", "Esta semana", "Este mes", "Últimos 30 días"
- Los resultados se actualizan al aplicar el filtro
- Se muestra cantidad de ventas en el período seleccionado
- Se puede limpiar el filtro

#### Story 4.2.3: Como vendedor independiente quiero filtrar ventas por cliente para ver el historial de un comprador específico

**Criterios de Aceptación:**
- Existe selector de cliente en los filtros
- Se muestra solo ventas del cliente seleccionado
- Se muestra total vendido a ese cliente
- Se puede combinar con filtro de fecha
- Se puede limpiar el filtro

#### Story 4.2.4: Como vendedor independiente quiero ver los detalles completos de una venta para revisar los productos vendidos y montos

**Criterios de Aceptación:**
- Al hacer clic en una venta se muestra el detalle completo
- Se muestra: fecha, cliente, lista de productos con cantidades y precios
- Se muestra subtotal por producto y total general
- Se muestra estado de pago y historial de pagos si existen
- Se puede imprimir o exportar el detalle (futuro)
- Existe botón para volver a la lista

#### Story 4.2.5: Como vendedor independiente quiero editar una venta para corregir errores en el registro

**Criterios de Aceptación:**
- Existe botón "Editar" en el detalle de venta
- Solo se pueden editar ventas con estado "Pendiente"
- Se pueden modificar productos, cantidades y cliente
- Se recalcula el total automáticamente
- Se actualiza el stock según los cambios
- Se muestra confirmación al guardar cambios
- Si la venta ya tiene pagos, se muestra advertencia

---

## EPIC 5: Gestión de Pagos

### Feature 5.1: Registro de Pagos

#### Story 5.1.1: Como vendedor independiente quiero marcar una venta como "Pagada" o "Pendiente" para saber su estado de cobro

**Criterios de Aceptación:**
- Al crear una venta se puede marcar como "Pagada" o "Pendiente"
- Por defecto las ventas se crean como "Pendiente"
- Se puede cambiar el estado desde el detalle de venta
- El estado se refleja visualmente (colores o íconos)
- Se actualiza inmediatamente en la base de datos

#### Story 5.1.2: Como vendedor independiente quiero registrar un pago completo de una venta para actualizar el estado a pagado

**Criterios de Aceptación:**
- Existe botón "Registrar pago" en ventas pendientes
- Se muestra formulario con monto de la venta
- Se puede seleccionar método de pago (efectivo, transferencia, otro)
- Se registra la fecha del pago (por defecto hoy)
- Al guardar, el estado de venta cambia a "Pagada"
- Se muestra confirmación del pago registrado
- El pago se guarda en el historial

#### Story 5.1.3: Como vendedor independiente quiero registrar un pago parcial (abono) a una venta para llevar control de deudas que se pagan en cuotas

**Criterios de Aceptación:**
- Se puede registrar un pago menor al total de la venta
- Se solicita el monto del abono
- El monto debe ser mayor a 0 y menor o igual al saldo pendiente
- Se registra método de pago y fecha
- El saldo pendiente se actualiza restando el abono
- La venta permanece en estado "Pendiente" hasta pago completo
- Se pueden registrar múltiples abonos
- Cada abono se guarda en el historial de pagos

#### Story 5.1.4: Como vendedor independiente quiero seleccionar el método de pago (efectivo, transferencia, etc.) para llevar registro de cómo cobré

**Criterios de Aceptación:**
- Al registrar pago se muestra selector de método
- Opciones: Efectivo, Transferencia, Tarjeta, Otro
- El método de pago es obligatorio
- Se guarda junto con el registro del pago
- Se puede ver en el historial de pagos

#### Story 5.1.5: Como vendedor independiente quiero ver el saldo restante después de un pago parcial para saber cuánto falta por cobrar

**Criterios de Aceptación:**
- Después de registrar un abono se muestra el saldo restante
- El saldo se calcula como: Total venta - Suma de pagos
- Se muestra en el detalle de la venta
- Se actualiza automáticamente con cada pago
- Se muestra con formato de moneda

---

### Feature 5.2: Control de Cuentas por Cobrar

#### Story 5.2.1: Como vendedor independiente quiero ver una lista de todas las ventas pendientes de pago para saber a quién debo cobrar

**Criterios de Aceptación:**
- Existe sección "Cuentas por cobrar" o "Ventas pendientes"
- Se muestran solo ventas con estado "Pendiente"
- Cada venta muestra: cliente, fecha, total, saldo pendiente
- Se puede acceder al detalle de cada venta
- Se muestra cantidad total de ventas pendientes
- Si no hay pendientes, se muestra mensaje indicándolo

#### Story 5.2.2: Como vendedor independiente quiero ver el total de dinero pendiente por cobrar para conocer mi capital inmovilizado

**Criterios de Aceptación:**
- Se calcula sumando todos los saldos pendientes
- Se muestra destacadamente en la pantalla de cuentas por cobrar
- Se actualiza automáticamente al registrar pagos
- Se muestra con formato de moneda
- Opcionalmente se muestra en el dashboard principal

#### Story 5.2.3: Como vendedor independiente quiero ver las ventas pendientes ordenadas por antigüedad para priorizar cobros más antiguos

**Criterios de Aceptación:**
- Se puede ordenar por fecha de venta (más antigua primero)
- Se resaltan ventas con más de 30 días de antigüedad
- Se muestra la cantidad de días transcurridos desde la venta
- El ordenamiento se puede cambiar

#### Story 5.2.4: Como vendedor independiente quiero ver los clientes con más deuda acumulada para hacer seguimiento especial

**Criterios de Aceptación:**
- Se muestra lista de clientes con saldo pendiente
- Se ordena por monto de deuda (mayor a menor)
- Se muestra total adeudado por cliente
- Se puede acceder al detalle del cliente
- Se resaltan clientes con deuda > umbral definido

---

### Feature 5.3: Historial de Pagos

#### Story 5.3.1: Como vendedor independiente quiero ver el historial de pagos de una venta para verificar abonos realizados

**Criterios de Aceptación:**
- En el detalle de venta se muestra sección "Historial de pagos"
- Cada pago muestra: fecha, monto, método de pago
- Los pagos se ordenan cronológicamente
- Se muestra suma total de pagos recibidos
- Se muestra saldo pendiente si aplica

#### Story 5.3.2: Como vendedor independiente quiero ver el historial de todos los pagos recibidos para llevar control de ingresos

**Criterios de Aceptación:**
- Existe sección "Historial de pagos" general
- Se muestran todos los pagos recibidos
- Cada pago muestra: fecha, cliente, monto, método, venta asociada
- Se ordenan por fecha (más recientes primero)
- Se muestra total de pagos recibidos
- Se puede acceder a la venta asociada

#### Story 5.3.3: Como vendedor independiente quiero filtrar pagos por fecha para analizar cobros en períodos específicos

**Criterios de Aceptación:**
- Existe filtro de rango de fechas
- Se pueden usar atajos: "Hoy", "Esta semana", "Este mes"
- Los resultados se actualizan al aplicar filtro
- Se muestra total cobrado en el período
- Se puede exportar el reporte (futuro)

---

## EPIC 6: Reportes y Análisis

### Feature 6.1: Reporte de Inversión

#### Story 6.1.1: Como vendedor independiente quiero ver el total invertido en productos para saber cuánto dinero tengo comprometido

**Criterios de Aceptación:**
- Se calcula sumando (Costo compra × Cantidad en stock) de todos los productos
- Se muestra en formato de moneda
- Se actualiza automáticamente al cambiar stock o costos
- Se muestra en dashboard o sección de reportes
- Se incluye fecha de última actualización

#### Story 6.1.2: Como vendedor independiente quiero ver la inversión total por producto para identificar dónde tengo más capital invertido

**Criterios de Aceptación:**
- Se muestra tabla de productos ordenados por inversión
- Cada producto muestra: nombre, cantidad, costo unitario, inversión total
- La inversión total se calcula: Costo × Cantidad
- Se puede exportar el reporte
- Se muestran los top 10 productos con mayor inversión

#### Story 6.1.3: Como vendedor independiente quiero ver la inversión por período de tiempo para analizar tendencias de compra

**Criterios de Aceptación:**
- Se puede seleccionar rango de fechas
- Se calcula inversión basada en productos agregados en ese período
- Se muestra gráfico de inversión en el tiempo
- Se compara con períodos anteriores
- Se puede cambiar la granularidad (diario, semanal, mensual)

---

### Feature 6.2: Reporte de Ventas

#### Story 6.2.1: Como vendedor independiente quiero ver el total de ventas realizadas para conocer mi volumen de negocio

**Criterios de Aceptación:**
- Se muestra cantidad total de ventas realizadas
- Se muestra monto total vendido (suma de todas las ventas)
- Se distingue entre ventas pagadas y pendientes
- Se muestra ticket promedio (total ÷ cantidad ventas)
- Se actualiza en tiempo real

#### Story 6.2.2: Como vendedor independiente quiero ver ventas por período (día, semana, mes) para identificar mis mejores períodos

**Criterios de Aceptación:**
- Se puede seleccionar período: día, semana, mes, año
- Se muestra gráfico de ventas en el tiempo
- Se compara con período anterior (% cambio)
- Se identifican picos de venta
- Se puede exportar el reporte

#### Story 6.2.3: Como vendedor independiente quiero ver los productos más vendidos para saber qué artículos tienen más demanda

**Criterios de Aceptación:**
- Se muestra ranking de productos por cantidad vendida
- Cada producto muestra: nombre, unidades vendidas, ingresos generados
- Se puede filtrar por período de tiempo
- Se muestran top 10 o 20 productos
- Se muestra gráfico visual (barras o pastel)

#### Story 6.2.4: Como vendedor independiente quiero ver mis mejores clientes por volumen de compra para identificar clientes VIP

**Criterios de Aceptación:**
- Se muestra ranking de clientes por monto total comprado
- Cada cliente muestra: nombre, cantidad de compras, monto total
- Se puede filtrar por período
- Se identifican top 10 clientes
- Se muestra contribución al total de ventas (%)

---

### Feature 6.3: Reporte de Ganancias

#### Story 6.3.1: Como vendedor independiente quiero ver mi ganancia total (solo de ventas pagadas) para saber cuánto he ganado realmente

**Criterios de Aceptación:**
- Se calculan solo ventas con estado "Pagada"
- Ganancia = Suma de (Precio venta - Costo compra) × Cantidad
- Se muestra en formato de moneda destacado
- Se excluyen ventas pendientes
- Se actualiza al marcar ventas como pagadas

#### Story 6.3.2: Como vendedor independiente quiero ver la ganancia potencial (incluyendo ventas pendientes) para proyectar mis ingresos

**Criterios de Aceptación:**
- Se incluyen todas las ventas (pagadas y pendientes)
- Se distingue claramente: ganancia real vs ganancia potencial
- Se muestra cuánto falta por cobrar
- Se calcula de la misma forma que ganancia real
- Ayuda a proyectar ingresos futuros

#### Story 6.3.3: Como vendedor independiente quiero ver el margen de ganancia promedio para evaluar la rentabilidad general de mi negocio

**Criterios de Aceptación:**
- Se calcula promedio de márgenes de todos los productos vendidos
- Se muestra en porcentaje
- Se puede filtrar por producto o categoría
- Se compara con períodos anteriores
- Se identifica si está por encima o debajo de meta

#### Story 6.3.4: Como vendedor independiente quiero comparar inversión vs. ganancias para ver el retorno de mi inversión

**Criterios de Aceptación:**
- Se muestra gráfico comparativo inversión vs ganancias
- Se calcula ROI (Return on Investment): (Ganancia ÷ Inversión) × 100
- Se muestra en formato de porcentaje
- Se puede ver por período de tiempo
- Se incluyen indicadores visuales de rendimiento

---

### Feature 6.4: Dashboard Principal

#### Story 6.4.1: Como vendedor independiente quiero ver un resumen ejecutivo al iniciar sesión para tener una visión general de mi negocio

**Criterios de Aceptación:**
- El dashboard se muestra al iniciar sesión
- Es la pantalla principal después del login
- Muestra información resumida más relevante
- Se actualiza en tiempo real
- Es visualmente clara y organizada

#### Story 6.4.2: Como vendedor independiente quiero ver indicadores clave (total vendido, por cobrar, ganancia) para monitorear la salud de mi negocio

**Criterios de Aceptación:**
- Se muestran tarjetas/widgets con KPIs principales:
  - Total vendido (mes actual)
  - Cuentas por cobrar
  - Ganancia real (mes actual)
  - Productos con stock bajo
  - Cantidad de clientes activos
- Cada indicador muestra comparación con mes anterior (% cambio)
- Los valores se actualizan automáticamente
- Se usan colores para indicar estado (verde/positivo, rojo/alerta)

#### Story 6.4.3: Como vendedor independiente quiero ver gráficos de ventas en el tiempo para visualizar tendencias fácilmente

**Criterios de Aceptación:**
- Se muestra gráfico de línea de ventas (últimos 30 días)
- Se puede cambiar a vista semanal o mensual
- El gráfico es interactivo (mostrar valores al pasar el cursor)
- Se muestra tendencia (creciente/decreciente)
- Opcionalmente se muestra gráfico de productos más vendidos

---

## EPIC 7: Configuración y Administración

### Feature 7.1: Configuración General

#### Story 7.1.1: Como vendedor independiente quiero configurar el nombre de mi negocio para personalizar la aplicación

**Criterios de Aceptación:**
- Existe sección "Configuración" en el menú
- Se puede ingresar/editar nombre del negocio
- El nombre se muestra en el dashboard y reportes
- Los cambios se guardan inmediatamente
- Es opcional (puede dejarse vacío)

#### Story 7.1.2: Como vendedor independiente quiero seleccionar mi moneda preferida para ver todos los montos en mi divisa local

**Criterios de Aceptación:**
- Se muestra selector de moneda en configuración
- Opciones mínimas: USD, MXN, EUR, COP, ARS, CLP, etc.
- Al cambiar, todos los montos se muestran con el símbolo correspondiente
- Por defecto se establece según ubicación del usuario
- El cambio se aplica inmediatamente en toda la app

#### Story 7.1.3: Como vendedor independiente quiero configurar categorías de productos personalizadas para organizar mejor mi catálogo

**Criterios de Aceptación:**
- Se pueden crear categorías personalizadas
- Se pueden editar y eliminar categorías
- No se permite eliminar categorías con productos asociados
- Las categorías aparecen en el selector al crear/editar productos
- Se pueden asignar colores a las categorías (opcional)

---

### Feature 7.2: Respaldo de Datos

#### Story 7.2.1: Como vendedor independiente quiero que mis datos se guarden automáticamente para no perder información

**Criterios de Aceptación:**
- Todos los cambios se guardan automáticamente en la base de datos
- No se requiere acción manual del usuario
- Se muestra indicador de "guardando..." cuando hay cambios
- Los datos persisten aunque se cierre el navegador
- Se implementa sistema de respaldo automático diario

#### Story 7.2.2: Como vendedor independiente quiero exportar mis datos a Excel o CSV para tener un respaldo externo

**Criterios de Aceptación:**
- Existe opción "Exportar datos" en configuración
- Se puede exportar: productos, clientes, ventas, pagos
- El formato es CSV o Excel (.xlsx)
- El archivo se descarga automáticamente
- Los datos exportados están completos y bien formateados
- Se incluye fecha de exportación en el nombre del archivo

---

*Documento generado para el proyecto Mobile MiVenta*  
*Fecha: Enero 2026*