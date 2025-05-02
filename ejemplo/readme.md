
# 🪪 Generador de Credenciales de Evento

### Estudiante(s):  
- Giovanni Caceres – Patrones de Diseño (Sección X)

---

## 🎯 Objetivo del Proyecto

Este sistema permite emitir credenciales personalizadas para un evento, a partir de una plantilla clonable. Se aplican los patrones de diseño **Prototype** (para clonar credenciales) y **Singleton** (para configuración global del evento). (redactar el suyo)

---

## 🚀 Cómo ejecutar

1. Clonar el repositorio:
```bash
git clone https://github.com/usuario/repositorio.git
cd repositorio
```

2. Compilar y ejecutar:
```bash
javac DemoEvento.java
java DemoEvento
```

---

## 🧬 Patrón Prototype – Aplicación

- `Prototype` implementa `Cloneable`.
- Clonado

```java
Prototype clon = plantilla.clone();
clon.setNombre("Tulio");
```

---

## 🔒 Patrón Singleton – Aplicación

- `Singleton` contiene:
  - Atributo
- Se accede con `getInstancia()`:

```java
Singleton.getInstancia().atributo("atributo");
```

---

## 🖥️ Menú por consola

```
--- MENÚ ---
1. Agregar nueva credencial
2. Ver credenciales generadas
3. Salir
```

---

## 📊 Diagrama de Clases (UML)

![Diagrama de Clases UML](uml/diagrama_clases.png)

> (Incluir imagen del diagrama UML generado o escaneado)

---

## 📸 Captura del sistema funcionando

> Agregar una o más capturas de pantalla con credenciales personalizadas creadas por consola.
