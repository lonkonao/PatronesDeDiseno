# 🧩 Patrón de Diseño: **Iterator**

## 📘 ¿Qué aprenderás?
- Qué es el patrón de diseño **Iterator**
- Sus componentes y estructura en **UML**
- Cuándo y por qué usarlo en desarrollo de software

---

## 🧺 ¿Colección, lista o array?
- **Colección:** Grupo general de elementos (ej: lista, conjunto, cola)
- **Lista:** Colección ordenada que permite duplicados (ej: `ArrayList`)
- **Array:** Tamaño fijo, no tiene métodos de colección

---

## 🔁 ¿Qué es el patrón **Iterator**?
- Es un **patrón de comportamiento** (GoF)
- Permite **recorrer elementos** de una colección
- Sin exponer su implementación interna
- Separa **estructura** y **recorrido**

---

## 🧱 Estructura del patrón

- `Iterator`: define `hasNext()` y `next()`
- `ConcreteIterator`: implementación del recorrido
- `Aggregate`: interfaz para crear el iterador
- `ConcreteAggregate`: colección que entrega el iterador

---

## 📊 Diagrama UML

![image](https://github.com/user-attachments/assets/5ce9a432-4ac3-4c2e-9406-8c920584375e)


---

## ❓¿Por qué usar Iterator?
- No todas las colecciones tienen orden o posición
- A veces los datos vienen de fuentes desconocidas (API, archivo)
- Queremos recorrer **sin importar la estructura**
- El `for-each` no siempre es suficiente

---

## ✅ Usos ideales
- Listas, conjuntos, colas, pilas
- Árboles, colecciones personalizadas
- Recorridos secuenciales simples

## ❌ No recomendable para
- Recorridos aleatorios
- Modificar elementos mientras se recorren
- Estructuras altamente dinámicas como grafos densos

---

## 🧠 Ventajas
- **Desacopla** el recorrido de la estructura
- Funciona en múltiples tipos de colección
- Permite recorridos personalizados
- Mejora legibilidad y mantenimiento
- Ya está integrado en muchos lenguajes

---

## 🎥 Actividad: Explica Iterator en 1 Minuto

### 🎯 Objetivo:
Explicar claramente qué hace el patrón **sin tecnicismos**, en un video de **máx. 60 segundos**.

### 🎥 Requisitos:
- Sin usar términos como: clase, método, código, objeto, interfaz, for, lista, etc.
- Puede grabarse con:
  - Cámara personal
  - Avatar
  - Dibujos / objetos físicos
- Audio debe ser claro
- Entrega:  
  📧 **gcaceres6@santotomas.cl**  
  📌 Asunto: `Iterator - [Nombre completo]`  
  🗓️ **Plazo: 19-06-2025 a las 23:59**

---

## 📝 Rúbrica de Evaluación

| Criterio                                  | Puntos  | Descripción |
|-------------------------------------------|---------|-------------|
| Explicación clara                         | +1.0    | Fácil de entender |
| Sin lenguaje técnico                      | +0.5    | No usa palabras técnicas |
| Uso creativo del ejemplo                  | +0.5    | Buena comparación o metáfora |
| Presentación general (tono, intención)    | +1.0    | Se nota interés |

---

## ❌ Descuentos

| Infracción                                       | Penalización |
|--------------------------------------------------|--------------|
| +60 segundos                                     | −0.1 por segundo extra |
| 1–2 tecnicismos leves                            | −1.0 |
| Repetición de tecnicismos                       | −2.0 |
| Audio con ruido constante o inaudible            | −1.0 |
| Entrega incorrecta (solo audio, sin esfuerzo)    | −2.0 |
| Video genérico que no explica el patrón          | −3.0 |
| Entrega fuera de plazo (si se acepta igual)      | −2.0 |


[clase9.pdf](https://github.com/user-attachments/files/20746379/clase9.pdf)
