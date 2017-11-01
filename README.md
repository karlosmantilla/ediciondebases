
# Edición de Bases de Datos

En primer lugar, seleccionemos y revisemos el directorio de trabajo
Recordemos que se puede hacer manualmente mediante el menú contextual o usando la línea setwd() para seleccionar el directorio de trabajo.
Para verificar el directorio se emplea la línea getwd():


```R
getwd()
```


'C:/Users/UIS'


Ahora, podemos verificar los objetos existentes


```R
ls()
```





Vamos a crear la base de datos con la que vamos a trabajar.
En en ejemplo, se busca saber qué tanto difiere la opinión de hombres y mujeres sobre la forma como se dirigen las organizacione. Se registran datos básicos y las respuestas en un cuestionario. Las respuestas se registran en una escala de valor:
1. Completamente en desacuerdo
2. En desacuerdo
3. Ni lo uno ni lo otro
4. De acuerdo
5. Completamente de acuerdo

El ejemplo se basa en la respuesta de 5 gerentes. Los resultados son:

|gerente|     fecha|pais|genero|edad|q1|q2|q3|q4|q5|
|-------|----------|----|------|----|--|--|--|--|--|
|    1  |  10/24/08| US |     M|  32| 5|4 |5 |5 |5 |
|    2  |  10/28/08| US |     F|  45| 3|5 |2 |5 |5 |
|    3  |10/01/2008| UK |     F|  25| 3|5 |5 |5 |2 |
|    4  |10/12/2008| UK |     M|  39| 3|3 |4 |NA|NA|
|    5  | 5/01/2009| UK |     F|  99| 2|2 |1 |2 |1 |


```R
gerente <- c(1, 2, 3, 4, 5)
fecha <- c("10/24/08", "10/28/08", "10/1/08", "10/12/08", "5/1/09")
pais <- c("US", "US", "UK", "UK", "UK")
genero <- c("M", "F", "F", "M", "F")
edad <- c(32, 45, 25, 39, 99)
q1 <- c(5, 3, 3, 3, 2)
q2 <- c(4, 5, 5, 3, 2)
q3 <- c(5, 2, 5, 4, 1)
q4 <- c(5, 5, 5, NA, 2)
q5 <- c(5, 5, 2, NA, 1)
liderazgo <- data.frame(gerente, fecha, pais, genero, edad,
q1, q2, q3, q4, q5, stringsAsFactors=FALSE)
liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td></tr>
</tbody>
</table>



##  Creando una nueva variable

Para crear una nueva variable se usa la línea ```variable<-expresion``` donde se puede definir mediante cualquier expresión matemática una nueva variable. Vale aclarar que este procedimiento es para crear nuevas variables a partir de las existentes

¿Cuáles on las expresiones posibles?

| Expresion | Significado    |
|-----------|----------------|
|     +     |         Suma   |
| -         |         Resta  |
| *         | Multiplicación |
| /         |       División |
| ^ o **    | Exponenciación |
| x%%y      |Módulo (x mod y)|
| x%/%y     | División Entera|

Creemos un ```dataframe```


```R
mydata<-data.frame(x1 = c(2, 2, 6, 4), x2 = c(3, 4, 2, 8))
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th></tr></thead>
<tbody>
	<tr><td>2</td><td>3</td></tr>
	<tr><td>2</td><td>4</td></tr>
	<tr><td>6</td><td>2</td></tr>
	<tr><td>4</td><td>8</td></tr>
</tbody>
</table>



Ahora, añadamos la variable suma (```sumx```) y media (```meanx```)


```R
mydata$sumx <- mydata$x1 + mydata$x2
mydata$meanx <- (mydata$x1 + mydata$x2)/2
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th><th scope=col>sumx</th><th scope=col>meanx</th></tr></thead>
<tbody>
	<tr><td>2  </td><td>3  </td><td> 5 </td><td>2.5</td></tr>
	<tr><td>2  </td><td>4  </td><td> 6 </td><td>3.0</td></tr>
	<tr><td>6  </td><td>2  </td><td> 8 </td><td>4.0</td></tr>
	<tr><td>4  </td><td>8  </td><td>12 </td><td>6.0</td></tr>
</tbody>
</table>



Más opcines con los mismo resultados:


```R
mydata<-data.frame(x1 = c(2, 2, 6, 4), x2 = c(3, 4, 2, 8))
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th></tr></thead>
<tbody>
	<tr><td>2</td><td>3</td></tr>
	<tr><td>2</td><td>4</td></tr>
	<tr><td>6</td><td>2</td></tr>
	<tr><td>4</td><td>8</td></tr>
