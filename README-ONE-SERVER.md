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

- `Docker: ~> v17.06 `
- `mysql-client: ~> 5.4`
- `git`

> Nota: La infraestructura soporta la comunity edition para Docker.

### Despliegue por Primera Vez

Para desplegar la aplicación por primera vez sólo es necesario ejecutar los siguientes comandos:

```Bash
git clone https://github.com/LabAuSegTIC/InfrastructureDockerCompose.git
docker-compose -f aresvi-compose.yml -d up
```

El comando descargará todas las imagenes de Docker necesarias y las inciará con la configuración esperada. Un comando mágico que levanta y configura todo lo necesario. Iniciando la base de datos y ejecutando los scripts de iniciación.

## Actualización de la Aplicación

Una vez que `AresVI` esté en funcionamiento hacer un upgrade del sistema no debería ser algo complicado. Es por ello que se creó un script llamadao `upgrade-aresvi.sh` (sólo compatible con plataformas Unix).

Con sólo ejecutar el script `upgrade-aresvi.sh` el sistema realizará un backup de la base de datos, luego dará de baja todos los contenedores, eliminandolos, borrando los volumentes, redes y toda la configuración. Luego levantará toda la infraestructura y restaurará el backup realizado.

### Actualización Sin Backup

En caso que se desee actualizar toda la infraestructura sin mantener los datos se deberá agregar el parámetro: `--no-backup`

``./upgrade-aresvi.sh  --no-backup ``

Luego de ejecutarlo el sistema nos pedirá confirmación de la operación.

## Autores

* **Javier Caballero** - *Tecnical Director* - [Web Site](http://javiercaballero.info)

Puedes ver la lista de [colaboradores](https://github.com/orgs/LabAuSegTIC/outside-collaborators) 

## License

La licencia de este proyecto es  GPL-3.0. Para más infomación puede leer el siguiente archivo  [LICENSE.md](https://github.com/LabAuSegTIC/InfrastructureDockerCompose/blob/master/LICENSE).

## Agradecimiento

* Universidad Tecnológica Nacional - Facultad Regional Mendoza
* Universidad del Aconcagua
* Laboratorio de Auditoría y Seguridad en TIC
