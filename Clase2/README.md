# Caso Práctico: Sistema de Gestión de Bodega de Insumos Médicos

## Contexto
Una empresa de distribución de insumos médicos cuenta con una **bodega central** y **dos sucursales**.  
La bodega es responsable de recibir productos de distintos **proveedores**, almacenarlos y distribuirlos a las **sucursales** según su demanda.  

Cada sucursal puede **solicitar productos** a la bodega central cuando su **stock está bajo**, y la bodega debe gestionar los envíos.  
Además, la empresa necesita un **control detallado del inventario** en cada ubicación y **registrar las ventas** de las sucursales.  

---

## Problemática
Actualmente, la empresa **no cuenta con un sistema automatizado** para la gestión de inventarios y pedidos.  
Esto genera problemas como:  

- **Falta de control sobre el stock** en la bodega y sucursales.  
- **Retrasos en la reposición** de productos en las sucursales.  
- **Errores en la distribución** de insumos médicos.  
- **Poca visibilidad** sobre las ventas y movimientos de productos.  

---

## Lo que hay que hacer  
Se requiere diseñar un **sistema de gestión** de la bodega y las sucursales, modelando los siguientes **diagramas UML**:  

### 1️⃣ Diagrama de Clases  
- Definir clases como **BodegaCentral, Sucursal, Producto, Pedido, Proveedor, Venta**.  
- Establecer **relaciones** entre ellas (**asociaciones, agregaciones o composiciones**).  

### 2️⃣ Diagrama de Casos de Uso  
- Identificar los **actores principales**:  
  - **Administrador de Bodega**  
  - **Jefe de Sucursal**  
- Modelar los casos de uso:  
  - **Solicitar insumos**  
  - **Registrar ingreso de productos**  
  - **Registrar venta**  
  - **Actualizar stock**  

### 3️⃣ Diagrama de Secuencia  
- Representar el flujo de una **solicitud de reposición** de una sucursal a la bodega central, incluyendo:  
  - **Validaciones de stock**  
  - **Confirmación del pedido**  

---

