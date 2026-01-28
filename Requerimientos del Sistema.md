# Proyecto Mobile MiVenta

## 1. CONTEXTO

Existe un segmento importante de emprendedores y vendedores independientes que compran productos para revenderlos con un margen de ganancia, pero no están formalizados como empresas. Estos vendedores necesitan controlar su inversión, calcular márgenes de ganancia, registrar ventas y hacer seguimiento a pagos de clientes.

Actualmente utilizan métodos manuales (cuadernos, hojas de cálculo) que son propensos a errores, pérdida de información y no les permiten tener una visión clara de la rentabilidad real de su negocio.

**Necesidad:** Una aplicación móvil nativa para Android simple y accesible que les permita gestionar productos, clientes, ventas y pagos de manera organizada y profesional desde sus smartphones.

## 2. PROBLEMA

### Planteamiento
Los vendedores independientes no cuentan con herramientas simples y accesibles para gestionar eficientemente su negocio de compra-venta.

### Consecuencias
- Pérdida de dinero por falta de control en cuentas por cobrar
- Desconocimiento de la rentabilidad real del negocio
- Dificultad para calcular precios de venta adecuados
- Tiempo perdido en gestión administrativa manual
- Conflictos con clientes por falta de registros claros

### Solución
Aplicación móvil nativa para Android que permita:
- Registrar productos con costo de compra y precio de venta
- Calcular automáticamente márgenes de ganancia
- Gestionar clientes y su historial
- Controlar ventas y estado de pagos
- Visualizar reportes básicos de inversión y ganancias
- Trabajar en modo offline con sincronización automática
- Compartir información de ventas por WhatsApp y otras apps

## 3. ACTORES

### 3.1 Vendedor Independiente (Usuario Principal)

**Descripción:** Emprendedor que compra y vende productos sin estar formalizado como empresa.

**Perfil:**
- Edad: 18-55 años
- Conocimientos técnicos básicos (usa smartphone, WhatsApp, redes sociales)
- Vende productos de cualquier categoría (ropa, cosméticos, tecnología, etc.)
- Trabaja frecuentemente con ventas a crédito

**Objetivos:**
- Llevar control ordenado de su negocio
- Saber cuánto está ganando realmente
- Recuperar dinero de ventas a crédito
- Tomar decisiones informadas sobre precios

**Funciones en el sistema:**
- Registrar y gestionar productos
- Calcular márgenes de ganancia
- Registrar clientes y ventas
- Controlar pagos y cuentas por cobrar
- Consultar reportes de inversión y ganancias

### 3.2 Cliente (Actor Indirecto)

**Descripción:** Persona que compra productos al vendedor, frecuentemente a crédito.

**Perfil:**
- Cliente recurrente o eventual
- Generalmente conocido del vendedor
- Paga en efectivo, transferencia o "fiado"

**Interacción con el sistema:**
- No usa el sistema directamente
- Sus compras y pagos son registrados por el vendedor
- Beneficia de registros exactos de sus deudas

### 3.3 Administrador del Sistema (Futuro - Opcional)

**Descripción:** Persona o equipo que mantiene y da soporte a la plataforma.

**Responsabilidades:**
- Soporte técnico a usuarios
- Mantenimiento del sistema
- Implementación de mejoras

---

## REQUERIMIENTOS DEL SISTEMA

### EPIC 1: Gestión de Autenticación y Usuarios

#### Feature 1.1: Autenticación con Google Sign-In
- **Story 1.1.1:** Como vendedor independiente quiero registrarme usando mi cuenta de Google para acceder rápidamente sin crear una contraseña
- **Story 1.1.2:** Como vendedor independiente quiero iniciar sesión con mi cuenta de Google para acceder de manera segura con un solo clic
- **Story 1.1.3:** Como vendedor independiente quiero que el sistema sincronice automáticamente mi nombre y email de Google para no tener que ingresarlos manualmente
- **Story 1.1.4:** Como vendedor independiente quiero ver qué cuenta de Google estoy usando para identificar mi sesión actual