</tbody>
</table>




```R
attach(mydata)
mydata$sumx <- x1 + x2
mydata$meanx <- (x1 + x2)/2
detach(mydata)
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th><th scope=col>sumx</th><th scope=col>meanx</th></tr></thead>
<tbody>
	<tr><td>2  </td><td>3  </td><td> 5 </td><td>2.5</td></tr>
	<tr><td>2  </td><td>4  </td><td> 6 </td><td>3.0</td></tr>
	<tr><td>6  </td><td>2  </td><td> 8 </td><td>4.0</td></tr>
	<tr><td>4  </td><td>8  </td><td>12 </td><td>6.0</td></tr>
</tbody>
</table>




```R
mydata<-data.frame(x1 = c(2, 2, 6, 4), x2 = c(3, 4, 2, 8))
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th></tr></thead>
<tbody>
	<tr><td>2</td><td>3</td></tr>
	<tr><td>2</td><td>4</td></tr>
	<tr><td>6</td><td>2</td></tr>
	<tr><td>4</td><td>8</td></tr>
</tbody>
</table>




```R
mydata <- transform(mydata,
sumx = x1 + x2,
meanx = (x1 + x2)/2)
mydata
```


<table>
<thead><tr><th scope=col>x1</th><th scope=col>x2</th><th scope=col>sumx</th><th scope=col>meanx</th></tr></thead>
<tbody>
	<tr><td>2  </td><td>3  </td><td> 5 </td><td>2.5</td></tr>
	<tr><td>2  </td><td>4  </td><td> 6 </td><td>3.0</td></tr>
	<tr><td>6  </td><td>2  </td><td> 8 </td><td>4.0</td></tr>
	<tr><td>4  </td><td>8  </td><td>12 </td><td>6.0</td></tr>
</tbody>
</table>



## Recodificar una variable


Algunas veces requerimos recodificar una variable, por ejemplo, cuando debemos llevar el registro de las edades a una variable categórica agrupada por rangos. Los operadores básicos que podemos emplear son:

| Operador |           Significado          |
|----------|--------------------------------|
|<         |                     Menor que  |
| <=       |               Menor o igual a  |
| >        |                     Mayor que  |
| >=       |         Mayor o igual igual a  |
| ==       |           Exactamante igual a  |
| !=       |                    No igual a  |
| !x       |                       No es x  |
| x $|$ y	   |                         x o y  |
| x & y	   |                         x y y  |
| isTRUE(x)|   Comprueba si x es verdadero  |

Creemos un objeto de respaldo para trabajar con los datos de ```liderazgo```:


```R
data<-liderazgo; liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td></tr>
</tbody>
</table>




```R
liderazgo$edad[liderazgo$edad == 99] <- NA
liderazgo$edadcat[liderazgo$edad > 75] <- "Elder"
liderazgo$edadcat[liderazgo$edad >= 55 &
liderazgo$edad <= 75] <- "Middle Aged"
liderazgo$edadcat[liderazgo$edad < 55] <- "Young"
liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th><th scope=col>edadcat</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td><td>Young   </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td><td>Young   </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td><td>Young   </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td><td>Young   </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>NA      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td><td>NA      </td></tr>
</tbody>
</table>



Más opciones:


