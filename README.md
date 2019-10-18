# Cloud Computing

Repositorio que recopila el trabajo desarollado en la asignatura de Cloud Computing del Máster de Ingeniería Informática, en la Universidad de Granada.

El proyecto a desarrollar sigue una metodología incremental, de naturaleza ágil, siguiendo el _feedback_ del profesor de la asignatura.
Por tanto, muchos detalles encontrados en la documentación pueden ser cambiantes en el tiempo.

## Descripción

La idea a desarollar consiste en un servicio de gestión de pagos entre integrantes de grupos.

Seguiría una estructura de microservicios interconectados entre sí, cada uno con unas responsabilidades.
Entre los componentes, podemos distinguir:

- [Autenticación y Usuarios](#autenticaci%c3%b3n-y-usuarios)
- [Transacciones y Pagos](#transacciones-y-pagos)
- [Estadísticas](#estad%c3%adsticas)

## Desarrollo y Tecnologías

Se procurará desarollar los diferentes componentes con diferentes tecnologías y en diferentes plataformas, ya que uno de los objetivos de la asignatura es comunicar diferentes microservicios entre sí.  
Cada microservicio estará contenido en un repositorio individual, añadidos como submodulos a este repositorio.

De esta manera, se plantea usar [RabbitMQ][rabbitmq] como cola de mensajes, así como las plataformas [Erlang][erlang] con [Elixir][elixirlang] y la plataforma [Golang][golang] para desarrollar unos u otros componentes.

[rabbitmq]: https://www.rabbitmq.com/
[elixirlang]: https://elixir-lang.org/
[erlang]: https://www.erlang.org/
[golang]: https://www.golang.org/

## Microservicios

De carácter general, cada microservicio contendrá únicamente la información propia a su propósito o necesaria para vincular datos, comunicándose con otros microservicios, por paso de mensajes o notificaciones de cuando necesitan más detalles para una correcta funcionalidad. También se contempla que presenten una interfaz REST para comunicación externa.

### Autenticación y Usuarios

Módulo que será dueño de la información de los usuarios y los grupos, también actuando como punto de acceso para verificar que las credenciales de un usuario sean válidas.

### Transacciones y Pagos

Módulo que será dueño del registro de transacciones, así como de llevar las operaciones de pago.  
A priori contendría una cola de mensajes donde depositar eventos (pago pendiente, pago realizado) para incorporar en otros servicios.

### Estadísticas

Módulo que se encargará de generar estadísticas de los grupos (consumo medio/tiempo, transacciones/tiempo...)
