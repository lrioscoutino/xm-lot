# XM-Lot Generator 🎰

Aplicación parametrizada para la generación aleatoria de números de lotería (Powerball, Mega Millions, Melate, etc.).

## Arquitectura del Algoritmo de Generación

El siguiente diagrama describe el flujo parametrizado de selección de números sin duplicados y ordenamiento automático:

```mermaid
flowchart TD
    START([INICIO: Seleccionar Lotería]) --> CONFIG[Cargar Parámetros: N, MaxMain, M, MaxSpecial]
    CONFIG --> INIT_MAIN[Inicializar BolasPrincipales = [ ]]
    INIT_MAIN --> GEN_MAIN[Generar aleatorio 'Num' en [1, MaxMain]]
    GEN_MAIN --> CHECK_DUP{¿'Num' en BolasPrincipales?}
    CHECK_DUP -- SÍ --> GEN_MAIN
    CHECK_DUP -- NO --> ADD_MAIN[Agregar 'Num' a BolasPrincipales]
    ADD_MAIN --> CHECK_COUNT{¿Longitud == N?}
    CHECK_COUNT -- NO --> GEN_MAIN
    CHECK_COUNT -- SÍ --> SORT_MAIN[Ordenar BolasPrincipales]
    SORT_MAIN --> CHECK_SPEC_REQ{¿M > 0?}
    CHECK_SPEC_REQ -- NO --> DISP[Mostrar Combinación]
    CHECK_SPEC_REQ -- SÍ --> INIT_SPEC[Inicializar BolasEspeciales = [ ]]
    INIT_SPEC --> GEN_SPEC[Generar aleatorio 'Spec' en [1, MaxSpecial]]
    GEN_SPEC --> ADD_SPEC[Agregar 'Spec' a BolasEspeciales]
    ADD_SPEC --> CHECK_SPEC_COUNT{¿Longitud == M?}
    CHECK_SPEC_COUNT -- NO --> GEN_SPEC
    CHECK_SPEC_COUNT -- SÍ --> DISP
    DISP --> END([FIN])
```# xm-lot
