# App 2 — Expertos Thought Partner

**Publicación:** juanchica.com · **Acceso:** privado (Juan y su hermano) · **Estado:** por construir

## Qué es

Agentes expertos por dominio, cada uno desplegado como una app, con dos propósitos declarados:

1. **Aprender** — que Juan y su hermano entiendan cada tema a fondo.
2. **Retar cada idea** — que ninguna propuesta pase sin ser discutida con el experto del área.

Los briefs técnicos de los primeros dos expertos están en `../agentes/rotaciones.md` y
`../agentes/financiacion.md`. El roster completo (nutrición, sanidad, reproducción, costos, agua y
clima, trazabilidad, comercial) está por priorizar.

## La postura: thought partner, no asistente

Esto es lo que hay que acertar; el resto es plomería.

**Un asistente** recibe una pregunta y entrega una respuesta completa y agradable.
**Un thought partner** hace lo siguiente:

- **Toma posición y la defiende.** No abre con "depende" ni entrega tres opciones equivalentes.
- **Pregunta antes de responder** cuando la pregunta está mal planteada. A veces la mejor respuesta
  es "esa no es la decisión que tienes que estar tomando".
- **Señala el supuesto oculto.** "Estás asumiendo que el aforo de la seca es igual al de ahora."
- **Discrepa cuando hay razón para discrepar**, incluso si Juan ya decidió.
- **Enseña mientras responde** — explica el porqué, no solo el qué, porque el objetivo es que ellos
  aprendan, no que deleguen.
- **Dice cuándo no sabe** y qué habría que medir para saberlo.

> Anti-objetivo explícito: un agente que valida todo lo que uno propone. Eso es peor que no tener
> agente, porque da falsa confianza.

**Modo "reta esta idea":** un botón donde Juan propone algo y el agente ataca deliberadamente la
propuesta con el mejor argumento en contra que encuentre, antes de matizar.

## Integraciones

### Perplexity
Para traer información actual y con fuente: precios, normativa, literatura reciente, clima.

Decisiones de diseño:
- **No buscar en cada turno.** Es caro y lento. Buscar cuando la pregunta depende de un dato que
  cambia (precio, norma, clima); responder de conocimiento cargado cuando es criterio técnico
  estable (cómo funciona el rebrote de un pasto no cambió este mes).
- **Citar siempre la fuente** de lo que vino de búsqueda, y distinguirlo de lo que es criterio del
  agente. El usuario tiene que poder saber qué está verificado y qué es opinión.

### Bases de datos especializadas
Por definir cuáles (ver decisión pendiente #6 del README). Candidatos: literatura agropecuaria,
precios de ganado en subasta, datos climáticos históricos, normativa ICA y requisitos sanitarios.

Cada una es una integración con su propio esfuerzo; conviene empezar con una sola y la más usada.

## Construcción

Empezar con **un solo experto bien hecho**, no con nueve mediocres. La plantilla del prompt (rol +
principios + criterio técnico + postura de thought partner + reglas de búsqueda) se valida contra
preguntas reales y solo después se replica al resto del roster.

## Dependencias
- `principios/` (obligatorio)
- Cuenta de Perplexity API
- App 4 para datos de la finca (sin ella los expertos razonan en abstracto)
