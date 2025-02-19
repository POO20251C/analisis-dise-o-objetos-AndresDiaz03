# Codigos de Diagramas UML de todos los diferentes casos:

## Solución de cada caso

En este archivo se encuentra cada uno de los códigos correspondientes al Diagrama UML que se elaboro en Mermaid, todos los casos están resueltos y bien detallados.

Integrantes del Equipo: Andres Felipe Diaz


**Caso 1: Caso Biblioteca**

Codigo del diagrama:

# Diagrama UML - Biblioteca 📚

Este diagrama representa el modelo UML para el sistema de gestión de una biblioteca.

```mermaid
classDiagram
    class Libro {
        -string titulo
        -string isbn
        -int anioPublicacion
        +getTitulo()
        +getISBN()
        +getAnioPublicacion()
    }

    class Lector {
        -string nombre
        -string numeroSocio
        -Fecha fechaRegistro
        +realizarPrestamo()
        +devolverLibro()
        +getNombre()
        +getNumeroSocio()
    }

    class Prestamo {
        -Fecha fechaPrestamo
        -Fecha fechaDevolucion
        -boolean estado
        -Libro libro
        -Lector lector
        +actualizarEstado()
        +getFechaPrestamo()
        +getFechaDevolucion()
    }

    class Fecha {
        -int dia
        -int mes
        -int anio
        +getFecha()
    }

    Libro "1" o-- "*" Prestamo : es prestado en
    Lector "1" o-- "*" Prestamo : realiza
    Prestamo "1" -- "1" Libro : asocia
    Prestamo "1" -- "1" Lector : pertenece a
    Prestamo "1" -- "1" Fecha : tiene fecha de

**Caso 2: Caso Hotel**

Codigo del diagrama:

    classDiagram
        class Persona {
            -string nombre
            -string id
            -int edad
            -string numeroTelefonico
        }
        
        class Huesped {
            -Fecha fechaRegistro
            -list Reservas
            +realizarReserva()
        }
        Persona <|-- Huesped : tipo
        
        class Fecha {
            -string dia
            -string mes
            -string anio
        }
        
        class Habitacion {
            -string numero
            -float tarifaPorNoche
        }
        
        class HabitacionIndividual {
            -int maxHuespedes = 1
        }
        Habitacion <|-- HabitacionIndividual : tipo
        
        class HabitacionDoble {
            -int maxHuespedes = 2
        }
        Habitacion <|-- HabitacionDoble : tipo
        
        class HabitacionSuite {
            -int maxHuespedes = 4
        }
        Habitacion <|-- HabitacionSuite : tipo
        
        class Reserva {
            -Habitacion habitacionReservada
            -Huesped huespedReservo
            -Fecha fechaInicio
            -Fecha fechaFin
            -boolean estado
            +actualizarEstado()
            +calcularCosto()
        }
        
        Habitacion "1" o-- "*" Reserva : es reservada
        Huesped "1" o-- "*" Reserva : realiza
        Reserva "*" -- "1" Habitacion : asocia
        Reserva "*" -- "1" Huesped : pertenece a
        Reserva "1" -- "1" Fecha : tiene


**Caso 3: Caso Tienda de Mascotas**

Codigo del diagrama:

    classDiagram
        class Persona {
            -string nombre
            -string identificacion
            -string fechaRegistro
        }
        
        class Dueno {
            +registrarMascota()
            +agendarCita()
        }
        Persona <|-- Dueno
        
        class Mascota {
            -string nombre
            -string especie
            -string fechaNacimiento
        }
        
        class Cita {
            -string fecha
            -string hora
            -boolean estado
            +actualizarEstado()
        }
        
        Dueno "1" o-- "*" Mascota : posee
        Mascota "1" o-- "*" Cita : asiste a
        Dueno "1" o-- "*" Cita : programa
        Cita "1" -- "1" Mascota : corresponde a
        Cita "1" -- "1" Dueno : pertenece a


**Caso 4: Caso Tienda de Música**

Codigo del diagrama:

    classDiagram
        class Persona {
            -string nombre
            -string identificacion
        }
        
        class Cliente {
            -Fecha fechaRegistro
            +realizarCompra()
            +devolverAlbum()
        }
        Persona <|-- Cliente : tipo

        class Fecha {
            -string dia
            -string mes
            -string anio
        }

        class Album {
            -string titulo
            -string codigoIdentificacion
            -string fechaLanzamiento
        }

        class Compra {
            -Fecha fechaCompra
            -boolean estado
            +actualizarEstado()
        }
        
        Cliente "1" o-- "*" Compra : realiza
        Compra "1" -- "1" Album : pertenece a
        Compra "1" -- "1" Cliente : pertenece a
        Album "1" o-- "*" Compra : es comprado
        Cliente "1" -- "1" Fecha : tiene
        Compra "1" -- "1" Fecha : ocurre en


**Caso 5: Caso Escuela de Música**

Codigo del diagrama:

    classDiagram
        class Persona {
            -string nombre
            -string identificacion
        }
        
        class Estudiante {
            -Fecha fechaRegistro
            +inscribirseEnCurso()
            +completarCurso()
        }
        Persona <|-- Estudiante : tipo

        class Fecha {
            -string dia
            -string mes
            -string anio
        }

        class Curso {
            -string nombre
            -string codigoCurso
            -int duracionSemanas
        }

        class Inscripcion {
            -Fecha fechaInscripcion
            -boolean estado
            +actualizarEstado()
        }
        
        Estudiante "1" o-- "*" Inscripcion : realiza
        Inscripcion "1" -- "1" Curso : pertenece a
        Inscripcion "1" -- "1" Estudiante : pertenece a
        Curso "1" o-- "*" Inscripcion : es inscrito en
        Estudiante "1" -- "1" Fecha : tiene
        Inscripcion "1" -- "1" Fecha : ocurre en


**Caso 6: Caso Galería de Arte**

Codigo del diagrama:

    classDiagram
        class Galeria {
            -string nombre
            -List~Artista~ artistas
            -List~Exposicion~ exposiciones
            +crearArtista()
            +gets()
            +sets()
        }

        class Artista {
            -string id
            -string nombre
            -Fecha fechaRegistro
            -List~Obra~ obras
            +presentarObras()
            +gets()
            +sets()
        }

        class Obra {
            -string titulo
            -string id
            -Fecha fechaCreacion
            +gets()
            +sets()
        }

        class Exposicion {
            -Fecha fechaInicio
            -Fecha fechaFin
            -boolean estado
            -Artista artista
            -Obra obra
            +cambiarEstado()
            +gets()
            +sets()
        }

        class Fecha {
            -string dia
            -string mes
            -string anio
        }

        Galeria "1" o-- "*" Artista : contiene
        Galeria "1" o-- "*" Exposicion : organiza
        Artista "1" o-- "*" Obra : crea
        Artista "1" -- "1" Exposicion : participa
        Obra "1" -- "1" Exposicion : exhibe
        Exposicion "1" -- "1" Fecha : inicia
        Exposicion "1" -- "1" Fecha : finaliza
        Artista "1" -- "1" Fecha : registra en
        Obra "1" -- "1" Fecha : creada en


