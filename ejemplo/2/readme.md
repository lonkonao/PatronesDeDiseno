# Sistema de Gestión de Insumos Médicos

## ✅ Descripción General del Sistema
Este proyecto corresponde al modelado completo de un **Sistema de Gestión de Insumos Médicos**, enfocado en asegurar la trazabilidad, integridad y control de dispositivos médicos, desde su recepción hasta el egreso, en cumplimiento de la **Norma Técnica N° 226 del MINSAL**.

El sistema considera aspectos operacionales críticos en un entorno hospitalario, incluyendo:
- Registro y gestión de movimientos de insumos por lote, fecha de vencimiento y unidad.
- Control de stock con alertas preventivas.
- Configuración flexible y centralizada de parámetros operativos.
- Integración con sistemas externos (ERP).
- Accesos diferenciados y escalabilidad multi-bodega.

---

## 🔍 Objetivos del Modelado
- Desarrollar una transición completa desde la visión funcional hasta el despliegue físico.
- Aplicar patrones de diseño en el diseño lógico y reflejarlos en la arquitectura de implementación.
- Ejercitar el pensamiento arquitectónico en la separación de responsabilidades, modularidad y escalabilidad.

---

## 🔹 1. Diagrama de Casos de Uso UML
![image](https://github.com/user-attachments/assets/0d7847bb-b6b0-468a-aecc-8855e2240684)



### Descripción general
El análisis funcional permitió identificar con claridad los actores involucrados y las funcionalidades críticas del sistema. Además, se aplicaron correctamente **relaciones de `<<include>>` y `<<extend>>`** para reflejar flujos obligatorios y opcionales en el proceso.

#### Actores identificados:
- **Bodeguero**: Responsable de operaciones de ingreso y egreso de insumos, consulta de stock.
- **Supervisor Médico**: Consulta stock, visualiza trazabilidad, genera reportes de alertas.
- **Administrador del Sistema**: Configura el sistema, gestiona usuarios, integra con ERP, realiza auditorías.
- **Auditor Externo**: Revisa auditoría de movimientos, accede a reportes de trazabilidad.
- **Sistema ERP Hospitalario**: Actor externo con el que se sincronizan datos críticos.

#### Casos de uso destacados y relaciones aplicadas:
- **Ingreso de Insumos con Código de Barras**
  - `<<extend>>` **Alertas Automáticas por Stock Bajo o Vencimiento Próximo**: al ingresar insumos, puede opcionalmente activarse una alerta.
- **Egreso Controlado de Insumos**
  - `<<extend>>` **Alertas Automáticas por Stock Bajo o Vencimiento Próximo**: al egresar insumos, podría dispararse una alerta opcional.
  - `<<extend>>` **Generación de Reportes de Movimientos**: se puede generar el reporte posterior al egreso como acción opcional.
- **Consulta Detallada de Stock por Bodega y Lote**
  - `<<extend>>` **Generación de Reportes de Alertas**: opcionalmente, tras consultar stock, se puede emitir un reporte.
- **Auditoría de Movimientos y Trazabilidad**
  - `<<include>>` **Generación de Reportes de Movimientos**: la generación de reportes es siempre parte del proceso de auditoría.
- **Integración con Sistema ERP Hospitalario**
  - Comunicación obligatoria con el actor **Sistema ERP Hospitalario** para sincronización.

#### Justificación de las relaciones aplicadas:
- Se utilizaron `<<include>>` en procesos donde el caso de uso base **siempre depende de otro caso obligatorio**, como en la **Auditoría de Movimientos y Trazabilidad**, que necesariamente genera un reporte.
- Se aplicaron `<<extend>>` en procesos donde las acciones son **condicionadas o opcionales**, como la **generación de reportes tras egresos** o la **activación de alertas al ingresar o egresar insumos**.
- Se reforzó la modularidad y claridad de los flujos mediante estas relaciones, cumpliendo con el nivel de detalle exigido en entornos profesionales.

#### Relación destacada:
El sistema se comunica con el **Sistema ERP Hospitalario** para sincronizar datos de movimientos, egresos e ingresos, garantizando integridad y trazabilidad en la cadena logística institucional.


## 🔹 2. Diagrama de Clases UML con Patrones Aplicados
![image](https://github.com/user-attachments/assets/ef4a83da-4246-44e8-9b8a-0de62471b0a7)


## 🧩 Justificación Arquitectónica y Patrones Aplicados

### Selección de patrones
La elección de los patrones de diseño no fue arbitraria, sino estratégica y alineada a las necesidades específicas del sistema y sus desafíos técnicos:

### **1. Singleton (`ConfiguracionSistema`)**
#### Justificación:
Se seleccionó Singleton para la **gestión centralizada de parámetros críticos del sistema**, como tiempos de vencimiento, stock mínimo, tipos de alerta, entre otros.  
Este patrón permite garantizar que **exista una única instancia accesible globalmente**, evitando inconsistencias y facilitando la administración de la configuración desde cualquier módulo del sistema.

#### Intención arquitectónica:
- Centralizar el control de la configuración.
- Facilitar la escalabilidad futura permitiendo la consulta distribuida.
- Evitar múltiples puntos de configuración que pudieran provocar errores operacionales.

---

### **2. Prototype (`PlantillaMovimiento`)**
#### Justificación:
La operación hospitalaria exige rapidez y eficiencia en la gestión de movimientos repetitivos.  
Se implementó Prototype para **permitir la clonación de plantillas de movimientos frecuentes**, como egresos de insumos comunes o ingresos masivos programados, permitiendo a los operadores agilizar las operaciones sin recrear movimientos desde cero.

#### Intención arquitectónica:
- Reducir la complejidad y tiempo de operaciones manuales.
- Permitir la creación rápida de nuevas instancias de movimientos desde plantillas base, manteniendo flexibilidad y control.
- Facilitar la parametrización de campañas o protocolos especiales (ej.: vacunación masiva).

---

### **3. Adapter (`AdaptadorERP`)**
#### Justificación:
Dado que el sistema debe integrarse con el ERP hospitalario, el uso de Adapter fue clave para **desacoplar el núcleo del sistema de la API del ERP externo**, permitiendo mantener la flexibilidad en caso de cambios o actualizaciones en el sistema ERP.

#### Intención arquitectónica:
- Asegurar la independencia tecnológica del sistema interno.
- Facilitar el mantenimiento y evolución del sistema de integración.
- Permitir la adaptación a distintos sistemas externos (ERP, contabilidad, etc.) sin impactar el dominio.

---

### **4. Bridge (`InterfazUsuario` + `VistaBodeguero`, `VistaSupervisor`)**
#### Justificación:
Considerando la diversidad de usuarios y dispositivos (bodeguero móvil, supervisor en escritorio, etc.), se aplicó Bridge para **separar la interfaz de usuario de la lógica de negocio**, permitiendo adaptar la experiencia según el perfil del usuario y el dispositivo utilizado, sin afectar la lógica central del sistema.

#### Intención arquitectónica:
- Flexibilizar las vistas según necesidades operativas.
- Garantizar independencia entre interfaz y lógica.
- Facilitar futuras integraciones con nuevas plataformas (app, web, terminal de autoservicio).

---

## 🔹 3. Diagrama de Implementación UML
![image](https://github.com/user-attachments/assets/e78fb473-d493-4c4a-b916-c470f34e63e7)


### Despliegue Físico y decisiones técnicas:
- **Nodos físicos diferenciados** para reforzar seguridad, escalabilidad y disponibilidad.
- Separación clara de responsabilidades entre servidores de aplicaciones, configuración, integración ERP, y bases de datos.
- Uso de protocolos estándar (REST, SOAP) en las integraciones externas.
- Aislamiento de componentes críticos (como `ConfiguracionSistema`) en nodos dedicados para reforzar el control de cambios y configuración.

---

## 🧩 Reflexiones Finales del Modelado

Este ejercicio refleja una aproximación arquitectónica profesional donde:
- Cada patrón fue seleccionado según necesidades específicas y no como elemento decorativo.
- La transición entre **caso de uso ➡ diagrama de clases ➡ implementación** permitió mantener una trazabilidad clara desde el negocio hasta la infraestructura.
- La modularización y aplicación de patrones permitieron diseñar un sistema robusto, flexible, mantenible y alineado a buenas prácticas de ingeniería de software.

Este repositorio tiene como propósito servir de **referencia formal para futuros trabajos de modelado arquitectónico**, mostrando estándares exigidos en entornos profesionales.

---

## ⚠️ Nota
Este repositorio es exclusivamente documental.  
No se incluye código fuente, ya que el foco es el modelado arquitectónico.

