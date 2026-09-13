# Principios — la capa fundacional

> **POR ESCRIBIR.** Este es el insumo más importante de todo el proyecto y el único que nadie más
> puede producir.

## Por qué esto va primero

El planteamiento del Thought Partner dice que los agentes deben *"operar bajo los principios que yo
le enseñé"*. Ahí está la diferencia entre este sistema y cualquier chatbot: el conocimiento técnico
del mundo es público y un modelo ya lo tiene. **El criterio propio no.**

Sin principios escritos, cada agente responde con el promedio de lo que se ha publicado en internet
sobre ganadería. Con principios escritos, responde desde una manera particular de entender el
negocio, la tierra y el riesgo — y puede retar una idea *desde algún lado*, que es lo que hace útil
a un thought partner.

Todo lo demás (apps, integraciones, interfaces) se puede reconstruir. Esto no.

## Qué hay que capturar

Tres capas, de lo general a lo específico:

### 1. Principios rectores
Las convicciones que atraviesan todas las decisiones, independientes del tema.
*Ejemplo de la forma que tienen:* "la tierra se deja mejor de como se recibió", "no nos endeudamos
para crecer más rápido de lo que el suelo aguanta", "si no lo podemos medir, no lo afirmamos
frente a un inversionista".

### 2. Criterios por dominio
Cómo se aplica lo anterior en cada tema: rotaciones, financiación, sanidad, comercial.
*Ejemplo:* "antes de comprar suplemento se revisa si el problema es de manejo del pastoreo".

### 3. Reglas duras
Lo que no se hace nunca y lo que se hace siempre. Un agente puede discutir un criterio, pero no
puede pasar por encima de una regla dura sin decirlo explícitamente.

## Cómo capturarlos (método sugerido)

No hay que sentarse a redactar filosofía. La forma más rápida:

1. **Entrevista.** Una conversación de una hora donde Juan explica cómo tomó tres o cuatro
   decisiones reales de la finca y por qué. Los principios salen de las razones, no de la teoría.
2. **Extracción.** De esa conversación se destilan los principios en forma de afirmaciones cortas.
3. **Validación.** Juan corrige; su hermano también, porque los va a usar.
4. **Versionado.** Quedan en este repo como archivos. Cambian con el tiempo y ese historial importa.

## Cómo los usan los agentes

Los principios se cargan en el prompt de sistema de **todos** los agentes del Thought Partner. No
son sugerencias: son el marco desde el que el agente argumenta.

Y, crítico para la postura de thought partner: **el agente debe poder señalar cuando una idea de
Juan contradice sus propios principios.** Ese es probablemente su uso más valioso.

## Archivos previstos

```
principios/
├── README.md            ← este documento
├── rectores.md          ← POR ESCRIBIR
├── por-dominio.md       ← POR ESCRIBIR
└── reglas-duras.md      ← POR ESCRIBIR
```