```R
liderazgo<-data
liderazgo <- within(liderazgo,{
edadcat <- NA
edadcat[edad > 75] <- "Elder"
edadcat[edad >= 55 & edad <= 75] <- "Middle Aged"
edadcat[edad < 55] <- "Young" })
liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th><th scope=col>edadcat</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td><td>Young   </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td><td>Young   </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td><td>Young   </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td><td>Young   </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td><td>Elder   </td></tr>
</tbody>
</table>



## Renombrar una Variable

En ocasiones requerimos cambiar los nombres de las variables por unos más descriptivos o de más fácil identificación. En el ejemplo de liderazgo, vamos a cambiar el nombre de la variable ```fecha``` por ```testDate``` y a las variables que reprentan las respuestas (```q_i```) por la expresión ```item_i```


```R
liderazgo<-data
names(liderazgo)[2] <- "testDate"
names(liderazgo)[6:10] <- c("item1", "item2",
"item3", "item4", "item5")
liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>testDate</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>item1</th><th scope=col>item2</th><th scope=col>item3</th><th scope=col>item4</th><th scope=col>item5</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td></tr>
</tbody>
</table>



Con la librería ```plyr``` podemos emplear la función ```rename```


```R
liderazgo<-data
library(plyr)
liderazgo <- rename(liderazgo,
c(gerente="gerenteID", fecha="testDate"))
liderazgo
```


<table>
<thead><tr><th scope=col>gerenteID</th><th scope=col>testDate</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td></tr>
	<tr><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td></tr>
	<tr><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td></tr>
	<tr><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td></tr>
</tbody>
</table>



## Valores Perdidos

Cuando el volumen de observaciones lo justifica, podemos omitir aquellas que tienen datos perdidos. Anteriormente, vimos cómo recodificar los valores perdidos. Ahora, evaluemos su existencia y omitámoslos:


```R
liderazgo<-data
names(liderazgo)
```


<ol class=list-inline>
	<li>'gerente'</li>
	<li>'fecha'</li>
	<li>'pais'</li>
	<li>'genero'</li>
	<li>'edad'</li>
	<li>'q1'</li>
	<li>'q2'</li>
	<li>'q3'</li>
	<li>'q4'</li>
	<li>'q5'</li>
</ol>




```R
is.na(liderazgo[,6:10])
```


<table>
<thead><tr><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td></tr>
	<tr><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td></tr>
	<tr><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td></tr>
	<tr><td>FALSE</td><td>FALSE</td><td>FALSE</td><td> TRUE</td><td> TRUE</td></tr>
	<tr><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td><td>FALSE</td></tr>
</tbody>
</table>




```R
newdata <- na.omit(liderazgo)
newdata
```


<table>
<thead><tr><th></th><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><th scope=row>1</th><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td>5       </td><td>5       </td></tr>
	<tr><th scope=row>2</th><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td>5       </td><td>5       </td></tr>
	<tr><th scope=row>3</th><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td>5       </td><td>2       </td></tr>
	<tr><th scope=row>5</th><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td>2       </td><td>1       </td></tr>
</tbody>
</table>



## Fechas

Las fechas se pueden definir con la línea ```as.Date(x,'formato')``` donde ```x``` es el vector de datos y ```formato``` el formato de fecha a emplear. Los formatos más comunes son:

| Formato |  Resultado                      |
|---------|---------------------------------|
| %d      |  Día como un número             |
| %a      |  Día de la semana abreviado     |
| %A      |  Día de la semana sin abreviar  |
| %m      |  Mes como número                |
| %b      |  Mes abreviado                  |
| %B      |  Mes sin abreviar               |
| %y      |  Año en dos dígitos             |
| %Y      |  Año completo                   |


```R
mydates <- as.Date(c("2007-06-22", "2004-02-13")); mydates
```


<ol class=list-inline>
	<li><time datetime="2007-06-22">2007-06-22</time></li>
	<li><time datetime="2004-02-13">2004-02-13</time></li>
</ol>




```R
strDates <- c("01/05/1965", "08/16/1975"); strDates
```


<ol class=list-inline>
	<li>'01/05/1965'</li>
	<li>'08/16/1975'</li>
</ol>




```R
dates <- as.Date(strDates, "%m/%d/%Y"); dates
```


<ol class=list-inline>
	<li><time datetime="1965-01-05">1965-01-05</time></li>
	<li><time datetime="1975-08-16">1975-08-16</time></li>
</ol>



Vamos a modificar la fecha en el ejemplo de liderazgo


```R
myformat <- "%m/%d/%y"
liderazgo$fecha <- as.Date(liderazgo$fecha, myformat)
liderazgo
```


