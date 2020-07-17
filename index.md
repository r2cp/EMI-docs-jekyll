---
layout: default
title: Inicio
nav_order: 1
description: "El esquema de evaluación de medidas de inflación (EMI) es un proyecto del Banco de Guatemala para evaluar, bajo un enfoque de estadística inferencial, la eficiencia de diferentes medidas en estimar la inflación."
permalink: /
last_modified_date: 2020-07-17T12:00:00-0600
usemathjax: true
---

# Evaluación de medidas de inflación de Guatemala
{: .fs-9 }

En este repositorio se encuentra publicada la documentación respecto al proyecto de evaluación de medidas de inflación (EMI).
{: .fs-6 .fw-300 }

[Introducción](#introducción){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [Ver en GitHub](https://github.com/DIE-BANGUAT/EMI){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Introducción

En el Índice de Precios al Consumidor (IPC) de la mayoría de países hay rubros cuyos precios experimentan muy alta volatilidad. Esto afecta a la medida de inflación, causando variaciones en el IPC que no necesariamente reflejan cambios en la inflación, entendida ésta como un incremento generalizado en los precios.  

Los bancos centrales han utilizado diferentes medidas de inflación subyacente para enfrentar este problema, por lo que utilizar un procedimiento de evaluación de medidas de inflación es de gran relevancia para discernir entre ellas, aquéllas que tienen mayor contenido informativo en términos macroeconómicos.  

Entendiendo una medida de inflación como un estimador muestral de una variable no observada (la inflación), y bajo el entendido de que es posible obtener diferentes estimadores muestrales para darle seguimiento al comportamiento generalizado de los precios, pueden surgir las preguntas: ¿qué tan bueno es un determinado estimador muestral?, ¿cuáles son sus características generales de precisión y sesgo?, y finalmente, ¿cómo es posible evaluar si un estimador posee algunas características estadísticas deseables para sus usuarios? Estas preguntas no son fáciles de responder solamente con la información que se tiene disponible, pues la verdadera inflación permanecerá siempre como un fenómeno no observable.  

En este trabajo se utiliza una aproximación que pretende responder a estas interrogantes utilizando una técnica de simulación de *bootstrapping* y datos históricos de la canasta del IPC de Guatemala.
