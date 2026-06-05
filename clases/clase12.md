---
title: No12 - Programación Diferencial Pt2
---

# Programación Diferenciable: Métodos Forward Pt2

**Fecha:** 01/06/2026

:::{iframe} https://www.youtube.com/embed/hlUUiCIZ_mE
:width: 100%
:::

Estas notas prosiguen la temática de {term}`Programación diferenciable` de la clase pasada, retomando la introducción a {term}`Diferenciación automática` (*Automatic Differentation (AD)*).
En particular, comenzamos con una implementación de *AD* en Julia, haciendo uso de los {term}`números duales`.

## Números duales

Se define a los números duales como una extensión de los reales, comenzando por definir a $\epsilon$ número abstracto cumpliendo

$$
\epsilon^{2} = 0\quad ;\quad \epsilon \neq 0 
$$

y escribiendo a todo número dual como 

$$
x_{\epsilon} = x_1 + \epsilon x_2
$$
en donde a $x_1$ será el *valor* de $x_{\epsilon}$ y $x_2$ será su *derivada*.

En lo que a la *AD* respecta, los números duales son una manera muy fácil y directa de implementarla en un lenguaje de programación con herramientas de POO como lo es Julia.

```julia
@ksdef struct DualNumber{F <: AbstractFloat}
            value: F
            derivative: F
end
```
Queremos ser capaces de operar sobre los números duales, sumar, multiplicar, aplicar funciones elementales.
Una de las cosas buenas de Julia es su simplicidad a la hora de extender operaciones a nuevas estructuras de datos.

```julia
#Define operations on dual numbers
function Base.:(+)(a::DualNumber, b::DualNumber)
    res_value = a.value + b.value
    res_derivative = a.derivative + b.derivative
    return DualNumber(res_value, res_derivative)
end

function Base.:(*)(a::DualNumber, b::DualNumber)
    res_value = a.value * b.value
    res_derivative = a.value * b.derivative + a.derivative * b.value 
    return DualNumber(res_value, res_derivative)
end
```
Esto nos va a permitir instanciar los números duales y operar sobre ellos, trasladando siempre en la *parte dual* la derivada correspondiente a la ejecución de las operaciones.