<table>
<thead><tr><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><td>1         </td><td>2008-10-24</td><td>US        </td><td>M         </td><td>32        </td><td>5         </td><td>4         </td><td>5         </td><td> 5        </td><td> 5        </td></tr>
	<tr><td>2         </td><td>2008-10-28</td><td>US        </td><td>F         </td><td>45        </td><td>3         </td><td>5         </td><td>2         </td><td> 5        </td><td> 5        </td></tr>
	<tr><td>3         </td><td>2008-10-01</td><td>UK        </td><td>F         </td><td>25        </td><td>3         </td><td>5         </td><td>5         </td><td> 5        </td><td> 2        </td></tr>
	<tr><td>4         </td><td>2008-10-12</td><td>UK        </td><td>M         </td><td>39        </td><td>3         </td><td>3         </td><td>4         </td><td>NA        </td><td>NA        </td></tr>
	<tr><td>5         </td><td>2009-05-01</td><td>UK        </td><td>F         </td><td>99        </td><td>2         </td><td>2         </td><td>1         </td><td> 2        </td><td> 1        </td></tr>
</tbody>
</table>



### Usando la fecha del sistema

Para usar la fecha del sistema existen variaas opciones:


```R
Sys.Date()
```


<time datetime="2017-11-01">2017-11-01</time>



```R
date()
```


'Wed Nov 01 09:41:49 2017'


También es posible calcular diferencias de fechas:


```R
startdate <- as.Date("2004-02-13")
enddate <- as.Date("2011-01-22")
days <- enddate - startdate
days
```


    Time difference of 2535 days


Se puede emplear la función ```difftime```. Veamos sus argumentos:


```R
args(difftime)
```


<pre class=language-r><code>function (time1, time2, tz, units = c("auto", "secs", "mins", 
<span style=white-space:pre-wrap>    "hours", "days", "weeks")) </span>
NULL</code></pre>


Es decir, podemos calcular la diferencia en varias periodicidades.


```R
today <- Sys.Date()
initial <- as.Date("1956-10-12")
difftime(today, initial, units="weeks")
```


    Time difference of 3185.714 weeks


### Ejercicio simple:
con los compañeros del mesón calcular las diferencias de edades en segundos, semanas, días, horas. Hacer los mismo con las edades de cada compañero. Identificar el día de la semana en que nació cada compañero

## Cambiando el Tipo de Datos

Hay momentos en los que se requiere cambiar el tipo de dato. Por ejemplo, convertir un caracter en factor o una tabla en data.frame. Para ello existen vairas opciones:

| Test           |       Convertir a  |
|----------------|--------------------|
| is.numeric()   |   as.numeric()     |
| is.character() |   as.character()|
| is.vector()    |   as.vector()|
| is.matrix()    |   as.matrix()|
| is.data.frame()|   as.data.frame()|
| is.factor()    |   as.factor()|
| is.logical()   |   as.logical()|

Veamos un ejemplo:


```R
a <- c(1,2,3); a
```


<ol class=list-inline>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ol>




```R
is.numeric(a)
```


TRUE



```R
is.vector(a)
```


TRUE



```R
a <- as.character(a); a
```


<ol class=list-inline>
	<li>'1'</li>
	<li>'2'</li>
	<li>'3'</li>
</ol>




```R
is.numeric(a)
```


FALSE



```R
is.vector(a)
```


TRUE



```R
is.character(a)
```


TRUE


## Ordenando los datos

Por múltiples motivos, requerimos ordenar los datos en función de una variable específica. Algunos ejemplos de cómo hacerlo:


```R
newdata <- liderazgo[order(liderazgo$edad),];newdata
```


