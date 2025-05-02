# Sistema Bancario ABC - Nuevas Funcionalidades

## Instrucciones para la entrega

Esta sustentación consiste en implementar dos módulos para el Sistema Bancario ABC. El código base ya está proporcionado y **solo debes implementar las funciones específicas** que se indican a continuación.

### Importante:
- **NO modifiques** la estructura del código principal, constantes o funciones de inicialización
- **NO modifiques** la función `main()` que ya está implementada
- **SOLO implementa** las funciones que se indican como pendientes

## Formato de entrega

Para cada módulo, entrega **solo** el archivo fuente (.cpp) con las implementaciones de las funciones solicitadas.

## Evaluación

Tu código será evaluado según:
- Correcta implementación de la funcionalidad requerida
- Manejo adecuado de los casos límite
- Coincidencia con las salidas de ejemplo proporcionadas


## 1. Módulo de Notificaciones Limitadas

Implemente un módulo de notificaciones que permita almacenar hasta 10 notificaciones por socio. Utilice un array fijo para almacenar las notificaciones. El módulo debe incluir las siguientes funcionalidades:

- Agregar una nueva notificación (si hay espacio disponible).
- Mostrar todas las notificaciones de un socio.
- Marcar una notificación como leída.
- Eliminar la notificación más antigua cuando el array esté lleno y se quiera agregar una nueva.
```cpp
void agregarNotificacion(ModuloNotificaciones* modulo, const char* mensaje);
void mostrarNotificaciones(const ModuloNotificaciones* modulo);
void marcarComoLeida(ModuloNotificaciones* modulo, int indice);
```

```cpp
#include <iostream>
#include <cstring>

const int MAX_NOTIFICACIONES = 10;
const int MAX_LONGITUD_MENSAJE = 100;

struct Notificacion {
    char mensaje[MAX_LONGITUD_MENSAJE];
    bool leida;
};

struct ModuloNotificaciones {
    Notificacion notificaciones[MAX_NOTIFICACIONES];
    int cantidadNotificaciones;
};

void inicializarModulo(ModuloNotificaciones* modulo) {
    modulo->cantidadNotificaciones = 0;
    for (int i = 0; i < MAX_NOTIFICACIONES; i++) {
        modulo->notificaciones[i].mensaje[0] = '\0';
        modulo->notificaciones[i].leida = false;
    }
}

void agregarNotificacion(ModuloNotificaciones* modulo, const char* mensaje);
void mostrarNotificaciones(const ModuloNotificaciones* modulo);
void marcarComoLeida(ModuloNotificaciones* modulo, int indice);

int main() {
    ModuloNotificaciones modulo;
    inicializarModulo(&modulo);

    agregarNotificacion(&modulo, "Bienvenido al sistema bancario ABC");
    agregarNotificacion(&modulo, "Su préstamo ha sido aprobado");
    agregarNotificacion(&modulo, "Nuevo servicio de banca en línea disponible");

    std::cout << "Notificaciones sin leer:" << std::endl;
    mostrarNotificaciones(&modulo);

    marcarComoLeida(&modulo, 0);

    std::cout << "\nNotificaciones después de marcar como leída:" << std::endl;
    mostrarNotificaciones(&modulo);

    return 0;
}

// Implementa las funciones aquí
```
Ejemplod e salida:
```
Agregando notificaciones:
Notificación agregada: "Bienvenido al sistema"
Notificación agregada: "Su pago mensual está próximo"

Mostrando notificaciones:
1. [No leída] Bienvenido al sistema
2. [No leída] Su pago mensual está próximo

Marcando como leída la notificación 1...

Mostrando notificaciones actualizadas:
1. [Leída] Bienvenido al sistema
2. [No leída] Su pago mensual está próximo
```
## 2. Sistema de Gestión de Cajeros Automáticos

Implemente un sistema para gestionar el estado de hasta 20 cajeros automáticos del banco. Utilice un array fijo para almacenar la información de cada cajero. El sistema debe incluir:

- Registro del estado de cada cajero (operativo, fuera de servicio, en mantenimiento).
- Actualización del saldo disponible en cada cajero.
- Registro de las últimas 5 transacciones realizadas en cada cajero.
- Generación de un informe que muestre el estado actual de todos los cajeros.
```cpp
void agregarCajero(SistemaCajeros* sistema, int id, EstadoCajero estado, double saldoInicial);
void actualizarEstadoCajero(SistemaCajeros* sistema, int id, EstadoCajero nuevoEstado);
void registrarTransaccion(SistemaCajeros* sistema, int id, double monto, const char* tipo);
void generarInforme(const SistemaCajeros* sistema);
```
```cpp
#include <iostream>
#include <cstring>

const int MAX_CAJEROS = 20;
const int MAX_TRANSACCIONES = 5;

enum EstadoCajero { OPERATIVO, FUERA_DE_SERVICIO, EN_MANTENIMIENTO };

struct Transaccion {
    double monto;
    char tipo[20];  // "retiro" o "deposito"
};


struct Cajero {
    int id;
    EstadoCajero estado;
    double saldo;
    Transaccion ultimasTransacciones[MAX_TRANSACCIONES];
    int numTransacciones;
};

struct SistemaCajeros {
    Cajero cajeros[MAX_CAJEROS];
    int numCajeros;
};

void inicializarSistema(SistemaCajeros* sistema) {
    sistema->numCajeros = 0;
    for (int i = 0; i < MAX_CAJEROS; i++) {
        sistema->cajeros[i].id = 0;
        sistema->cajeros[i].estado = FUERA_DE_SERVICIO;
        sistema->cajeros[i].saldo = 0.0;
        sistema->cajeros[i].numTransacciones = 0;
    }
}
void agregarCajero(SistemaCajeros* sistema, int id, EstadoCajero estado, double saldoInicial);
void actualizarEstadoCajero(SistemaCajeros* sistema, int id, EstadoCajero nuevoEstado);
void registrarTransaccion(SistemaCajeros* sistema, int id, double monto, const char* tipo);
void generarInforme(const SistemaCajeros* sistema);
#include <iostream>

int main() {
    SistemaCajeros sistema;
    inicializarSistema(&sistema);

    agregarCajero(&sistema, 1, OPERATIVO, 50000.0);
    agregarCajero(&sistema, 2, OPERATIVO, 30000.0);

    registrarTransaccion(&sistema, 1, 1000.0, "retiro");
    registrarTransaccion(&sistema, 2, 500.0, "deposito");

    actualizarEstadoCajero(&sistema, 2, EN_MANTENIMIENTO);

    std::cout << "Informe de estado de cajeros:" << std::endl;
    generarInforme(&sistema);

    return 0;
}
// Implementa las funciones aquí
```
Ejemplo de salida:

```
Informe de Cajeros Automáticos

Cajero #1
Estado: OPERATIVO
Saldo: $50000.00
Últimas transacciones:
1. Retiro: $200.00
2. Depósito: $500.00
3. Retiro: $100.00

Cajero #2
Estado: EN_MANTENIMIENTO
Saldo: $0.00
Sin transacciones recientes

Cajero #3
Estado: OPERATIVO
Saldo: $75000.00
Últimas transacciones:
1. Retiro: $300.00
2. Retiro: $50.00

Total cajeros operativos: 2
Total cajeros en mantenimiento: 1
Total cajeros fuera de servicio: 0
```

## Entrega

Para cada funcionalidad, entrega:

1. El código fuente completo (.cpp ).


¡Buena suerte con la implementación!