#### Feature 1.2: Gestión de Sesión
- **Story 1.2.1:** Como vendedor independiente quiero mantener mi sesión activa mientras uso la app para no tener que autenticarme constantemente
- **Story 1.2.2:** Como vendedor independiente quiero cerrar sesión para proteger mi información cuando no esté usando la aplicación
- **Story 1.2.3:** Como vendedor independiente quiero que mi sesión sea segura y expire automáticamente después de un período de inactividad prolongado

#### Feature 1.3: Perfil de Usuario
- **Story 1.3.1:** Como vendedor independiente quiero ver mi información de perfil para verificar mis datos personales
- **Story 1.3.2:** Como vendedor independiente quiero editar mi información de perfil para mantener mis datos actualizados

---

### EPIC 2: Gestión de Productos

#### Feature 2.1: Catálogo de Productos
- **Story 2.1.1:** Como vendedor independiente quiero registrar un nuevo producto con nombre, descripción, costo de compra y precio de venta para tener un catálogo de mis productos
- **Story 2.1.2:** Como vendedor independiente quiero ver una lista de todos mis productos para conocer mi inventario actual
- **Story 2.1.3:** Como vendedor independiente quiero buscar productos por nombre o categoría para encontrarlos rápidamente
- **Story 2.1.4:** Como vendedor independiente quiero editar la información de un producto para actualizar precios o descripciones
- **Story 2.1.5:** Como vendedor independiente quiero eliminar un producto para mantener mi catálogo limpio de artículos que ya no vendo

#### Feature 2.2: Cálculo de Márgenes
- **Story 2.2.1:** Como vendedor independiente quiero ver el margen de ganancia calculado automáticamente (en dinero y porcentaje) para saber cuánto ganaré por cada producto
- **Story 2.2.2:** Como vendedor independiente quiero simular diferentes precios de venta para decidir el precio óptimo antes de vender
- **Story 2.2.3:** Como vendedor independiente quiero recibir una alerta si mi precio de venta es menor al costo de compra para evitar vender con pérdidas

#### Feature 2.3: Control de Inventario
- **Story 2.3.1:** Como vendedor independiente quiero registrar la cantidad disponible de cada producto para llevar control de mi stock
- **Story 2.3.2:** Como vendedor independiente quiero que el stock se actualice automáticamente al hacer una venta para tener inventario en tiempo real
- **Story 2.3.3:** Como vendedor independiente quiero ver productos con stock bajo para saber cuándo debo reabastecerme

---

### EPIC 3: Gestión de Clientes

#### Feature 3.1: Registro de Clientes
- **Story 3.1.1:** Como vendedor independiente quiero registrar un nuevo cliente con nombre, teléfono y dirección para tener un directorio de mis compradores
- **Story 3.1.2:** Como vendedor independiente quiero ver una lista de todos mis clientes para acceder rápidamente a su información
- **Story 3.1.3:** Como vendedor independiente quiero buscar clientes por nombre o teléfono para encontrarlos fácilmente
- **Story 3.1.4:** Como vendedor independiente quiero editar la información de un cliente para mantener sus datos actualizados
- **Story 3.1.5:** Como vendedor independiente quiero eliminar un cliente para limpiar mi base de datos de contactos inactivos

#### Feature 3.2: Historial de Clientes
- **Story 3.2.1:** Como vendedor independiente quiero ver el historial de compras de un cliente para conocer su comportamiento de compra
- **Story 3.2.2:** Como vendedor independiente quiero ver el saldo pendiente de cada cliente para saber quién me debe dinero
- **Story 3.2.3:** Como vendedor independiente quiero ver la fecha de la última compra de un cliente para identificar clientes activos e inactivos

---

### EPIC 4: Gestión de Ventas