<table>
<thead><tr><th></th><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><th scope=row>3</th><td>3         </td><td>2008-10-01</td><td>UK        </td><td>F         </td><td>25        </td><td>3         </td><td>5         </td><td>5         </td><td> 5        </td><td> 2        </td></tr>
	<tr><th scope=row>1</th><td>1         </td><td>2008-10-24</td><td>US        </td><td>M         </td><td>32        </td><td>5         </td><td>4         </td><td>5         </td><td> 5        </td><td> 5        </td></tr>
	<tr><th scope=row>4</th><td>4         </td><td>2008-10-12</td><td>UK        </td><td>M         </td><td>39        </td><td>3         </td><td>3         </td><td>4         </td><td>NA        </td><td>NA        </td></tr>
	<tr><th scope=row>2</th><td>2         </td><td>2008-10-28</td><td>US        </td><td>F         </td><td>45        </td><td>3         </td><td>5         </td><td>2         </td><td> 5        </td><td> 5        </td></tr>
	<tr><th scope=row>5</th><td>5         </td><td>2009-05-01</td><td>UK        </td><td>F         </td><td>99        </td><td>2         </td><td>2         </td><td>1         </td><td> 2        </td><td> 1        </td></tr>
</tbody>
</table>




```R
attach(liderazgo)
newdata <- liderazgo[order(genero, edad),]
detach(liderazgo)
newdata
```

    The following objects are masked _by_ .GlobalEnv:
    
        edad, fecha, genero, gerente, pais, q1, q2, q3, q4, q5
    
    


<table>
<thead><tr><th></th><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><th scope=row>3</th><td>3         </td><td>2008-10-01</td><td>UK        </td><td>F         </td><td>25        </td><td>3         </td><td>5         </td><td>5         </td><td> 5        </td><td> 2        </td></tr>
	<tr><th scope=row>2</th><td>2         </td><td>2008-10-28</td><td>US        </td><td>F         </td><td>45        </td><td>3         </td><td>5         </td><td>2         </td><td> 5        </td><td> 5        </td></tr>
	<tr><th scope=row>5</th><td>5         </td><td>2009-05-01</td><td>UK        </td><td>F         </td><td>99        </td><td>2         </td><td>2         </td><td>1         </td><td> 2        </td><td> 1        </td></tr>
	<tr><th scope=row>1</th><td>1         </td><td>2008-10-24</td><td>US        </td><td>M         </td><td>32        </td><td>5         </td><td>4         </td><td>5         </td><td> 5        </td><td> 5        </td></tr>
	<tr><th scope=row>4</th><td>4         </td><td>2008-10-12</td><td>UK        </td><td>M         </td><td>39        </td><td>3         </td><td>3         </td><td>4         </td><td>NA        </td><td>NA        </td></tr>
</tbody>
</table>




```R
attach(liderazgo)
newdata <-liderazgo[order(genero, edad),]
detach(liderazgo); newdata
```

    The following objects are masked _by_ .GlobalEnv:
    
        edad, fecha, genero, gerente, pais, q1, q2, q3, q4, q5
    
    


<table>
<thead><tr><th></th><th scope=col>gerente</th><th scope=col>fecha</th><th scope=col>pais</th><th scope=col>genero</th><th scope=col>edad</th><th scope=col>q1</th><th scope=col>q2</th><th scope=col>q3</th><th scope=col>q4</th><th scope=col>q5</th></tr></thead>
<tbody>
	<tr><th scope=row>3</th><td>3       </td><td>10/1/08 </td><td>UK      </td><td>F       </td><td>25      </td><td>3       </td><td>5       </td><td>5       </td><td> 5      </td><td> 2      </td></tr>
	<tr><th scope=row>2</th><td>2       </td><td>10/28/08</td><td>US      </td><td>F       </td><td>45      </td><td>3       </td><td>5       </td><td>2       </td><td> 5      </td><td> 5      </td></tr>
	<tr><th scope=row>5</th><td>5       </td><td>5/1/09  </td><td>UK      </td><td>F       </td><td>99      </td><td>2       </td><td>2       </td><td>1       </td><td> 2      </td><td> 1      </td></tr>
	<tr><th scope=row>1</th><td>1       </td><td>10/24/08</td><td>US      </td><td>M       </td><td>32      </td><td>5       </td><td>4       </td><td>5       </td><td> 5      </td><td> 5      </td></tr>
	<tr><th scope=row>4</th><td>4       </td><td>10/12/08</td><td>UK      </td><td>M       </td><td>39      </td><td>3       </td><td>3       </td><td>4       </td><td>NA      </td><td>NA      </td></tr>
</tbody>
</table>



# Ejercicio

Con las bases de datos suministradas a través del ejercicio de importación de datos aplicar lo visto en las últimas dos sesiones
