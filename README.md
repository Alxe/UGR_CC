# Cloud Computing

Repositorio que recopila el trabajo desarollado en la asignatura de Cloud Computing del Máster de Ingeniería Informática, en la Universidad de Granada.

## Descripción

La idea a desarollar consiste en un servicio de gestión de pagos entre integrantes de grupos.

Seguiría una estructura de microservicios interconectados entre sí, cada uno con unas responsabilidades, comunicándose a través de una cola de mensajes.
Entre los componentes, podemos distinguir:

- [Gestión de Grupos y Usuarios][user-repo] <!-- TODO -->
- [Registro e Historial de Transacciones][transaction-repo] <!-- TODO -->
- [Interfaz de Usuario como Bot de Telegram][telegram-repo] <!-- TODO -->

[user-repo]: #
[transaction-repo]: #
[telegram-repo]: #

## Desarrollo

Se procurará desarollar los diferentes componentes con diferentes tecnologías y en diferentes plataformas, ya que uno de los objetivos de la asignatura es comunicar diferentes microservicios entre sí.  
Cada microservicio estará contenido en un repositorio individual, añadidos como submodulos a este repositorio.

De esta manera, se plantea usar [RabbitMQ][rabbitmq] como cola de mensajes, así como las plataformas [Erlang][erlang] con [Elixir][elixirlang] y la plataforma [Golang][golang] para desarrollar unos u otros componentes.

[rabbitmq]: https://www.rabbitmq.com/
[elixirlang]: https://elixir-lang.org/
[erlang]: https://www.erlang.org/
[golang]: https://www.golang.org/
