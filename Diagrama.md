# Diagrama de clase

## Integrantes:
- Juan Esteban Alvarez Arciniegas
- Danna Michelle Morales Losada


## Descripcion general:

- Este proyecto implementa una base de datos para un sistema de carrito de compras que gestiona roles de Administrador y Comprador. Incluye funcionalidades como registro y autenticación de usuarios, administración de productos en inventario, y generación de facturas detalladas para cada compra. La estructura del sistema se organiza en torno a entidades clave, que incluyen Usuario, Producto, Inventario, Factura, y DetalleFactura. Este diseño permite realizar consultas y relaciones entre varias entidades, mejorando la funcionalidad y gestión de datos en el sistema de compras.

## Código WSD

```plantuml
@startuml

package "Clases Principales" {
    class Usuario {
        - nombreCompleto : String
        - apellidos : String
        - correoElectronico : String
        - contrasenia : String
    }

    class Producto {
        - nombre : String
        - descripcion : String
        - costo : Float
        - cantidad : Int
    }

    class Inventario {
        - producto : Producto
        - proveedor : String
        - ordenCompra : String
        - imagen : String
    }

    class DetalleFactura {
        - descripcion : String
        - IVA : Double
        - tipoPago : String
        - factura : Factura
    }

    class Factura {
        - usuario : Usuario
        - producto : Producto
        - costoEnvio : Float
        - totalCompra : Float
        - totalUnitario : Float
    }
}

package "Interfaz CRUD y Entidad Base" {
    interface CRUD {
        + Create(Entity entity) : EntityClass
        + Update(Entity entity, Integer id) : void
        + All(Boolean data) : List<Entity>
        + FindById(Integer id) : Optional<Entity>
        + Delete(Integer id) : void
    }

    abstract class BaseEntity implements CRUD {
        - status : Boolean
        - createdAt : LocalDateTime
        - updatedAt : LocalDateTime
        - deletedAt : LocalDateTime
        - createdBy : Integer
        - updatedBy : Integer
        - deletedBy : Integer
    }
}

package "Entidades Implementadas" {
    class UsuarioEntity extends BaseEntity {
    }

    class ProductoEntity extends BaseEntity {
    }

    class InventarioEntity extends BaseEntity {
    }

    class DetalleFacturaEntity extends BaseEntity {
    }

    class FacturaEntity extends BaseEntity {
    }
}

Usuario *-- Factura : "realiza"
Producto *-- Factura : "detallado en"
Factura *-- DetalleFactura : "compuesto por"
Producto *-- Inventario : "almacenado en"

@enduml
```
## Diagrama 
![](DiagramaClase.png)


