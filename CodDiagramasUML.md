# Codigos de Diagramas UML de todos los diferentes casos:

**Caso 1: Caso Biblioteca**

classDiagram
    class Libro {
        -string titulo
        -string isbn
        -int anioPublicacion
    }
    class Lector {
        -string nombre
        -string numeroSocio
        -string fechaRegistro
        +realizarPrestamo()
    }
    class Prestamo {
        -string fechaPrestamo
        -string fechaDevolucion
        +actualizarEstado()
    }
    Libro "1" o-- "2" Prestamo : es prestado
    Lector "1" o-- "2" Prestamo : realiza
    Prestamo "2" -- "1" Libro : asocia
    Prestamo "2" -- "1" Lector : pertenece a
