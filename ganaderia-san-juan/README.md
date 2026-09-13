# Ganadería San Juan — Thought Partner

> **Estado: idea capturada, sin ejecutar.** Este documento existe para no perder el planteamiento
> y para arrancar la ejecución apenas haya computador disponible. Nada de lo que está aquí está
> construido todavía.

## 1. Qué es

**Ganadería San Juan** es la operación ganadera. El **Thought Partner** es la capa de inteligencia
que la acompaña: un conjunto de agentes expertos y aplicaciones propias con las que Juan y su
hermano **piensan, aprenden y retan ideas** antes de decidir.

La distinción importa y define todo el diseño: un thought partner **no ejecuta por ti, piensa
contigo**. No es un asistente que entrega una respuesta y cierra. Es un interlocutor que sostiene
una posición técnica, la argumenta, y te obliga a defender la tuya. El objetivo declarado es
doble:

1. **Aprender** de cada tema con un experto al lado.
2. **Retar cada idea** — la de ellos y la del propio agente.

Un agente que solo valida lo que uno propone falló en su trabajo.

## 2. Dónde se publica

| Qué | Dónde | Por qué |
|-----|-------|---------|
| **Todas las apps del Thought Partner** | **juanchica.com** | Es el dominio propio. Todo lo que se construya vive ahí. |
| Landing de Yuwú / Reserva San Juan de Frías | `jfchica86.github.io/reserva-pauji` (este repo) | Era una pieza pública para compartir; se queda donde está. |

> Pendiente técnico: definir el hosting de juanchica.com y si cada app es una ruta del mismo sitio
> (`juanchica.com/junta`, `juanchica.com/finca`) o despliegues independientes. Ver sección 6.

## 3. El portafolio: cuatro aplicaciones

Cada una tiene su brief propio en `apps/`.

| # | App | Qué hace | Para quién |
|---|-----|----------|------------|
| 1 | **[Mi Junta Asesora](apps/01-junta-asesora.md)** | Sala donde Juan interactúa con la junta asesora de Ganadería San Juan — varios perfiles que deliberan entre sí sobre una decisión | Juan |
| 2 | **[Expertos Thought Partner](apps/02-expertos-thought-partner.md)** | Agentes expertos por dominio, conectados a Perplexity y bases de datos especializadas, que enseñan y retan bajo los principios definidos | Juan y su hermano |
| 3 | **[Rotaciones](apps/03-rotaciones.md)** | Generador de planes de rotación especializados para los potreros reales de la finca | Operación |
| 4 | **[Gestión de finca e inversionistas](apps/04-gestion-finca-inversionistas.md)** | Software propietario de finca e inventario animal + portal donde cada inversionista ve cómo va su ganado | Interno + inversionistas externos |

### Cómo se relacionan

```
        principios/  ← la capa que define el criterio de TODO lo demás
              │
   ┌──────────┼──────────────┬────────────────┐
   │          │              │                │
Junta      Expertos      Rotaciones      Gestión de finca
Asesora    (2)           (3)             (4)
(1)          │              │                │
   │         └──── consultan datos ──────────┘
   │                                          │
   └──── delibera sobre decisiones ───────────┘
                                              │
                                    Portal inversionistas
```

- **Los principios son la base.** Sin ellos, los agentes 1 y 2 son genéricos.
- **La app 4 es la fuente de verdad de los datos.** Los agentes 1, 2 y 3 consultan de ahí; si no,
  opinan sobre una finca imaginaria.
- **La app 3 es un caso especializado de la 2** — puede empezar dentro de ella y separarse después.

## 4. Los principios (capa fundacional — falta escribirlos)

El planteamiento dice que los agentes deben *"operar bajo los principios que yo le enseñé"*. Esos
principios **no están escritos en ningún lado todavía** y son el insumo más importante de todo el
proyecto: son lo que separa a estos agentes de un ChatGPT cualquiera.

Ver `principios/README.md` para el formato y qué hay que capturar.

**Este es el primer trabajo a hacer frente al computador.**

## 5. Ruta de ejecución

- **Fase 0 — Principios.** Escribir la capa fundacional. Bloquea la calidad de todo lo demás.
- **Fase 1 — Un experto, bien hecho.** Construir un solo agente experto (Rotaciones o Financiación)
  con los principios cargados, conexión a Perplexity y postura de thought partner. Probarlo con
  preguntas reales hasta que el criterio se sienta correcto. **No escalar antes de que uno funcione.**
- **Fase 2 — Datos de finca.** Levantar el inventario de potreros y el hato (sección 6 de cada
  brief). Sin esto las apps 3 y 4 no existen y la 2 se queda en teoría.
- **Fase 3 — Gestión de finca.** Construir el núcleo de la app 4: registro de animales con su
  trazabilidad de inversión. Es la pieza con más valor operativo y la que más tiempo toma.
- **Fase 4 — Junta asesora.** Con los principios maduros y los datos cargados, montar la sala de
  deliberación.
- **Fase 5 — Portal de inversionistas.** Se construye sobre la app 4, una vez los datos sean
  confiables. **No se le muestra a un inversionista un dato que no esté sólido.**
- **Fase 6 — Rotaciones como app aparte**, si el uso lo justifica.

## 6. Decisiones pendientes

**Técnicas**
1. **Hosting de juanchica.com** — ¿dónde está hoy el dominio, qué tiene publicado, y sobre qué se
   despliega (Vercel, Netlify, servidor propio)?
2. **¿Un sitio o varios?** Rutas de un mismo proyecto contra despliegues independientes.
3. **¿Repo nuevo?** Este repo (`reserva-pauji`) es el landing de Yuwú. El Thought Partner
   probablemente merece repositorio propio; esta carpeta se mueve allá cuando se decida.
4. **Autenticación.** Las apps 1, 2 y 4 son privadas. El portal de inversionistas necesita login
   por inversionista. Hay que elegir el mecanismo.
5. **Perplexity API** — cuenta, plan y costo por consulta. Definir cuándo un agente busca en vivo y
   cuándo responde con su conocimiento cargado (buscar en cada turno es caro y lento).
6. **Bases de datos especializadas** — ¿cuáles exactamente? (literatura agropecuaria, precios de
   ganado, datos climáticos, normativa ICA). Cada una es una integración distinta.

**De negocio**
7. **Estructura de la inversión por animal.** ¿Qué es legalmente lo que compra el inversionista:
   propiedad del animal, participación en el lote, o un contrato de rendimiento? Esto define el
   modelo de datos de la app 4, no al revés.
8. **Miembros de la junta asesora.** ¿Son perfiles inventados por rol, personas reales modeladas,
   o una mezcla?
9. **¿Qué finca es?** Confirmar si es el predio de San Juan de Frías u otra operación, y si
   Ganadería San Juan y la reserva Yuwú conviven en una misma narrativa o se separan.

## 7. Contenido de esta carpeta

```
ganaderia-san-juan/
├── README.md                              ← este documento
├── principios/README.md                   ← capa fundacional, POR ESCRIBIR
├── apps/
│   ├── 01-junta-asesora.md
│   ├── 02-expertos-thought-partner.md
│   ├── 03-rotaciones.md
│   └── 04-gestion-finca-inversionistas.md
└── agentes/
    ├── PLANTILLA.md                       ← formato para un agente nuevo
    ├── rotaciones.md                      ← brief del experto en rotaciones
    └── financiacion.md                    ← brief del experto en financiación
```
