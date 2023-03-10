---
title: "Introducción a R y a los gráficos en R"
author: "Ricardo Castro"
date: "2023-02-08"
output:
      html_document:
        keep_md: true
---




# "Introducción a R y a los gráficos en R"

## Prerequisites {-}

- Estar interesados en el uso de R.
- Instrucciones de instalación y uso extensas en: [R](https://cran.r-project.org/) and [RStudio](https://www.rstudio.com/).
- No rendirse.



## Instalación del software {-}
Mientras [**R**](https://cran.r-project.org/) es el software colaborativo y de acceso libre, [**RStudio**](https://www.rstudio.com/) es un entorno de desarrollo integrado (IDE) para R, pobablemente 
el más usado. R no es tan amigable como para usarlo sólo. RStudio por otro lado hace que el uso de R sea más sencillo y eficiente, además de integrar software de terceros para su uso con R


### macOS {-}

#### Si ya tiene instalado R y RStudio, actualizalos {-}

* Abre y en la opción de "Help" > "Check for updates". Si hay una versión nueva, actualiza.
* R también puede ser actualizado, al abrir RStudio aparecera su version de R.
  En la página del CRAN puede cotejar la version que tiene con la más actual, puede descargar e instalarm the [CRAN website](https://cran.r-project.org/bin/macosx/).

#### Si no tienes R and RStudio instalados {-}

* Descargue R
  the [CRAN website](http://cran.r-project.org/bin/macosx).
* Seleccione el arhivo de extrnesión`.pkg`  del alultima verisón
* Descargue para instalar
* Vaya a la pagina de [RStudio download page](https://posit.co/download/rstudio-desktop/)
* Selecciones el ejecutable para su sistema
* En su carpeta de descargas doble click sobre el archivo de RStudio para instalar

### Windows {-}

#### Si ya tiene instalado R y RStudio, actualizalos {-}

* Siga las mismas instrucciones que en el parrafo anterior. Si hay nuevas versiones, aculaice R y RStudio.
* Vea si la ultima versión de R es la que ud. tiene. Vaya a 
  the [CRAN website](https://cran.r-project.org/bin/windows/base/) y cheque la versión. Ud puede desinstalar con sus herramientas de gestion de windows.


#### Si no tienes R and RStudio instalados {-}

* Descargue Rde
  the [CRAN website](https://cran.r-project.org/) para sus sistema, extensión ".exe".
* Doble click en archivo e instale.
* Para RStudio, vaya a la pagina de [RStudio download page](https://posit.co/download/rstudio-desktop/)
* Selecciones el ejecutable para su sistema
* En su carpeta de descargas doble click sobre el archivo de RStudio para instalar.



### GNU/Linux {-}

* El tran tiene instrucciones para las distintas distribuciones, revise e instale [CRAN](https://cloud.r-project.org/bin/linux). Se recomienda usar su gestor de paquetes para actualizar  (e.g., for Debian/Ubuntu corra
  `sudo apt-get install r-base`, and for Fedora `sudo yum install R`), pero suele suceder que esta version esté desactualizada
* vaya a [RStudio download page](https://posit.co/download/rstudio-desktop/)
* Seleccione la version de su sistema e instale según sea pertinente para su distribución (e.g., with Debian/Ubuntu `sudo dpkg -i
  rstudio-x.yy.zzz-amd64.deb` en la terminal).


## Acknowledgements {-}
Una fracción de este material es una adaptación de https://cengel.github.io/R-intro/


[Cheat sheet Rmarkdown](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)

[Cheat sheet Rmarkdown-Español](https://www.ic.fcen.uba.ar/materias/datos/material/rmarkdown-spanish.pdf)

[Guía rápida Rmarkdown](https://raw.githubusercontent.com/rstudio/cheatsheets/main/translations/spanish/rmarkdown_es.pdf)


# Getting Started with R {#gettingstarted}

> Aprendizaje
>
> * Objetos de R: creación y asignación de valores
> * Usar los comentarios en los scripts.
> * Usar objetos y valores para operaciones aritmeticas.
> * Crear e invocar (llamar funciones).
> * Revisión de objetos y vectores.
> * Obtener subconjuntos de datos de vectores.
> * Definir datos perdidos (NAs).
> * Uso de la interfaz de [Rstudio]() 
> * Invocar Ayuda de [R]()
> * Buscar ayuda sobre problemas y busqueda de soluciones.
> * Descargar, instalar y cargar paquete de R.

------------


---


## Objetos de R: creación y asignación de valores

Definamos _valores_ y después poder asignarlos a _objetos_, mediante el operador de asignación `<-`, Ejemplo:


```r
peso_kg <- 55
```

`<-` El operador de asignación es en realidad una flecha depentidndo del sentido de la flecha se asignaran los valores, en el ejemplo anterior la flecha va de izquierda a derecha, entonces el objeto definido es el de la izquierda "pero_kg", entonces el valor 55 **se guarda dentro de** `peso_kg`.  También puede usar el simbolo `=`
pero no en todos los casos,porque hay [pequeñas](http://blog.revolutionanalytics.com/2008/12/use-equals-or-arrow-for-assignment.html) [diferencias](https://web.archive.org/web/20130610005305/https://stat.ethz.ch/pipermail/r-help/2009-March/191462.html) en la sintaxis y es mejor usar  `<-` para evitar cualquier conflicto.

In RStudio, typing <kbd>Alt</kbd> + <kbd>-</kbd> (push <kbd>Alt</kbd> at the
same time as the <kbd>-</kbd> key) will write ` <- ` in a single keystroke.

Hay ciertas reglas:

- cualquier nombre pueden recibir los objetos, la simpleza es compensada `x`, `current_temperature`, or
`subject_id`. 
- Nombres no tan largos.
- No se recomiendan espacios, ni caráctres especiales.
- No **no pueden empezar** con números (`2x` es inválido, `x2` está bien). 
- R es sensible a mayusculas y R no reconoce si no se escribe el nombre identico.
- There are some names that
cannot be used because they are the names of fundamental functions in R (e.g., `if`, `else`, `for`, see
[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/Reserved.html) for a complete list). In general, even if it is allowed, it's best to not use other function names (e.g., `c`, `T`, `mean`, `data`, `df`, `weights`). If in doubt, check the help to see if the name is already in use. 
- It's also best to
avoid dots (`.`) within a variable name as in `my.dataset`. There are many
functions in R with dots in their names for historical reasons, but because dots have a special meaning in R (for methods) and other programming languages, it is best to avoid them. 
- It is also recommended to use *nouns for variable names*, and
*verbs for function names*. 
- It's important to be consistent in the styling of your code (where you put spaces, how you name variables, etc.). Using a consistent
coding style makes your code clearer to read for your future self and your
collaborators.  
In R, three popular style guides
are
[Google's](https://google.github.io/styleguide/Rguide.xml),
[Jean Fan's](http://jef.works/R-style-guide/) and
the [tidyverse's](http://style.tidyverse.org/). The tidyverse's is very comprehensive
and may seem overwhelming at first. You can install the 
[**`lintr`**](https://github.com/jimhester/lintr) to automatically check for issues 
in the styling of your code.


When assigning a value to an object, R does not print anything. You can force R to print the value by using parentheses or by typing the object name:


```r
weight_kg <- 55    # doesn't print anything
(weight_kg <- 55)  # but putting parenthesis around the call prints the value of `weight_kg`
```

```
## [1] 55
```

```r
weight_kg          # and so does typing the name of the object
```

```
## [1] 55
```

Now that R has `weight_kg` in memory, we can do arithmetic with it. For
instance, we may want to convert this weight into pounds (weight in pounds is 2.2 times the weight in kg):


```r
2.2 * weight_kg
```

```
## [1] 121
```

We can also change a variable's value by assigning it a new one:


```r
weight_kg <- 100
2.2 * weight_kg
```

```
## [1] 220
```

This means that assigning a value to one variable does not change the values of
other variables.  For example, let's store the weight in pounds in a new
variable, `weight_lb`:


```r
weight_lb <- 2.2 * weight_kg
```

and then change `weight_kg` to 50.


```r
weight_kg <- 50
```

> <h3>Challenge</h3>
> 
> What do you think is the current content of the object `weight_lb`? 110 or 220?





















## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Including Plots

You can also embed plots, for example:

![](intro_r_and_plots_files/figure-html/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.


 
## Introducción a objetos de R 

Vamos a probar algunos comandos de R para objetos

### Buscando ayuda


```r
?lm
```
 con help
 

```r
help(objects)
```
 
### vectores y  listas

vector v

```r
a<-c(2,1,3,4)
a
```

```
## [1] 2 1 3 4
```


```r
getwd() #para ver mi directorio de trabajo
```

```
## [1] "/home/rcastro/Documentos/intro_R_and_plots"
```

```r
setwd("/home/rcastro/Documentos/intro_R_and_plots") # es por si requiero configurar mi directorio
```
Todo embebido
