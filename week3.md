## Lapply
```
x <- list(a= 1:5, b = rnorm(10))
lapply(x, mean)
```

#la siguiente es una funcion silecciosa porque se crea solo para el lapply, otra cosa es que elt y los corchetes hacen referencia a ninguna fila y una columna.
```
x <- list(a= matrix(1:4,2,2), b= matrix(1:6,3,2))
lapply(x, function(elt) elt[,1])
```
## apply
```
x <- matrix(rnorm(200),20,10)
apply(x,2,mean)
```
##mapply

#esto es tredioso: 
```
list(rep(1,4), rep(2,3),rep(3,2), rep(4,1))
```
#con mapply lo hago asi:
```
mapply(rep, 1:4,4:1)
```
## split
```
library(dataset)
head(airquality)
s<- split(airquality, airquality$Month)
lapply(s, function(x) colMeans(x[,c("Ozone","Solar.R","Wind")]))
```

#en la formula  usamos lo que se le hizo split y en X usamos la coma antes de la c (,C(..)) para hacer una frame es decir una tabla de ese tipo con los tipos en las filas 
#con estas formulas voy a sacar por mes las media de los items buscados; ozono, solar r y wind. pero hay un problema y es que ozono tiene muchos NA. 

#Antes de resolver los NA vamos a ver otra sapply
```
sapply(s, function(x) colMeans(x[,c("Ozone","Solar.R","Wind")]))
```
#y ahora sin los NA:
```
sapply(s, function(x) colMeans(x[,c("Ozone","Solar.R","Wind")], na.rm= TRUE))
```

### DEBUGGING tools

los debug nos sirven para identificar errores

#traceback ejemplo
```
mean(x)
traceback()
```

#calculo la media de x pero no exite entonces es un error. al llamar tracebakc me dice donde esta el error. Debo aalmarla despues del error

#debug ejemplo 
```
debug (lm)
lm(y-x)
```
#lo que hace es imprimir todo el codigo de la funcion. y aparece Browse y abre el navegador browese aqui al lado de los MD. lo que voy haciendo es precionar "n" que significa next para ir viendo paso a paso las lineas del codigo.cuando llego al error me lo muestra. puedo llamar las funciones de adentro con debug(nombredeF) y asi abrir un tercer browser para esta funcion.

# recover ejemplo

# puedo configirar la funcion recover como un manejador de errores. utilizando la funcion options. 

```
options(error = recover)
```

#voy a causar el error llamando un archivo que no exite, luego apareceran los mensajes de error pero me abrirá un pequeño menu con algunas opciones para manejar el error.

```
read.cvs("noexito")
```
#### no me funcionó. hacer error= recover




###     SWirl 

#apply() always returns a list, whereas sapply() attempts to simplify the result.

#Whereas sapply() tries to 'guess' the correct format of the result, vapply() allows you to specify it explicitly. If the result doesn't match the format you specify, vapply() will throw an error, causing the operation to stop. This can prevent significant problems in your code that might be caused by getting unexpected return values from sapply()








