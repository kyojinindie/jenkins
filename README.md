# jenkins

## Integración continua

Es una práctica de desarrollo que requiere a los desarrolladores integrar el código
en el que trabajan, actualizan o modifican a un repositorio compartido, varias veces al día.

## Prácticas de integración continua

1- Auromatizar el proceso de bvuild o compilación
2- Optimizar el build para que se auto testee
3- Mantener un solo source repository
4- No complicar las cosas para el resto
5- Ña visibilidad de qué está sucediendo
6- Despliegue automático

## Resposabilidades del equipo

1- Check in frecuente
2- No realizar un check in con código erróneo
3- No realizar un check in en código que no fue testeado
4- No realizar un check in cuando el build no funciona

## Entrega continua

La entrega continua de código a un entorno específico una vez que el código está listo y preparado para ser entregado.


## Despliegue continuo

Es la práctica de liberar y entregar cada build o compilación satisfactoria al usuario.

## Jenkins

Es una herramienta CI/CD de fuente abierta escrita en java

## Instalación

```shell
mkdir -p /jenkins/jenkins_home
chown 1000 jenkins
docker pull jenkins/jenkins
```

```yaml

version: '3'
services:
  jenkins:
    image: jenkins/jenkins
    ports:
      - 8080:8080
      - 50000:50000
    container_name: jenkins
    volumes:
      - $PWD/jenkins_home:/var/jenkins_home
    networks:
      - net
networks:
  net:
```

```shell
docker-compose up -d
```

## Jenkins Job

Son tareas ejecutables que son supervisadas y controladas por jenkins.

## Arquitectura Maestro Esclavo

### Tareas del Maestro

1- Es el encargado de programar el Build Job.
2- Envía la compilación al esclavo para que se haga efectiva la ejecución del Job.
3- Supervisar el trabajo del esclavo y registrar los resultados del Build.


### Esclavo

Los esclavos son máquinas programadas para construir los proyectos que el maestro le requiere

Cuado el maestro registra los esclavos, empieza a enviar y elegir las tareas para cada esclavo

### Jenkins executor
Un ejecutor es una secuencia separada de compilaciones que se ejecutarán en un nodo en paralelo
Un nodo o esclavo puede tener uno o más ejecutores