#### Feature 4.1: Registro de Ventas
- **Story 4.1.1:** Como vendedor independiente quiero crear una nueva venta seleccionando un cliente para asociar la transacción al comprador correcto
- **Story 4.1.2:** Como vendedor independiente quiero agregar múltiples productos a una venta con sus cantidades para registrar ventas de varios artículos
- **Story 4.1.3:** Como vendedor independiente quiero ver el total de la venta calculado automáticamente para saber el monto exacto a cobrar
- **Story 4.1.4:** Como vendedor independiente quiero registrar la fecha de la venta para llevar un historial cronológico
- **Story 4.1.5:** Como vendedor independiente quiero guardar una venta para mantener el registro en el sistema

#### Feature 4.2: Listado y Consulta de Ventas
- **Story 4.2.1:** Como vendedor independiente quiero ver una lista de todas mis ventas para tener un historial completo
- **Story 4.2.2:** Como vendedor independiente quiero filtrar ventas por fecha para analizar períodos específicos
- **Story 4.2.3:** Como vendedor independiente quiero filtrar ventas por cliente para ver el historial de un comprador específico
- **Story 4.2.4:** Como vendedor independiente quiero ver los detalles completos de una venta para revisar los productos vendidos y montos
- **Story 4.2.5:** Como vendedor independiente quiero editar una venta para corregir errores en el registro

---

### EPIC 5: Gestión de Pagos

#### Feature 5.1: Registro de Pagos
- **Story 5.1.1:** Como vendedor independiente quiero marcar una venta como "Pagada" o "Pendiente" para saber su estado de cobro
- **Story 5.1.2:** Como vendedor independiente quiero registrar un pago completo de una venta para actualizar el estado a pagado
- **Story 5.1.3:** Como vendedor independiente quiero registrar un pago parcial (abono) a una venta para llevar control de deudas que se pagan en cuotas
- **Story 5.1.4:** Como vendedor independiente quiero seleccionar el método de pago (efectivo, transferencia, etc.) para llevar registro de cómo cobré
- **Story 5.1.5:** Como vendedor independiente quiero ver el saldo restante después de un pago parcial para saber cuánto falta por cobrar

#### Feature 5.2: Control de Cuentas por Cobrar
- **Story 5.2.1:** Como vendedor independiente quiero ver una lista de todas las ventas pendientes de pago para saber a quién debo cobrar
- **Story 5.2.2:** Como vendedor independiente quiero ver el total de dinero pendiente por cobrar para conocer mi capital inmovilizado
- **Story 5.2.3:** Como vendedor independiente quiero ver las ventas pendientes ordenadas por antigüedad para priorizar cobros más antiguos
- **Story 5.2.4:** Como vendedor independiente quiero ver los clientes con más deuda acumulada para hacer seguimiento especial

#### Feature 5.3: Historial de Pagos
- **Story 5.3.1:** Como vendedor independiente quiero ver el historial de pagos de una venta para verificar abonos realizados
- **Story 5.3.2:** Como vendedor independiente quiero ver el historial de todos los pagos recibidos para llevar control de ingresos
- **Story 5.3.3:** Como vendedor independiente quiero filtrar pagos por fecha para analizar cobros en períodos específicos

---

### EPIC 6: Reportes y Análisis

#### Feature 6.1: Reporte de Inversión
- **Story 6.1.1:** Como vendedor independiente quiero ver el total invertido en productos para saber cuánto dinero tengo comprometido
- **Story 6.1.2:** Como vendedor independiente quiero ver la inversión total por producto para identificar dónde tengo más capital invertido
- **Story 6.1.3:** Como vendedor independiente quiero ver la inversión por período de tiempo para analizar tendencias de compra

#### Feature 6.2: Reporte de Ventas
- **Story 6.2.1:** Como vendedor independiente quiero ver el total de ventas realizadas para conocer mi volumen de negocio
- **Story 6.2.2:** Como vendedor independiente quiero ver ventas por período (día, semana, mes) para identificar mis mejores períodos
- **Story 6.2.3:** Como vendedor independiente quiero ver los productos más vendidos para saber qué artículos tienen más demanda
- **Story 6.2.4:** Como vendedor independiente quiero ver mis mejores clientes por volumen de compra para identificar clientes VIP

