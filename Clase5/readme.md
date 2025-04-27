
# 📚 Clase 5 - Patrones de Diseño GOF

## 🎯 Objetivo de la clase
- Comprender el propósito de los patrones GOF.
- Identificar su clasificación: Creacionales, Estructurales y de Comportamiento.

## 🧠 ¿Qué es un Patrón de Diseño?
Un **patrón de diseño** es una solución **reutilizable** y **probada** para resolver problemas comunes en el diseño de software orientado a objetos.

> "Un patrón no es el código que escribes, es la forma en que piensas al escribirlo."

## 👥 ¿Quiénes son los GOF (Gang of Four)?
Autores del libro **"Design Patterns: Elements of Reusable Object-Oriented Software" (1994)**:
- Erich Gamma
- Richard Helm
- Ralph Johnson
- John Vlissides

Este libro **revolucionó** la forma de diseñar software orientado a objetos.

## 🧩 Clasificación de Patrones GOF
| Tipo            | ¿Qué resuelven?                                       | Ejemplos           |
|-----------------|--------------------------------------------------------|--------------------|
| **Creacionales** | Formas de crear objetos flexiblemente                  | Singleton, Prototype |
| **Estructurales** | Componer clases/objetos en estructuras más complejas | Adapter, Bridge |
| **Comportamiento** | Controlar flujos de trabajo o comunicación            | Observer, Strategy |

## 🏰 Patrón Singleton
### 🔥 ¿Qué problema resuelve?
- Asegura que una clase tenga **una única instancia** en todo el sistema.
- Proporciona un **punto de acceso global**.

### 🛠️ ¿Cuándo usarlo?
- Configuración global de la aplicación.
- Acceso centralizado a recursos (logs, base de datos).
- Control de acceso o autenticación.

### ❌ ¿Qué pasa si no se usa?
- Instancias duplicadas innecesarias.
- Inconsistencias en datos compartidos.

## 📈 Lazy vs Eager Instantiation
**Lazy (perezosa):**
- Se crea la instancia **solo si se necesita**.
- Ahorra memoria.
- Puede no ser seguro en entornos multihilo.

```java
if (instancia == null) {
    instancia = new Singleton();
}
```

**Eager (ansiosa):**
- La instancia se crea **al cargar la clase**.
- Más segura en entornos multihilo.
- Puede desperdiciar memoria si no se usa.

```java
private static final Singleton instancia = new Singleton();
```

| Tipo  | Ventajas | Desventajas |
|------|----------|-------------|
| Lazy | Ahorro de memoria, sólo si se usa | Riesgo multihilo |
| Eager | Seguro multihilo | Uso de memoria innecesario |

## 💻 Ejemplo de Código Java (Lazy Singleton)
```java
public class Singleton {
    private static Singleton instancia;

    private Singleton() { }

    public static Singleton getInstancia() {
        if (instancia == null) {
            instancia = new Singleton();
        }
        return instancia;
    }
}
```

## 🐾 De UML a Código – Ejemplo Registro de Gatos
- Se aplica Singleton para tener un único registro centralizado de gatos en el sistema.
- Diseño sencillo para demostrar acceso controlado.

## ✍️ Resumen de la Clase
- Qué son los patrones de diseño.
- Quiénes son los GOF.
- Clasificación: Creacionales, Estructurales y de Comportamiento.
- Enfoque profundo en Singleton: UML, código y ejemplo realista.

## 🎬 Actividad Evaluativa (Video)
### Instrucciones:
1. Trabaja en pareja.
2. Elige uno de estos patrones:
   - Prototype (creacional)
   - Adapter (estructural)
   - Bridge (estructural)
3. Graba un video máximo 2 minutos 30 segundos donde expliques:
   - ¿Qué problema resuelve?
   - Diagrama UML explicado (a mano o digital).
   - Código Java funcional y explicado.
   - Caso de uso realista.
   - Ventajas y desventajas.
   - Recursos visuales de apoyo.

### Requisitos técnicos:
- Audio claro.
- Buena calidad visual (pantalla nítida).
- Formato recomendado: `.mp4`, `.mov`, `.avi`.
- Fecha de entrega: **Martes 30 de abril, 23:59**.
- Entrega por correo.

### Rúbrica:
| Criterio | Puntaje Máximo |
|---|---|
| Explicación del patrón | 2.0 pts |
| Diagrama UML explicado | 2.0 pts |
| Código Java funcional | 2.0 pts |
| Caso de uso realista | 1.0 pt |
| Claridad y síntesis | 1.0 pt |
| Calidad de video y audio | 1.0 pt |
| Uso de recursos visuales | 1.0 pt |

## 📢 Cierre
> "Quien enseña, aprende dos veces." – Joseph Joubert

> "Explicar algo bien es el mejor test de si lo entendiste."
