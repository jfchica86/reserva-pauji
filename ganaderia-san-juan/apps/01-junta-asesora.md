# App 1 — Mi Junta Asesora

**Publicación:** juanchica.com · **Acceso:** privado (Juan) · **Estado:** por construir

## Qué es

Una sala donde Juan convoca a la junta asesora de Ganadería San Juan, le presenta una decisión, y
**los miembros deliberan entre sí** antes de darle una recomendación.

La diferencia con hablar con un experto suelto (app 2) es la **deliberación**: el financiero y el
técnico de pastoreo no ven el mismo problema, y el valor está justamente en verlos discrepar. Una
junta donde todos están de acuerdo no está aportando nada.

## Cómo funciona

1. Juan plantea la decisión ("¿compramos 80 novillos ahora o esperamos a que baje el precio?").
2. Cada miembro opina desde su rol, **viendo lo que dijeron los demás**.
3. Donde hay desacuerdo, se marca explícitamente y se argumenta.
4. La junta entrega una recomendación con sus disidencias — no un consenso forzado.
5. Juan puede interpelar a un miembro específico y la conversación sigue.

## Composición de la junta (por definir)

Roles candidatos, a confirmar en Fase 4:

| Rol | Qué aporta | Qué tiende a decir |
|-----|-----------|--------------------|
| Financiero | Caja, riesgo, apalancamiento | "¿de dónde sale la plata y qué pasa si no sale?" |
| Técnico de pastoreo | Suelo, forraje, capacidad de carga | "el suelo no aguanta esa carga" |
| Operador de finca | Realidad de campo, mano de obra | "eso en la práctica no se puede hacer" |
| Comercial / mercado | Precios, momento de venta, canales | "el mercado no va para allá" |
| Inversionista | Retorno, confianza, reputación | "¿cómo le explico esto a quien puso la plata?" |
| Escéptico / abogado del diablo | Romper el consenso | "¿y si esto sale mal?" |

> Decisión pendiente: ¿perfiles por rol, personas reales modeladas, o mezcla? Modelar a alguien
> real da más textura pero exige conocerlo bien y tiene su propia incomodidad.

## Decisiones de diseño

- **La junta asesora, no decide.** Juan decide. La app nunca presenta una recomendación como orden.
- **El desacuerdo se preserva.** Si hay dos posiciones, se muestran las dos. Promediarlas destruye
  el valor del ejercicio.
- **Memoria de sesiones.** Lo que la junta recomendó antes, y qué pasó después, debería estar
  disponible. Una junta con memoria es mucho más útil que una que arranca de cero.
- **Datos reales.** La junta consulta la app 4. Deliberar sobre números inventados no sirve.

## Construcción

Cada miembro es un agente con su prompt, su rol y los principios cargados. La deliberación es una
orquestación por turnos: ronda de posiciones iniciales → ronda de réplica viendo lo de los demás →
síntesis con disidencias marcadas.

## Dependencias
- `principios/` (obligatorio — sin esto la junta es genérica)
- App 4 para datos reales (deseable; se puede empezar sin ella)
