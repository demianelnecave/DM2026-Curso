---
title: No1 - Introducción
---

## Introducción

**Fecha:** 08/04/2026

**Material:** [Slides de la clase](../slides/2026-04-08.pdf)

:::{iframe} https://www.youtube.com/embed/LDp4yZyDHdQ
:width: 100%
:::


En esta clase se introducen los temas que se van a estudiar durante la cursada.
Trataremos de entender con ecuaciones físicas y herramientas de aprendizaje automático cuál es la dinámica de distintos sistemas físicos.
Las aplicaciones de la materia van a estar motivadas por la geofísica.

## Motivación

Comprender y predecir el comportamiento de sistemas físicos complejos es uno de los grandes desafíos de la computación científica moderna.
Como hilo conductor de la clase nos enfocaremos en el estudio de **glaciares** como ejemplo de sistema dinámico. 

:::{note} ¿Qué es un glaciar?

Un glaciar es un cuerpo persistente de hielo que evoluciona dinámicamente a lo largo del tiempo.

Aunque pueda parecer una estructura estática, un glaciar fluye lentamente bajo el efecto de la gravedad y responde a cambios climáticos y ambientales.
:::

### Importancia de los glaciares

* **Reguladores del clima a nivel global**
    - Influencia sobre el nivel del mar.
    - Reflexión de radiación solar.
    - Relación con el cambio climático.

* **Recursos hídricos**
    - Reserva de agua dulce.
    - Regulación del suministro de agua.

* **Componente cultural**
    - Impacto social y económico.
    - Importancia turística y ecológica

### Dinámica de un glaciar

Los glaciares son sistemas dinámicos.
Aunque estén formados por hielo, fluyen lentamente de manera similar a un río.
Su movimiento ocurre principalmente debido a la gravedad.

Existen distintos mecanismos que explican este movimiento.

- **Deformación interna:**  
  El hielo puede modelarse como un medio viscoso que se deforma internamente.
  Las capas superiores suelen moverse más rápido que las inferiores.

- **Deslizamiento:**  
  El glaciar interactúa con la roca subyacente mediante fuerzas de fricción.
  Dependiendo de estas interacciones, el hielo puede quedar adherido o deslizarse sobre la superficie.

Dado que los glaciares son sistemas dinámicos, existen leyes físicas que describen su evolución.

### ¿Cómo se modela un glaciar?

El modelado de glaciares combina física, matemática y computación.
Las ecuaciones que describen estos sistemas suelen ser complejas y, en general, no poseen soluciones analíticas exactas.
Por esta razón, es necesario utilizar métodos numéricos y simulaciones computacionales para aproximar sus soluciones.


Para calibrar los parámetros de las ecuaciones que describen la dinámica de un glaciar se utilizan distintas fuentes de datos.

1. **Registros históricos:**  
   por ejemplo mapas, dibujos y pinturas históricas.

2. **Observaciones in-situ:**  
   mediciones directas realizadas sobre el glaciar en su entorno natural.

3. **Observaciones satelitales:**  
   han revolucionado las Ciencias de la Tierra en las últimas décadas.
   Permiten obtener grandes volúmenes de datos observacionales.

4. **Paleogeografía:**  
   permite reconstruir el comportamiento histórico de glaciares a partir de evidencia geológica.

## La revolución de la IA

En los últimos años, distintos avances tecnológicos impulsaron el uso de técnicas de Inteligencia Artificial en Ciencias de la Tierra.

- **Volumen de datos:**  
  todo algoritmo de Inteligencia Artificial requiere grandes cantidades de datos.
  Existen alrededor de 280.000 glaciares en el mundo.
  Además, las observaciones satelitales generan grandes volúmenes de información.

- **Capacidad de cómputo:**  
  actualmente se dispone de hardware con gran capacidad de procesamiento.

- **Algoritmos y software:**  
  el desarrollo de herramientas y bibliotecas de código abierto facilitó la aplicación de modelos de IA.

Todos estos factores permiten aplicar técnicas de Inteligencia Artificial al modelado de glaciares.
Estos avances permiten combinar modelos físicos tradicionales con herramientas modernas de aprendizaje automático.

## ¿Física o Datos?

Pondremos en práctica lo que se conoce como **modelado híbrido**.
El modelado híbrido combina modelos físicos tradicionales con herramientas modernas de aprendizaje automático.

```{figure} figures/ModeladoHibrido.png
---
width: 90%
name: fig-hybrid-modeling
---
Relación entre modelos físicos, modelos basados en datos y modelado híbrido.
```

:::{important} Más allá de los glaciares

Las ideas presentadas en esta clase no son exclusivas del modelado de glaciares.

La combinación de modelos físicos, métodos numéricos, datos observacionales y herramientas de aprendizaje automático aparece en numerosas disciplinas científicas e ingenieriles.

Algunos ejemplos incluyen:
- predicción climática,
- dinámica de fluidos,
- oceanografía,
- y sistemas complejos en general.

El modelado híbrido es actualmente una de las estrategias más utilizadas en computación científica moderna.
:::

## Objetivo de la materia

* Desarrollar y entender metodología que nos permita asimilar datos (heterogéneos, irregulares) a nuestros modelos físicos.
    1. Entender mejor la física del sistema que estamos tratando de modelar.
    2. Mejorar capacidad predictiva de los modelos.

* Desarrollar un marco estadístico para definir dichos problemas.

* Desarrollar software que nos permita realizar esta tarea de manera eficiente y accesible.

* Tener un marco conceptual para pensar en problemas donde leyes físicas y aprendizaje automático hablen el mismo lenguaje.

:::{important} Software Abierto

Vamos a hacer énfasis en software abierto

1. Ciencia abierta y colaborativa

2. Reproducibilidad y replicabilidad de resultados

3. Accesibilidad a recursos y metodología sin limitación de capacidad de computo
:::
---
## Introducción a Physics-Informed Machine Learning (PIML)
El **PIML** es una disciplina donde convergen tres conceptos principales:
* **Modelado físico**: ecuaciones diferenciales que modelan la física del problema.
* **Aprendizaje automático**: algoritmos de *machine learning*.
* **Simulaciones numéricas**: para resolver las ecuaciones diferenciales ya mencionadas.
```{figure} figures/venn-diagram-piml.png
---
width: 60%
name: fig-piml-diagram
---
Caracterización del PIML a partir de la intersección entre el modelado físico, aprendizaje automático y simulaciones numéricas.
```
## Machine Learning: ¿es una caja negra de algoritmos?
1. Tiene poca interpretabilidad, no sabemos cómo aprende.
2. No extrapola bien fuera de los datos entrenados.
3. Es difícil de implementar.

Bajo esas críticas se fundamenta la idea de apoyarnos en leyes físicas a la hora de hacer uso del aprendizaje automático.
:::{note} Ejemplo: oscilador armónico amortiguado
Se pueden ver diferencias a la hora de entrenar una red neuronal **sin** restricciones físicas ({numref}`fig-nn`) y **con** restricciones físicas ({numref}`fig-pinn`).
```{figure} figures/nn.png
---
width: 60%
name: fig-nn
---
Aproximación de la solución del problema del oscilador armónico amortiguado utilizando aprendizaje automático entrenado en los puntos naranjas de la curva.
```
```{figure} figures/pinn.png
---
width: 60%
name: fig-pinn
---
Aproximación de la solución del problema del oscilador armónico amortiguado usando PIML entrenado en los puntos naranjas de la curva.
```
