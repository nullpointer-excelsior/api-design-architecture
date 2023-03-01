# Clean Architecture hexagonal

Conocida como arquitectura de puertos y adaptadores, nos provee una forma de seaprar el domnio de las implementaciones tecnologicas como 
lo pueden ser los frameworks. El concepto de puerto y adaptador se traduce en Interfaz e implementacion

Usarlo cuando:

* Queremos enfocarnos en un dominio limpio
* Pruebas unitarias sin complicaciones sobre nuestras lógicas de negocio
* No queremos contaminar la lógica core del negocio con algun framework o tecnologia

