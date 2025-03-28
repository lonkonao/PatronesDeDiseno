Los codigos se ejecutan en [PlantUML](https://www.plantuml.com/)

## Ejercicio 1

### Diagrama de Clases
Un restaurante necesita un sistema para gestionar sus pedidos. Se deben modelar las siguientes clases:
- **Cliente**
- **Pedido**
- **Producto**
- **Restaurante**

### Instrucciones:
1. Dibuja un Diagrama de Clases UML con estas entidades.
2. Agrega los atributos y métodos adecuados en cada clase.
3. Establece las relaciones correctas entre ellas (Asociación, Agregación, Composición, etc.).

### Resolución

```plantuml
@startuml
class Cliente {
    - nombre: String
    - telefono: String
    - email: String
    + realizarPedido()
}

class Pedido {
    - numero: int
    - fecha: Date
    - estado: String
    + calcularTotal()
    + cambiarEstado(nuevoEstado: String)
}

class Producto {
    - nombre: String
    - precio: double
    + obtenerDetalle()
}

class Restaurante {
    - nombre: String
    - direccion: String
    + registrarPedido(pedido: Pedido)
    + listarPedidos()
}

' Relaciones entre clases
Cliente "1" -- "*" Pedido : realiza
Pedido "1" *-- "*" Producto : contiene
Restaurante "1" o-- "*" Pedido : gestiona
@enduml
```

### Imagen del Diagrama
![image](https://github.com/user-attachments/assets/a85c97f4-c4ce-451a-adb0-687d108c4a3a)


---

## Ejercicio 2

### Diagrama de Casos de Uso
Modela los casos de uso para un sistema de biblioteca. Los actores principales son:
- **Usuario**
- **Bibliotecario**

### Instrucciones:
1. Dibuja un Diagrama de Casos de Uso UML.
2. Representa los siguientes casos de uso:
   - Buscar libro
   - Pedir préstamo
   - Devolver libro
   - Administrar inventario
3. Usa Asociación, Inclusión (<<include>>) y Extensión (<<extend>>) cuando sea necesario.

### Resolución

```plantuml
@startuml
left to right direction
actor Usuario
actor Bibliotecario

usecase "Buscar libro" as UC1
usecase "Pedir préstamo" as UC2
usecase "Devolver libro" as UC3
usecase "Administrar inventario"
usecase "Multas pendientes" as UC5

Usuario --> UC1
Usuario --> UC2
Usuario --> UC3
Bibliotecario --> "Administrar inventario"

UC2 .> UC1 : <<include>>
UC3 .> UC5 : <<extend>>
@enduml
```
### Imagen del Diagrama
![image](https://github.com/user-attachments/assets/82aa2bff-0802-43bb-937b-160004336f1b)

---

## Ejercicio 3

### Diagrama de Secuencia
Modela el flujo de inicio de sesión en un sistema web. Los elementos involucrados son:
- **Usuario**
- **Página de Login**
- **Servidor**
- **Base de Datos**

### Instrucciones:
1. El Usuario ingresa sus credenciales en la Página de Login.
2. La Página de Login envía los datos al Servidor.
3. El Servidor consulta la Base de Datos para validar el usuario.
4. La Base de Datos responde al Servidor.
5. Si los datos son correctos, el Servidor permite el acceso; de lo contrario, muestra un error.
6. Usa los tipos de mensajes adecuados (->, -->, -->>).

### Resolución

```plantuml
@startuml
actor Usuario
entity "Página de Login" as Login
entity Servidor
entity "Base de Datos" as BD

Usuario -> Login : Ingresa credenciales
Login -> Servidor : Enviar credenciales
Servidor -> BD : Consultar usuario
BD --> Servidor : Responder validación
alt Credenciales correctas
    Servidor -> Login : Acceso permitido
else Credenciales incorrectas
    Servidor -> Login : Error de login
end
@enduml
```
### Imagen del Diagrama
![image](https://github.com/user-attachments/assets/a36dc465-5fe0-470e-be1f-d37e7ff5230a)

---

[Clase2.pdf](https://github.com/user-attachments/files/19510744/Clase2.pdf)

