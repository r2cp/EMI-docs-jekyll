---
layout: default
title: Calibración varianza
nav_order: 2
has_children: false
permalink: /docs/calibracion-varianza
usemathjax: true
---

# Calibración de varianza del proceso de caminata aleatoria del EMI 

Se describe a continuación la propuesta de calibración de caminata aleatoria planteada por Juan Carlos Castañeda para la tendencia de caminata aleatoria del proceso de evaluación de medidas de inflación.

- [Calibración de varianza del proceso de caminata aleatoria del EMI](#calibración-de-varianza-del-proceso-de-caminata-aleatoria-del-emi)
  - [Propuesta de modelado de caminata aleatoria para la evaluación de medidas de inflación (EMI) - 8 de julio de 2020](#propuesta-de-modelado-de-caminata-aleatoria-para-la-evaluación-de-medidas-de-inflación-emi---8-de-julio-de-2020)
    - [Calibración de la varianza](#calibración-de-la-varianza)
  - [Tendencia estocástica en las trayectorias de inflación paramétrica](#tendencia-estocástica-en-las-trayectorias-de-inflación-paramétrica)

## Propuesta de modelado de caminata aleatoria para la evaluación de medidas de inflación (EMI) - 8 de julio de 2020

Se propone que la tendencia estocástica de la inflación, en la EMI, sea aditiva (en vez de multiplicativa).  El propósito de hacer dicha tendencia aditiva es que haya continuidad en su dirección cuando la inflación intermensual (poblacional o muestral) cambie de signo.  

Por ejemplo, si la tendencia estocástica de la inflación (en la forma de una caminata aleatoria que implica la existencia de persistencia serial positiva) es multiplicativa y mayor que uno, cuando la inflación intermensual pasa de ser positiva a ser negativa, entonces el valor grande de la tendencia estocástica hace que se pase de una inflación positiva grande a una inflación negativa grande, perdiéndose continuidad en la persistencia serial positiva que se pretende modelar con la caminata aleatoria.  

En cambio, si la referida tendencia estocástica es aditiva, entonces se preserva la continuidad en dicha tendencia estocástica cuando la inflación intermensual cambia de signo.

En particular, se propone el modelo siguiente:
> $$ z_t = x_t + y_t $$
> en donde $$z_t$$ representa la variación intermensual del IPC en $t$, $x_t$ la variación intermensual del IPC en $t$ sin tendencia estocástica y $y_t$ es el componente aditivo de tendencia estocástica en $t$.

El modelo para la tendencia estocástica aditiva es el de una caminata aleatoria:
$$ y_t = y_{t-1} + \varepsilon_t, \quad y_0 = 0, \quad \varepsilon_t\sim N(0, \sigma_\varepsilon^2) $$

### Calibración de la varianza

Para generar las series de tiempo correspondientes al parámetro poblacional y a las simulaciones muestrales, la variable $y_t$ tiene valor inicial cero y luego evoluciona de acuerdo con su ley de movimiento (caminata aleatoria).  Para este propósito, los valores de los choques estocásticos $t$ se extraen de una distribución normal con media cero y con varianza $\sigma_\varepsilon^2$.

El valor de $\sigma_\varepsilon^2$ se obtiene a partir de los datos históricos observados de inflación de Guatemala, de la manera siguiente:

> $$\sigma_\varepsilon^2 = \text{Var}(\delta_t)$$
> en donde  
> $$\delta_t = \frac{1}{12} \sum_{j=1}^{12} \left(q_{t-j} - q_{t-j-1} \right)$$  
> corresponde a la media móvil de 12 meses de las diferencias en las variaciones intermensuales del IPC $q_t$ del período $t$ en los datos históricos.

Al aplicar este proceso se obtiene la siguiente gráfica de variaciones intermensuales del IPC y sus medias móviles de 12 meses. Como se puede apreciar, la varianza es mucho menor para las medias móviles.  

![Variaciones intermensuales IPC](images/Calibraci%C3%B3n%20varianza%20RW_2020-07-14_154635.png)  

En la siguiente tabla se presentan las estimaciones de varianza y desviación estándar de las variaciones intermensuales del IPC en las dos períodos del IPC (así como en el período completo). Los valores se muestran en puntos porcentuales para las desviaciones estándar. Se puede resaltar que los valores de desviación estándar sin suavizamiento de media móvil parecen ser muy grandes, y por lo tanto, inadecuados para utilizarse en bruto para el proceso de calibración de varianza de la tendencia de caminata aleatoria.

| Período  | Varianza  | Desviación estándar | Varianza media móvil| Desviación estándar media móvil |
|---|---:|---:|---:|---:|
| Base 2000 | 0.2713 | 0.5209 |0.003490 | 0.0591 |
| Base 2010 | 0.2162 | 0.4650 |0.001868 | 0.0432 |
| Período completo | 0.2435 | 0.4935 | 0.002693 | 0.0519 |

Ahora se procederá a computar una señal de ruido blanco utilizando la varianza de la media móvil de 12 meses de las variaciones intermensuales del IPC de la base 2000 y del período completo. A continuación, como ejemplo, se muestra una de las realizaciones:  

![Ruido blanco](images/Calibraci%C3%B3n%20varianza%20RW_2020-07-16_155842.png)  

Como se puede observar, la volatilidad de la señal de ruido blanco utilizando la varianza del período completo ($\text{Var}(\delta_t) = 0.0027$) es ligeramente menor a la volatilidad de la señal de ruido blanco que utiliza la varianza solamente de la base 2000 ($\text{Var}(\delta_t) = 0.0035$). Aunque, en apariencia, la diferencia de volatilidad no parece muy importante.

A continuación se procederá a utilizar la señal de ruido blanco del período completo para computar las trayectorias paramétricas de inflación. Esto permitirá evaluar si la volatilidad calibrada a través de este procedimiento es adecuada, es decir, si permite que la evolución de la tendencia estocástica genere cambios significativos, pero no muy grandes, en la trayectoria de la inflación interanual.

## Tendencia estocástica en las trayectorias de inflación paramétrica

En esta sección se describe cómo quedan los parámetros poblacionales resultantes al utilizar la señal de ruido blanco aditiva calibrada con las variaciones intermensuales del IPC.

En esta figura se aprecia las diferentes componentes de tendencia, los cuales son aahora aditivos en el proceso de cómputo de inflación paramétrica y en el remuestreo.  

![Componentes tendencia](images/Calibraci%C3%B3n%20varianza%20RW_2020-07-16_161402.png)  

Como referencia, se muestran las trayectorias de inflación paramétrica sin tendencia.  

![Trayectorias paramétricas sin tendencia](images/Calibraci%C3%B3n%20varianza%20RW_2020-07-16_160221.png)  

Se muestran las trayectorias de inflación paramétrica utilizando la componente aditiva de tendencia de caminata aleatoria que se muestra en color morado en la figura anterior de componentes de tendencia.  

![Trayectorias paramétricas tendencia aditiva](images/Calibraci%C3%B3n%20varianza%20RW_2020-07-16_160236.png)  

Como se observa, se obtienen trayectorias de inflación paramétrica con tendencia estocástica y moderada volatilidad, por lo que el método de calibración podría considerarse adecuadamente escalado para modelar la varianza del proceso de caminata aleatoria de la tendencia.  