#### Feature 6.3: Reporte de Ganancias
- **Story 6.3.1:** Como vendedor independiente quiero ver mi ganancia total (solo de ventas pagadas) para saber cuánto he ganado realmente
- **Story 6.3.2:** Como vendedor independiente quiero ver la ganancia potencial (incluyendo ventas pendientes) para proyectar mis ingresos
- **Story 6.3.3:** Como vendedor independiente quiero ver el margen de ganancia promedio para evaluar la rentabilidad general de mi negocio
- **Story 6.3.4:** Como vendedor independiente quiero comparar inversión vs. ganancias para ver el retorno de mi inversión

#### Feature 6.4: Dashboard Principal
- **Story 6.4.1:** Como vendedor independiente quiero ver un resumen ejecutivo al iniciar sesión para tener una visión general de mi negocio
- **Story 6.4.2:** Como vendedor independiente quiero ver indicadores clave (total vendido, por cobrar, ganancia) para monitorear la salud de mi negocio
- **Story 6.4.3:** Como vendedor independiente quiero ver gráficos de ventas en el tiempo para visualizar tendencias fácilmente

---

### EPIC 7: Configuración y Administración

#### Feature 7.1: Configuración General
- **Story 7.1.1:** Como vendedor independiente quiero configurar el nombre de mi negocio para personalizar la aplicación
- **Story 7.1.2:** Como vendedor independiente quiero seleccionar mi moneda preferida para ver todos los montos en mi divisa local
- **Story 7.1.3:** Como vendedor independiente quiero configurar categorías de productos personalizadas para organizar mejor mi catálogo

#### Feature 7.2: Respaldo de Datos
- **Story 7.2.1:** Como vendedor independiente quiero que mis datos se guarden automáticamente para no perder información
- **Story 7.2.2:** Como vendedor independiente quiero exportar mis datos a Excel o CSV para tener un respaldo externo

---

### EPIC 8: Funcionalidades Específicas Android

#### Feature 8.1: Integración con Aplicaciones
- **Story 8.1.1:** Como vendedor independiente quiero compartir detalles de venta por WhatsApp para enviar resumen al cliente
- **Story 8.1.2:** Como vendedor independiente quiero llamar a un cliente desde la app para contactarlo rápidamente
- **Story 8.1.3:** Como vendedor independiente quiero compartir reportes por email o apps de mensajería para tener respaldo externo

#### Feature 8.2: Modo Offline
- **Story 8.2.1:** Como vendedor independiente quiero trabajar sin conexión a internet para no depender de la red
- **Story 8.2.2:** Como vendedor independiente quiero que mis datos se sincronicen automáticamente cuando recupere conexión para mantener información actualizada
- **Story 8.2.3:** Como vendedor independiente quiero ver el estado de sincronización para saber si mis datos están actualizados

#### Feature 8.3: Notificaciones
- **Story 8.3.1:** Como vendedor independiente quiero recibir notificaciones de pagos pendientes para recordar cobrar a mis clientes
- **Story 8.3.2:** Como vendedor independiente quiero recibir alertas de productos con stock bajo para saber cuándo reabastecer
- **Story 8.3.3:** Como vendedor independiente quiero configurar recordatorios personalizados para hacer seguimiento a clientes

#### Feature 8.4: Funcionalidades del Dispositivo
- **Story 8.4.1:** Como vendedor independiente quiero tomar fotos de productos desde la app para tener registro visual
- **Story 8.4.2:** Como vendedor independiente quiero escanear códigos de barras para agregar productos rápidamente
- **Story 8.4.3:** Como vendedor independiente quiero importar clientes desde mis contactos del teléfono para agilizar el registro