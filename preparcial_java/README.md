# Taller: Sistema de Gestión Hotelera

## Descripción
Este taller consiste en implementar un sistema de gestión hotelera siguiendo el diagrama de clases proporcionado. El sistema debe manejar reservas, diferentes tipos de habitaciones y categorías de clientes.
![image](https://github.com/user-attachments/assets/fac9ae4b-54d8-4371-9cf8-9dfc2b870d03)

## Objetivos
- Implementar el sistema completo en Java
- Aplicar conceptos de POO (herencia, polimorfismo, encapsulamiento)
- Implementar manejo de excepciones
- Implementar serialización para persistencia de datos

## Requisitos Funcionales

### Clases Principales
1. **Hotel**
   - Gestionar habitaciones ocupadas y disponibles
   - Implementar métodos para reservas y cálculo de ganancias
   - Serializar el estado del hotel

2. **Habitacion**
   - Tres tipos: Simple, Doble, Matrimonial
   - Cada tipo debe implementar sus propios métodos de:
     - `mostrarDetalles()` - Muestra información específica de la habitación
     - `calcularPrecioTotal(int dias)` - Calcula el precio según el tipo y días
     - `verificarDisponibilidad()` - Comprueba si la habitación está disponible
     - `aplicarServiciosAdicionales(List<Servicio> servicios)` - Agrega servicios extra
   - Debe ser serializable

3. **Cliente**
   - Dos tipos: Habitual y Esporádico
   - Los clientes habituales tienen descuento
   - Implementar serialización

4. **Reserva**
   - Gestionar fecha de inicio y duración
   - Vincular cliente con habitación
   - Implementar serialización

## Excepciones a Implementar
1. `HabitacionNoDisponibleException`
   - Cuando se intenta reservar una habitación ocupada

2. `FechaInvalidaException`
   - Para fechas de reserva inválidas

3. `ClienteNoValidoException`
   - Para operaciones con clientes no registrados

4. `CapacidadExcedidaException`
   - Cuando se supera el límite de personas por habitación

## Requisitos Técnicos
1. **Serialización**
   - Implementar `Serializable` en todas las clases
   - Crear métodos para guardar y cargar el estado del sistema
   - Gestionar la persistencia de:
     - Reservas activas
     - Información de clientes
     - Estado de las habitaciones

2. **Validaciones**
   - Verificar disponibilidad de habitaciones
   - Validar fechas de reserva
   - Comprobar descuentos aplicables
   - Validar capacidad máxima por tipo de habitación

3. **Documentación**
   - Agregar comentarios explicativos en el código

