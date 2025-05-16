# Taller Práctico: Herencia en Java

## Objetivo
Comprender y aplicar los conceptos básicos de herencia en Java mediante ejercicios prácticos.

## Duración
90 minutos

## Requisitos previos
- Conocimientos básicos de Java
- Entender el concepto de clases y objetos
- IDE Java instalado (Eclipse, IntelliJ IDEA, NetBeans, etc.)

## Actividades

### 1. Sistema de Figuras Geométricas (30 min)

#### Instrucciones:
1. Crea una clase base llamada `FiguraGeometrica` con:
   - Un atributo protegido `color` (String)
   - Un constructor que inicialice el color
   - Un método `getColor()` que devuelva el color
   - Un método abstracto `calcularArea()` que devuelva un double

2. Crea tres clases que hereden de `FiguraGeometrica`:
   - `Circulo`: con un atributo `radio` (double)
   - `Rectangulo`: con atributos `base` y `altura` (double)
   - `Triangulo`: con atributos `base` y `altura` (double)

3. Implementa el método `calcularArea()` en cada subclase:
   - Círculo: π × radio²
   - Rectángulo: base × altura
   - Triángulo: (base × altura) / 2

4. Crea una clase `Main` con un método `main` que:
   - Cree instancias de cada figura
   - Imprima el color y área de cada figura

#### Código de inicio:

```java
// Clase base
public abstract class FiguraGeometrica {
    protected String color;
    
    // Completar constructor
    
    // Método para obtener el color
    
    // Método abstracto calcularArea
}

// Subclases (completar)
public class Circulo extends FiguraGeometrica {
    // Completar
}

public class Rectangulo extends FiguraGeometrica {
    // Completar
}

public class Triangulo extends FiguraGeometrica {
    // Completar
}

// Clase Main
public class Main {
    public static void main(String[] args) {
        // Crear instancias y mostrar resultados
    }
}
```

### 2. Sistema de Empleados (30 min)

#### Instrucciones:
1. Crea una clase base llamada `Empleado` con:
   - Atributos protegidos: `nombre` (String), `id` (String) y `salarioBase` (double)
   - Un constructor que inicialice estos atributos
   - Un método `calcularSalario()` que devuelva el salarioBase
   - Un método `mostrarDetalles()` que imprima la información del empleado

2. Crea dos clases que hereden de `Empleado`:
   - `Gerente`: con un atributo adicional `bonusGerencia` (double)
   - `Desarrollador`: con un atributo adicional `horasExtras` (int) y `pagoPorHoraExtra` (double)

3. Sobrescribe el método `calcularSalario()` en cada subclase:
   - Gerente: salarioBase + bonusGerencia
   - Desarrollador: salarioBase + (horasExtras * pagoPorHoraExtra)

4. Sobrescribe el método `mostrarDetalles()` en cada subclase para incluir la información adicional

5. Crea una clase `Main2` con un método `main` que:
   - Cree al menos un objeto de cada tipo de empleado
   - Llame al método `mostrarDetalles()` para cada empleado
   - Muestre el salario calculado para cada empleado

### 3. Problema de Integración: Sistema de Transporte (30 min)

#### Instrucciones:
1. Crea una clase base llamada `Vehiculo` con:
   - Atributos protegidos: `marca` (String), `modelo` (String), `año` (int)
   - Un constructor que inicialice estos atributos
   - Un método `mostrarInfo()` que imprima la información básica
   - Un método `arrancar()` que imprima un mensaje genérico

2. Crea tres clases que hereden de `Vehiculo`:
   - `Coche`: con atributos adicionales `numeroPuertas` (int) y `tipoCombustible` (String)
   - `Motocicleta`: con atributo adicional `cilindrada` (int)
   - `Camion`: con atributo adicional `capacidadCarga` (double)

3. Sobrescribe el método `mostrarInfo()` en cada subclase para incluir la información específica

4. Sobrescribe el método `arrancar()` en cada subclase con un mensaje personalizado

5. Crea una clase `GestionTransporte` con un método `main` que:
   - Cree al menos un objeto de cada tipo de vehículo
   - Almacene todos los vehículos en un array de tipo `Vehiculo`
   - Recorra el array y llame a los métodos `mostrarInfo()` y `arrancar()` para cada vehículo

## Entrega
Al finalizar el taller, los estudiantes deberán:
1. Compartir su código fuente
2. Explicar brevemente cómo han aplicado el concepto de herencia en cada ejercicio
3. Mencionar alguna dificultad que hayan encontrado y cómo la solucionaron

## Consejos
- Recuerda usar el modificador `@Override` para los métodos sobrescritos
- Utiliza `super` para llamar a métodos o constructores de la clase padre
- Piensa en la jerarquía de clases antes de comenzar a codificar
