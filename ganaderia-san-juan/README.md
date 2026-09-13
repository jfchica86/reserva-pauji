# Ganadería San Juan — Farm Partner

> **Estado: idea capturada, sin ejecutar.** Este documento existe para no perder el planteamiento
> y para arrancar la ejecución apenas haya computador disponible. Nada de lo que está aquí está
> construido todavía.

## 1. Qué es

Una nueva sección —**Ganadería San Juan**— dentro del universo San Juan de Frías / Yuwú, donde se
despliega un **Farm Partner**: un equipo de agentes de IA especializados que acompañan la operación
ganadera como si fueran socios técnicos permanentes.

No es un chatbot general. Es un conjunto de agentes **expertos por dominio**, cada uno con su propio
contexto, sus datos y su criterio, que responden preguntas concretas de la finca y proponen
decisiones.

## 2. El roster de agentes

Los dos primeros son los que se nombraron explícitamente; el resto son candidatos naturales para
una operación ganadera y están listados para priorizarlos después.

| # | Agente | Dominio | Prioridad |
|---|--------|---------|-----------|
| 1 | **Rotaciones** | Pastoreo rotacional: aforo, carga animal, días de ocupación y descanso, división de potreros, recuperación de praderas | Alta (definido) |
| 2 | **Financiación** | Estructura de capital, crédito agropecuario (Finagro, bancos), flujo de caja, evaluación de inversiones, subsidios e incentivos | Alta (definido) |
| 3 | Nutrición y suplementación | Balance de dieta, sales mineralizadas, suplementación en época seca, bancos de forraje | Por definir |
| 4 | Sanidad | Calendario sanitario, vacunación obligatoria, parasitismo, bioseguridad | Por definir |
| 5 | Reproducción y genética | Índices reproductivos, IATF, selección de reemplazos, cruces | Por definir |
| 6 | Costos y márgenes | Costo por kilo producido, punto de equilibrio, indicadores por lote | Por definir |
| 7 | Agua y clima | Aforo de fuentes, bebederos, estacionalidad, pronóstico y planeación de sequía | Por definir |
| 8 | Trazabilidad y cumplimiento | Registro ICA, guías de movilización, requisitos de exportación, cero deforestación | Por definir |
| 9 | Comercial | Momento y canal de venta, precios de referencia, negociación | Por definir |

> Los agentes deben poder **hablarse entre sí**: rotaciones necesita saber qué dice agua y clima;
> financiación necesita los números de costos y márgenes.

## 3. Arquitectura propuesta

Tres piezas, de la más simple a la más ambiciosa. Se puede arrancar por la primera y subir.

1. **Subagentes de Claude Code** (`.claude/agents/*.md`) — cada experto es un archivo con su prompt
   y sus herramientas. Lo más rápido de montar; sirve para validar los prompts y el criterio de cada
   agente antes de invertir en producto.
2. **Skills** (`.claude/skills/*/SKILL.md`) — los procedimientos repetibles (calcular un aforo,
   armar un plan de rotación, evaluar un crédito) quedan como habilidades reutilizables.
3. **Producto propio** — una interfaz sobre el Claude Agent SDK con los datos de la finca cargados,
   accesible desde el celular en el campo. Etapa posterior.

## 4. Datos que hay que reunir (bloqueante para que los agentes sirvan)

Un agente experto sin datos de la finca es un agente genérico. Antes o durante la construcción hay
que levantar:

- [ ] Mapa y polígono de potreros con áreas (hectáreas) y tipo de pasto por potrero
- [ ] Inventario del hato: número de animales, categorías, pesos, edades
- [ ] Histórico de rotaciones si existe: fechas de entrada y salida por potrero
- [ ] Fuentes de agua y su ubicación por potrero
- [ ] Estructura de costos actual y estados financieros básicos
- [ ] Régimen de lluvias de la zona (estacionalidad)
- [ ] Obligaciones sanitarias y de registro vigentes

## 5. Ruta de ejecución

- **Fase 0 — Definición.** Cerrar las preguntas abiertas de la sección 6.
- **Fase 1 — Dos agentes.** Construir Rotaciones y Financiación como subagentes, probarlos con
  preguntas reales de la finca y ajustar sus prompts.
- **Fase 2 — Datos.** Cargar la información de la sección 4 en un formato que los agentes puedan
  consultar.
- **Fase 3 — Roster completo.** Priorizar y construir los agentes restantes.
- **Fase 4 — Sección web.** Publicar Ganadería San Juan en el sitio, en la línea visual de Yuwú
  (Cormorant Garamond + Jost, paleta del suelo), bilingüe ES/EN como el resto del landing.
- **Fase 5 — Producto.** Interfaz propia con acceso desde el campo.

## 6. Preguntas abiertas

1. **"Farm Partner"** — el dictado por voz llegó como *"fat partner"*; se interpretó como **Farm
   Partner**. Confirmar el nombre real del concepto.
2. **¿Dónde vive la sección web?** Este repo publica en `jfchica86.github.io/reserva-pauji`, no en
   juanchica.com. Definir si Ganadería San Juan es una sección de este landing, un sitio aparte, o
   una sección de juanchica.com (otro repo).
3. **¿Para quién es?** ¿Uso interno de la operación, o producto/servicio que se le ofrece a otros
   ganaderos?
4. **Relación con la reserva.** Yuwú es conservación; Ganadería San Juan es producción. ¿Conviven
   en la misma narrativa (ganadería regenerativa junto a la reserva) o se separan?
5. **¿Qué finca es?** Confirmar si es el predio de San Juan de Frías o una operación distinta.

## 7. Contenido de esta carpeta

```
ganaderia-san-juan/
├── README.md              ← este documento
└── agentes/
    ├── PLANTILLA.md       ← formato para definir un agente nuevo
    ├── rotaciones.md      ← brief del agente de Rotaciones
    └── financiacion.md    ← brief del agente de Financiación
```
