
# 📚 Unidad 2: Patrones de Diseño

### Fecha: 02-05-2025

---

## ✅ Contenidos abordados en clase

### 🔁 Patrón Singleton (Repaso)
- Vimos cómo garantizar que una clase tenga **una única instancia global**.
- Ejemplo en Java con `ContadorGlobal`.

```java
class ContadorGlobal {
    private static ContadorGlobal instancia;
    private int contador = 0;

    private ContadorGlobal() {
        System.out.println("Contador iniciado");
    }

    public static ContadorGlobal getInstancia() {
        if (instancia == null) {
            instancia = new ContadorGlobal();
        }
        return instancia;
    }

    public void incrementar() {
        contador++;
    }

    public int obtenerValor() {
        return contador;
    }
}

public class DemoSingleton {
    public static void main(String[] args) {
        ContadorGlobal a = ContadorGlobal.getInstancia();
        a.incrementar();
        a.incrementar();

        ContadorGlobal b = ContadorGlobal.getInstancia();
        b.incrementar();
        b.incrementar();
        b.incrementar();
        b.incrementar();

        System.out.println("Valor final: " + b.obtenerValor());

        if (a == b) {
            System.out.println("✅ Mismo objeto compartido (Singleton)");
        } else {
            System.out.println("❌ Diferentes instancias (NO Singleton)");
        }
    }
}

```
- Si queremos romperlo solo debemos cambiar la visibilidad a `private ContadorGlobal()`
- Luego cambiar `ContadorGlobal.getInstancia();` por `new ContadorGlobal();` 

### 🧬 Patrón Prototype
- Se explicó cómo **clonar objetos** sin usar `new`.
- Analizamos diferencias entre:
  - `Shallow Copy` (copia superficial, comparte referencias)
  - `Deep Copy` (copia independiente)
- Ejemplo práctico: clase `Caja` clonando listas.

```java
import java.util.ArrayList;
import java.util.List;

class Caja implements Cloneable {
    public List<String> elementos = new ArrayList<>();

    public void agregar(String item) {
        elementos.add(item);
    }

    @Override
    public Caja clone() {
        try {
            return (Caja) super.clone();
        } catch (CloneNotSupportedException e) {
            throw new AssertionError();
        }
    }
}

public class DemoPrototype {
    public static void main(String[] args) {
        Caja caja1 = new Caja();
        caja1.agregar("Lapiz");

        Caja caja2 = caja1.clone();
        caja2.agregar("Regla");

        System.out.println("Caja 1: " + caja1.elementos);
        System.out.println("Caja 2: " + caja2.elementos);

    }

}
```

- Si queremos romperlo solo debemos cambiar ` Caja clone()` `return (Caja) super.clone();`
- Por
```java
Caja caja = (Caja) super.clone();
caja.elementos = new ArrayList<>(this.elementos);
return caja;
```

---

## 🧪 Trabajo voluntario (para casa)

### 🎯 Objetivo
Implementar en Java el sistema representado por los siguientes diagramas UML:

<img width="960" alt="image" src="https://github.com/user-attachments/assets/37a74914-f94f-4589-8bdc-f0c77528fa58" />
<img width="914" alt="image" src="https://github.com/user-attachments/assets/c0c8c8ea-a802-4e0d-9c10-6d80f28c0988" />


### 🔧 Requisitos
- Crear clases en Java según los diagramas.
- Implementar Prototype y Singleton según se muestra.
- Personalizar al menos 2 formularios clonados.
- Mostrar información en consola.

### 🎁 Bonificación
- Este trabajo es **optativo**, pero suma `0,5` decimas para la prueba.

---

# 🪪 Trabajo obligatorio: Generador de Credenciales de Evento

### Estudiante(s):  
- Nombre Apellido – IEI-087  
- (Agregar más si es grupo)

---

## 🚀 Generador de Credenciales de Evento
Tu tarea será diseñar e implementar un sistema que permita emitir credenciales personalizadas para un evento, a partir de una plantilla base. Cada credencial incluirá datos como nombre del asistente, cargo y RUT.

## 🧬 Patrón Prototype – Aplicación

---

## 🔒 Patrón Singleton – Aplicación

---

## 📸 Plantilla de entrega

> https://github.com/lonkonao/PatronesDeDiseno/tree/main/ejemplo


📊 Rúbrica de Evaluación – Proyecto: Generador de Credenciales de Evento

**Puntaje total: 70 puntos**

| Criterio                              | Nivel alcanzado                                                                 | Puntaje |
|---------------------------------------|----------------------------------------------------------------------------------|---------|
| **Implementación de Prototype**       | Clonación funcional, deep copy aplicada correctamente, campos personalizables   | /15     |
| **Implementación de Singleton**       | Constructor privado, acceso controlado, uso global correcto                     | /15     |
| **Menú funcional por consola**        | Agrega, visualiza, gestiona lista correctamente                                 | /5     |
| **Organización y claridad del código**| Legible, dividido en clases, sin redundancia                                    | /10     |
| **Diagrama UML (clases)**             | Correcto, con relaciones, visibilidades y patrones evidenciados                 | /10     |
| **Informe técnico completo y claro en Github**  | Incluye todo lo solicitado, redactado con buena presentación                    | /15     |
| **Total**                             |                                                                                  | **/70** |

---

## ✅ Fechas de entrega
- `0,5` Decimas Martes 6 de mayo 2025 a las 23:59 hrs
- En `Parejas` sin decimas Miercoles 7 de mayo 2025 a las 23:59 hrs
- `Ìndividual` sin decimas Jueves 8 de mayo 2025 a las 23:59 hrs

## Presentación vista en clases
[Clase6](https://github.com/user-attachments/files/20020512/Clase6.pdf)
