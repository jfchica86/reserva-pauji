# App 3 — Rotaciones especializadas

**Publicación:** juanchica.com · **Acceso:** interno (operación) · **Estado:** por construir

## Qué es

Una app que **genera planes de rotación** para los potreros reales de la finca: qué lote entra a
qué potrero, cuántos días, y cuánto descansa cada potrero antes de volver a recibir animales.

Se diferencia del experto conversacional en rotaciones (app 2): ese **explica y discute**; este
**produce un plan ejecutable** que alguien sigue en campo. Conviene que convivan — el plan lo
genera la app 3, y cuando uno quiere entender o retar el plan, habla con el experto.

El criterio técnico completo (PRV/Voisin, aforo, balance forrajero, capacidad de carga estacional,
alturas de entrada y salida) está en `../agentes/rotaciones.md`.

## Qué produce

- **Calendario de rotación por lote** con fechas de entrada y salida por potrero.
- **Balance forrajero** proyectado a 30/60/90 días: oferta contra demanda.
- **Alertas**: potrero que entra antes de completar descanso, carga por encima de capacidad,
  déficit forrajero previsto para la seca.
- **Propuestas de subdivisión** con número de franjas y área.
- **Registro de lo que realmente pasó** — el plan contra la ejecución. Sin esto la app no aprende
  ni sirve como historia.

## Por qué "especializadas"

No es un calendario genérico. El plan se construye sobre:
- Los potreros reales, con su área y su tipo de pasto.
- El aforo medido, no un promedio de tabla.
- La estacionalidad de lluvia de esa zona.
- El hato real con sus categorías y pesos.
- Los principios de manejo definidos en `principios/`.

## Interfaz

Dos contextos distintos y hay que resolver los dos:

- **Planeación (escritorio):** mapa de potreros, escenarios, el plan completo.
- **Campo (celular):** "¿a dónde muevo el lote hoy?" y un botón para registrar el movimiento real.
  Tiene que funcionar con mala señal — considerar que guarde y sincronice después.

## Dependencias
- Inventario de potreros con área, pasto y aforo (bloqueante)
- Inventario del hato (bloqueante) → viene de la app 4
- `principios/`
