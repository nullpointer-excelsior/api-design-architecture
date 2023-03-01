# Modulos y capas

Cuando nuestra aplicación empieza atener distintos "features" o muchas funcionalidades agrupadas es ideal separar estos contextos en directorios para 
en un futuro tener cada responsabilidad separada cada uno de estos modulos es independiente y debemos evitar acoplarlos con otros. para evitar este acople se debe recurrir a un modulo 
`shared` p `commons` que contendra todas las piezas de código que deban compartirse, estas piezas deben ser lo mas simple posible y reutilizables

Los modulos pueden ser aplicados a cualquier arquitectura

cuando aplicar este enfoque

* Nuestra aplicacion tiene  distintos contextos
* Queremos organizar las logicas de negocio en contextos definidos
* Nuestra aplicación cambia constantemente y agrega nuevas funcionalidades
* Queremos identificar facilmente los modulos que puedne ser extraidos de la aplicacion



