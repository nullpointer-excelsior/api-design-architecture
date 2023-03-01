# Arquitectura N Capas

Esta arquitectura esta presente en la mayoria de los proyectos que realizamos. La idea de separar
las responsabilidades por capas nos da una jerarquía en el llamado de nuestros componentes de software que nos facilita entender
el flujo del programa.

En este ejemplo se sugiere las siguientes capas:

* `persistence:` todo lo relacionado con la lectura y escritura de datos de nuestra aplicacion. En esta capa pueden estar las librerías ORM, ODM, 
  entidades, modelos o estructuras.
* `domain:` Todo lo relacionado con la lógica de negocio de la aplicación y el modelo de las entidades
* `application:` Aca estará el puento de entrada de nuestra aplicación donde podemos invocar las funcionalidades. por ejemplo si nuestra aplicación es una API acá
estarán los restcontrollers, si fuera una aplicación de CLI tendriamos todo lo relacionado a uan aplicaión de consola.

Si tubieramos que realizar la integración con algun sistema externo debemos crear una capa adicional,

Usar cuando queremos:

* Nuestra aplicación tiene lógicas mas complejas que un CRUD
* Queremos una arquitectura simple pero que pueda crecer sin que el código quede inmantenible
