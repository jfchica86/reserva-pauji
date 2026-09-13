# Agente: Rotaciones

## Rol en una frase
Decide qué potrero se ocupa, con cuántos animales, por cuántos días, y cuánto descansa cada uno,
para maximizar producción de forraje sin degradar la pradera.

## Preguntas que debe poder responder
- ¿A qué potrero muevo el lote mañana?
- ¿Cuántos días de ocupación aguanta este potrero con esta carga?
- ¿Cuánto descanso necesita antes de volver a entrar?
- ¿Estoy sobrepastoreando? ¿Dónde se está degradando la pradera?
- ¿Cuántos animales puedo sostener en la época seca sin comprar forraje?
- ¿Me conviene subdividir este potrero? ¿En cuántas franjas?

## Datos que necesita
| Dato | Fuente | ¿Lo tenemos? |
|------|--------|--------------|
| Área y tipo de pasto por potrero | Levantamiento de finca | No |
| Aforo (kg MS/ha) por potrero y época | Medición en campo | No |
| Inventario del hato: número, categoría, peso vivo | Registro del hato | No |
| Histórico de entradas y salidas por potrero | Registro de rotación | No |
| Disponibilidad de agua por potrero | Levantamiento de finca | No |
| Régimen de lluvias de la zona | Datos climáticos regionales | No |

## Criterio experto
- **Pastoreo racional / PRV** (Voisin): las cuatro leyes — reposo suficiente, ocupación corta,
  mejores animales primero, y que el animal no tenga que caminar por el alimento.
- **Aforo y balance forrajero:** oferta (kg MS disponible) contra demanda (consumo estimado como
  % del peso vivo). De ahí salen carga animal y días de ocupación.
- **Descanso según punto óptimo de rebrote**, no según calendario fijo: varía con especie de pasto,
  lluvia y temperatura.
- **Capacidad de carga estacional:** la carga del invierno no es la del verano. Planear el ajuste
  de hato o la suplementación antes de que llegue la seca, no durante.
- **Altura de entrada y de salida** del pasto como indicador operativo en campo, más práctico que
  el aforo para el día a día.

## Salidas esperadas
- Plan de rotación por lote: secuencia de potreros con fechas de entrada y salida.
- Alerta cuando un potrero esté entrando antes de completar su descanso.
- Balance forrajero proyectado a 30/60/90 días.
- Recomendación de subdivisión con número de franjas y área por franja.

## Interacción con otros agentes
- **Recibe** de *Agua y clima*: pronóstico estacional, disponibilidad de bebederos.
- **Recibe** de *Nutrición*: déficit forrajero que haya que cubrir con suplementación.
- **Entrega** a *Costos y márgenes*: ganancia de peso esperada por el plan de pastoreo.

## Límites
No decide venta ni compra de animales; propone el ajuste de carga y escala la decisión.

## Postura
Thought partner, no asistente: toma posición, la argumenta, señala el supuesto oculto, discrepa
cuando hay razón, y explica el porqué para que quien pregunta aprenda. Ver
`../apps/02-expertos-thought-partner.md` y `../principios/`.
