# Taller de Sistema de Gestión de Inventario en C++

## Descripción

Este taller está diseñado para estudiantes de programación avanzada en C++. El objetivo es implementar un sistema de gestión de inventario que aplique conceptos de estructuras, arreglos y apuntadores.

## Objetivos de Aprendizaje

- Implementar estructuras para representar productos
- Utilizar arreglos de estructuras para manejar el inventario
- Aplicar conceptos de apuntadores a arreglos y estructuras
- Practicar el acceso y modificación de estructuras usando apuntadores
- Desarrollar funciones que trabajen con apuntadores para modificar y consultar información

## Estructura del Proyecto

El proyecto consiste en implementar las siguientes funciones:

```cpp
const int MAX_PRODUCTOS = 100;

struct Producto {
    int id;
    char nombre[50];
    float precio;
    int cantidad;
};

void inicializarInventario(Producto* inventario, int* tamano);
void agregarProducto(Producto* inventario, int* tamano, Producto nuevoProducto);
Producto* buscarProducto(Producto* inventario, int tamano, int id);
void actualizarCantidad(Producto* producto, int nuevaCantidad);
void imprimirProducto(const Producto* producto);
void imprimirInventario(const Producto* inventario, int tamano);
void ordenarInventarioPorPrecio(Producto* inventario, int tamano);
void manejarInventario();
```

## Conceptos Clave

### Intercambio de Variables Usando Apuntadores

Una operación fundamental en este taller es el intercambio de variables usando apuntadores. Esta técnica es especialmente útil en la función `ordenarInventarioPorPrecio`.

#### Ejemplo de Implementación:

```cpp
void intercambiar(Producto* a, Producto* b) {
    Producto temp = *a;
    *a = *b;
    *b = temp;
}
```

#### Uso en el Ordenamiento:

```cpp
void ordenarInventarioPorPrecio(Producto* inventario, int tamano) {
    for (int i = 0; i < tamano - 1; i++) {
        for (int j = 0; j < tamano - i - 1; j++) {
            if (inventario[j].precio > inventario[j + 1].precio) {
                intercambiar(&inventario[j], &inventario[j + 1]);
            }
        }
    }
}
```

#### Puntos Clave:
- La función `intercambiar` recibe apuntadores a `Producto`.
- Usamos dereferenciación (`*a`, `*b`) para acceder y modificar los valores.
- Esta técnica permite intercambiar objetos completos sin copiar todo su contenido.

Asegúrese de implementar y utilizar esta función de intercambio en su solución.

## Instrucciones de Implementación

1. **Arreglos y Apuntadores:** Use un arreglo estático de `Producto` para el inventario.
2. **Apuntadores a Arreglos:** En `imprimirInventario`, use un apuntador constante al arreglo.
3. **Apuntadores y Estructuras:** `buscarProducto` debe devolver un apuntador al `Producto`.
4. **Acceso a Estructuras:** Use apuntadores en `actualizarCantidad` e `imprimirProducto`.
5. **Ordenamiento:** Implemente `ordenarInventarioPorPrecio` usando apuntadores para intercambiar.
6. **Menú Principal:** Implemente `manejarInventario` para interactuar con el usuario.
7. **Intercambio de Variables:** Implemente la función `intercambiar` y utilícela en `ordenarInventarioPorPrecio`.

## Ejemplo de Uso

```cpp
int main() {
    manejarInventario();
    return 0;
}
```

## Evaluación

Se evaluará:
1. Implementación correcta de todas las funciones.
2. Uso apropiado de apuntadores.
3. Funcionalidad del sistema de inventario.
4. Implementación y uso correcto de la función de intercambio de variables usando apuntadores.

## Entrega

Subir el código fuente comentado a la plataforma designada. Asegurarse de que compile y funcione correctamente.


## Tiempo de Realización

2 horas durante la clase.

---

© 2024 Departamento de Ingeniería de Sistemas, Pontificia Universidad Javeriana
