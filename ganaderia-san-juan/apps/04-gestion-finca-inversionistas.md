# App 4 — Gestión de finca e inversionistas

**Publicación:** juanchica.com · **Acceso:** interno + portal por inversionista · **Estado:** por construir

> La pieza más grande del portafolio y la que sostiene a las demás: es la **fuente de verdad** de
> los datos que consultan las apps 1, 2 y 3.

## El planteamiento

Software propietario para gestionar la finca y el inventario, con una particularidad que define
toda la arquitectura:

> **Cada animal es el activo que respalda la inversión de un externo.**

De ahí salen dos interfaces sobre la misma base de datos:

1. **Interfaz de manejo (interna)** — operar la finca.
2. **Portal de inversionistas (externo)** — que cada inversionista vea cómo va *su* ganado, con
   confianza y tranquilidad sobre su inversión.

## A — Interfaz de manejo (interna)

- **Inventario animal**: cada animal como registro individual — identificación, categoría, fechas,
  procedencia, potrero actual, estado.
- **Pesajes y ganancia de peso** por animal y por lote. Es el indicador que el inversionista va a
  querer ver.
- **Eventos**: sanitarios, reproductivos, movimientos entre potreros, entradas y salidas.
- **Inventario de potreros** e infraestructura (alimenta la app 3).
- **Costos** imputados por lote o por animal, para poder calcular rendimiento real.
- **Registro en campo desde el celular**, con mala señal. Si capturar un dato es incómodo, no se
  captura, y una base de datos incompleta no le sirve a nadie.

## B — Portal de inversionistas (externo)

Cada inversionista entra y ve **solo sus animales**:

- Qué animales respaldan su inversión, identificados.
- Cómo van: peso actual, ganancia desde que entraron, estado sanitario.
- Dónde están y en qué condiciones (fotos del potrero ayudan más de lo que parece).
- Valorización estimada de su posición.
- Historia y trazabilidad del lote desde que entró.

### El principio que gobierna este portal

**La confianza se construye con transparencia, no con maquillaje.** Un portal que solo muestra
buenas noticias se desmorona el día que haya una mala. Concretamente:

- **Mostrar la fecha del último dato.** Un peso de hace cuatro meses presentado sin fecha es
  engañoso.
- **Distinguir medido de estimado.** Una proyección de valor no puede verse igual que un pesaje.
- **Reportar también lo malo** — mortalidad, un lote que no está ganando peso — con la explicación
  al lado. Así se construye credibilidad.
- **No publicar un dato que no esté sólido.** De ahí que el portal sea la última fase.

## Arquitectura de datos — el punto crítico

La relación **animal ↔ inversión** es la decisión de diseño que hay que acertar desde el principio,
porque rehacerla después con datos productivos es muy caro.

Preguntas que hay que responder antes de escribir el esquema:

- ¿El inversionista es dueño de **animales identificados** o de una **participación en un lote**?
  Son dos modelos de datos distintos.
- ¿Qué pasa cuando un animal **muere**? ¿Lo asume el inversionista, la operación, o hay un seguro
  o un fondo de contingencia?
- ¿Qué pasa cuando un animal se **vende**? ¿Cómo se liquida y cómo se refleja en el portal?
- ¿Se **reinvierte** el producto de la venta en animales nuevos, o se devuelve capital?
- ¿Cómo se reparte la **valorización** entre inversionista y operación?
- ¿Hay un **contrato** por escrito que ya define esto? **Si existe, el modelo de datos debe seguir
  el contrato, no al revés.**

> Esta es una decisión de negocio, no técnica. Hasta que no esté resuelta, no hay que construir la
> app 4 — hay que resolverla primero.

## Consideraciones

- **Auditabilidad.** Todo cambio sobre un animal queda registrado con quién y cuándo. Si un
  inversionista pregunta por qué cambió un número, tiene que haber respuesta.
- **Seguridad y separación.** Un inversionista no puede ver la posición de otro. Esto se diseña
  desde el primer día, no se parcha después.
- **Datos personales y financieros de terceros.** Hay obligaciones legales sobre su tratamiento;
  revisarlas antes de lanzar.
- **Construcción por etapas.** Primero el inventario interno funcionando y con datos confiables.
  El portal externo después. Nunca al revés.

## Dependencias
- Definición de la estructura de inversión (bloqueante absoluto)
- Levantamiento del hato y los potreros
- Mecanismo de autenticación por inversionista
