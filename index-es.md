## Introducción

Soy CTO de [Joinup](https://joinup.es/) desde principios de 2016. Desde finales de ese mismo año tenemos un backend de alta disponibilidad (24x7) y alta carga (varios miles de peticiones por minuto). No hacemos guardias, no tenemos problemas inesperados, y todo se lo debemos a seguir una serie de reglas básicas, todo se debe a seguir el siguiente zen.


### Nuestro zen

Identifica tus cuellos de botella.

Uno de los más comunes cuellos de botella son las bases de datos.

En cada petición HTTP debes de conocer, controlar y optimizar el número de consultas que se hacen a las bases de datos.

Como no se pueden comparar peras con manzanas, por cada petición HTTP también hay que conocer, controlar y optimizar el tiempo total que tardan en ejecutarse todas las consultas a las bases de datos.

Las bases de datos relacionales no sirven para todo.

Del mismo modo controla y optimiza el uso que se hace de la memoria en cada petición.

Si algo hace que suba la memoria… ¡estudialo!

La memoria es como los ahorros, si tienes memoria disponible en algún momento puedes gastarla en algún capricho, pero aún así no tengas muchos caprichos.

Por último controla el tiempo global de todas las peticiones. 

Todas las peticiones a sistemas externos deben tener un timeout. Es mejor amputar un brazo que morir de gangrena.

Ten un sistema de tareas en segundo plano para que el primer plano (servidor web) sea lo más rápido posible.

Todas las peticiones a sistemas externos, siempre que sea posible, deben hacerse en segundo plano. 

Y creeme la gran mayoría de las peticiones se pueden hacer en segundo plano. Puede que el usuario final pierda algo de información pero ganará un sistema robusto.

Conoce, controla y optimiza en segundo plano lo mismo que en primer plano.

No incumplas ninguna de estas normas por más que te tienten con una razón no técnica.

Si la razón es técnica, reflexionala durante el tiempo suficiente.

No creo que los Holandeses sean superhombres, pero mi color favorito es el naranja.

Si eres el responsable del backend, tu jefe a partir de ahora será el backend. El podrá despedirte mucho antes que cualquier otra persona de la empresa.

### Una implementación de este Zen

1. Servidor web: Django
1. Sistema de tareas en segundo plano: celery
1. Base de datos relacional: Postgresql
1. Base de datos no relacional: mongodb
1. Middlewares que controlan el número de  peticiones a las bases de datos, el tiempo de estas, el incremento de la memoria y el tiempo global de la petición http.
1. Decorador para cada tareas de celery que controla lo mismo que los middlewares


