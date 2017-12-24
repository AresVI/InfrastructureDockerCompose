![](https://raw.githubusercontent.com/LabAuSegTIC/PromotionalWebHtml/master/images/Ares_logoColor.png)

# ¿Cómo desplegar AresVI?

AresVI es un sistema de auditoría de la trazabilidad de los procesos de producción de vino. 
Esta plataforma está compuesta por un ecosistema muy heterogeneo de subsistemas, tales como:
 - Aplicación Java
 - Base de datos MySQL
 - Sistema de inferencia en Drools
 - Sistema BPMN2 con Bonita BPM
 - Cache con Redis

# AresVI - Docker - Un servidor

Si te gusta Docker esta solución te va a interesar.

## Introducción

La solución utilizando Docker para el despliegue simplifica mucho el manejo de dependencias y requisitos de sistema. Además facilita la tarea de upgrade del sistema a través de simples scripts bash. Nuestra propuesta está basada en sistema Unix, para sistemas Windows no se dará soporte, además de ello, esta solución es el primer escalon dado que si la exigencia sobre el sistema aumenta será necesario migrar a una arquitectura de microservicios distribuida, dónde cada servicio se aloja en máquinas diferentes y no en una sóla como en este caso.

### Requisistos

#### Requisitos Físicos

Dado que sólo se hará uso de un sólo servidor, los requisitos mínimos podrán ser un pocos elevados.

##### Requisitos Físicos Mínimos

- `4 Gb RAM`
- `Procesador de 2 nucleos`

##### Requisitos Físicos Recomendados

- `8 Gb RAM`
- `Procesador de 4 nucleos`

#### Requisitos de Software

- `docker: ~> v17.06 `
- `docker-compose: latest`
- `mysql-client: ~> 5.4`
- `git: latest`

> Nota: La infraestructura soporta la comunity edition para Docker.

### Despliegue por Primera Vez

Para desplegar la aplicación por primera vez sólo es necesario ejecutar los siguientes comandos:

```Bash
git clone https://github.com/LabAuSegTIC/InfrastructureDockerCompose.git
cd InfrastructureDockerCompose
docker-compose -f aresvi-compose.yml -d up
```

El comando descargará todas las imagenes de Docker necesarias y las inciará con la configuración esperada. Un comando mágico que levanta y configura todo lo necesario. Iniciando la base de datos y ejecutando los scripts de iniciación.

## Actualización de la Aplicación

Una vez que el sistema esté en funcionamiento, tendremos la necesidad de actualizarlo. Para ello simplemente se debe ejecutar estos dos commandos uno seguido del otro:

```Bash
docker-compose -f aresvi-compose.yml down
docker-compose -f aresvi-compose.yml -d up
```
