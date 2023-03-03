
# Mentoring 2 ninja dev 

We learn how do design applications with the correct technology and high scalable architectures


## La elección del lenguaje, liberías y frameworks dependerán del contexto.

En este capitulo discutiremos sobre como elegir un lenguaje, tecnología y frmaework dependiendo del problema a solucionar. Un montón de factores pueden influir en resolver el problema que enfrentan los equipos tales como

* Integración con sistemas legacy
* Integración con terceros
* experticie de los integrantes
* Tiempos de desarrollo
* complejidad de la tarea a resolver

Debemos abordar una solución conociento las ventajas y desvenjas de aquellas partes de la solución a su vez esto va de la mano con conocimientos a nivel conceptual y técnico 

## Diseño de aplicaiones WEB

En el diseño de aplicaciones web consideraremos 2 modelos altamente usados en la industria 

 * Modelo síncrono
 * Modelo asíncrono

### Modelo síncrono
donde las aplicaciones por cada peticion recibida crear un hilo para realizar la tarea. esto conlleva lo siguiente

* alto consumo de recursos en ram y cpu
* cada tarea es independiente 
* posibilidad de tareas bloqueantes

Este modelo es ideal para tareas bloqueantes por ejemplo conexiones lentas conexiones a base ded atos o peticones http de lenta respuesta, procesos intensivos en CPU 

Este modelo es altamente utilizado en paginas de contentido dinamico fue el primer modelo que enfrentamso cuando aprendemos aplicaiones web. 

### Modelo asíncrono

Este modelo es ideal para aplicaiones web concurrentes de alto trafico, nos permite trabajar con multiples peticiones con los minimos recursos necesarios. El ejmplo claro es NodeJS y su arquitectura llamada EventLoop donde con un solo hilo podemos atender multiples peticones ya que internamente los llamados a CPU son encolados a la espera de ser atendidos las caracteristicas de este enfoque son:

* Uso eficiente de los recursos RAM y CPU
* Ideal para aplicaciones web de alto trafico

Este rendimiento lleva un coste el cual es que debemos evitar el uso de procesos bloqueantes ya que hechariamos abajo la aplicacion sin la posibilidad de que otras peticiones puedan ser procesadas un ejemplo seria la combinacion:

NodeJS + Postgres + queries bloqueantes + despliegue K8s

Si tenemos un ambiente concurrente y dado el caso que algun momento una de las peticiones a base de datos resulta ser en un bloqueo nuestro servidor dejaria de responder solo por 1 query esto en algunos casos resulta tambien en que si nuetsra aplicacion esta desplegada en la nube y existe una estrategia de endpoint de `health` el gestor de la aplicacion posiblemente mate el proceso y levante una nueva instanca de la aplicaion, esto puede ser critico en ambientes de alto trafico.

Es por eso que la combinacion nodejs y mongo db es ideal para este tipo de situaciones ya que mongodb es rapido y eficiente en operaciones de lectura. 

### API asincrona o sincrona

Esto depende del caso es lo primero que debemos considerar en ambientes concurrentes, lo mas probable es que hallan casos que no identifiquemos a primera pero si tenemos que saber cuando usar un modelo asincrono o sincrono. Basicamente tendremos esta premisa

* Aplicaiones concurrentes con alto trafico: Modelo asincrono para mejor uso de recursos 
* Aplicaiones u tareas bloqueantes o intensivas en CPU: Modelo sincrono 

### EventLoop en Nodejs ya lo disponen otros lenguajes mediante librerías

La estrategia de EventLoop esta disponible en otros lenguajes mediante librerías o frmaeworks. discutiremos las ventajas lenguajes de programación mas adelante pero estas son las alternativas que existen tanto sicrono como asincrono

* Javascript: 
    * Asincrono: NodeJS, DenoJs
    * Sincrono: no disponible
* Python:
    * Sincrono: Flask Web Framework
    * Asincrono: Fast API
* Java:
    * Sincrono: Spring Web
    * Asincrono: Spring WebFlux


Finalmente cada modelo es ideal para:

* Sincrono: 
    * intesivos en cpu calculos procesamiento de datos
    * batch procesos
    * queries pesadas
* Asincrono:
    * tiempo real
    * concurrencia de usuarios
    * alto trafico



### Entorno empresarial logicas de negocio complejas

excelente para paradigmas orientados a objetos es por eso estos los veremos fuertemente en entronos empresariales como los son

* Java
* .NET

Estos lenguajes tambien tienen una ventaja aparte de su tipado en entornos empresariales, tienen un excelente soporte en cuanto a librerías y frameworks es distinto a el caso de nodejs en donde la cantidad de librerías es enorme y en algunois casos son probelematicas en temas de actualizaciones es por eso que debemos tener cuidado en que usamos en nodejs aun asi NestJs esta teneniendo un enorme crecimeinto como framework por lo que su adopcion es una excelente opcion en aplicaciones de medio a complejas sin embargo NestJs aun se queda corto en ciertos escenarios donde las implementaciones por defecto son para casos simples a medio pero su personalizacion a mas detalle puede que encuentrees que no es suficiente

resumiendo para aplicaciones con fuerte logica de negocio, necesidades de desarrollos rapido y alta criticidad, las elecciones serian
* Java Spring Framework
* .NET
* NestJs

### Resolucion de problemas especificos 

La necesidad de resolver un problema especifico de manera rapida podemos recurrir a python multiparadigma funcional y orientado a objetos podemos crear soluciones rapidas y sencillas con gran soporte de librerías para todo lo basico y complejo eso si debemos ser conciente de lo que usamos. python resuelve los siguientes problemas

* scripting
* automatizacione de tareas
* procesos ETL
* analizis de datos
* aplicaiones web 



# Training applicaton design for next level

En las siguientes series de mentoring aprenderemos a diseñar aplicaiones mantenibles y orientadas a un codigo mantenible y elegante en combinación con soluciones a nivel de arquitectura adecuada al problema a resolver.

## Proyecto base
 Trabajaremos sobre un proyecto base con NestJs en modo monorepo. nuestro proyecto debe cumplir con lo siguiente:

 * Monorepo con NestJs
 * Cada librería y aplicaion debe estar documentada brevemente explicando que es lo que hace 
 * La infraestructura debe estar montada con docker-compose
 * En el README raiz del proyecto debe indicar como ejecutar el proyecto variables de entorno y todo lo necesario para probar las aplicaiones

## API Usuarios y Roles

Aplicación para el manejod e usuarios roles y recursos. utilizando NestJs con arquitectura en n-capas
Crearemos una API backend para administrar usuarios roles y permisos

el usuario debe tener las siguientes propiedades:

* username (Unico)
* createdAt
* updatedAt
* isActive
* roles

los casos de uso son:

* Endpoint Crear usuarios
* El nombre de usuario debe ser en base a la siguiente entrada: `nombre` y `apellido` seguido de un numero y el username debe tomar la inicial del nombre seguido de un punto si ya existe el
usuario debe generarse yn numero correlativo ejemplo: Nombre `jack bauer` = username `j.bauer01` si existe un usuario ya con el nombre agregar un numero `j.bauer02` 
* Endpoint obtener todos los usuarios
* Endpoint Crear recursos con permisos de lectura o escritura
* Endpoint Crear roles al crear roles deben definirse los recursos asociados
* Endpoint Asignar roles a usuarios

Restriciones:

* Los errores de input o de validacion responden con un 409
* Errores de servidor 500















