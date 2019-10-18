# Cloud Computing

Repositorio que recopila el trabajo desarollado en la asignatura de Cloud Computing del Máster de Ingeniería Informática, en la Universidad de Granada.

El proyecto a desarrollar sigue una metodología incremental, de naturaleza ágil, siguiendo el _feedback_ del profesor de la asignatura.
Por tanto, muchos detalles encontrados en la documentación pueden ser cambiantes en el tiempo.

## Descripción

La idea a desarollar consiste en un servicio de gestión de pagos entre integrantes de grupos.

Seguiría una estructura de microservicios interconectados entre sí, cada uno con unas responsabilidades. Una previsualización se puede encontrar en [Draw.io][architecture].
Entre los componentes, podemos distinguir:

- [Autenticación y Usuarios](#autenticaci%c3%b3n-y-usuarios)
- [Transacciones y Pagos](#transacciones-y-pagos)
- [Estadísticas](#estad%c3%adsticas)

[architecture]: https://www.draw.io/?lightbox=1&highlight=0000FF&nav=1&title=DiagramaCC.drawio#R5VjbcpswEP0aHtvhYlz8aDuXpm2mmbpJ00dZCFArS4wQvvTruwIRwOCENEmTtCTjQavVIu3ZPbtgefPV9lSiNDkXIWGWa4dbyzuyXNcZua6l%2F%2B1wV0oCe1QKYklDo1QLFvQXMULbSHMakqylqIRgiqZtIRacE6xaMiSl2LTVIsHaT01RTDqCBUasK%2F1GQ5WYU%2Fh2LX9PaJxUT3ZsM7NClbIRZAkKxaYh8o4tby6FUOXdajsnTDuv8ku57uTA7M3GJOFqyAKcf%2Fl4%2Fe772YfP58F5jlfX7GrxxvNKM2vEcnNis1u1q1wAZsDbMJjBEVItxEzkYHW2SagiixRhLdxAAIAsUSsGIwduGVoSNkP4ZyxFzsO5YELCFBdcG4sEVwZvB5wxQ4zGHAaMREpPU8aqFZbrRb7%2B03tQUvwkjZlxcRmDDXl5gbzrKOO7NZGKbBsi47hTIlZEyR2omNmJcZMJ4spJmzoixhMDc9KIhlGFPTJRGN9YroGCG4PVfXDrgW3MtN9CuobbWN9OcwVHphhhas09a%2BbxSgme2dDrWarPfpnlSFKRVdNLub9g38zBwLkjUPawDn0ShKM%2BrAN36RVYPwKm3sRvgep5dgdVx%2B1BNXgqUN0hyRgCPZmhkCoRseCIHdfSWZFrRD%2FHhlGt80mI1Pj7B1FqZ3IP5Uq00QhRlhTrndscnYlcYnLLaQzPKyRjou4OZX2wW2GThCFF121efnwMRkMya5EvMyxp2kgsG2nSF2u6ouCqvqwBJ2odhFUOXPcLSX3qTKFQ25geZTpTH5BsTx8YcC65u9br3%2FrV8LsxVwyOtq3RzoxaAXWgKGiKLy5Q0TkMvmBTUxGU3t9fiET%2FsSOxWDqVEu0aCqmgXGUNyxdaUPPSuOKcXZuDTg7ou5Nb9eGm3EGdEzdH%2BfM0GZQlx4eC%2B1XXDX%2B85%2B%2Fg2euGPQSNKyJpBCiAItM%2FlEdCrpq9gT2cfDrWQ6Ltatqz872%2B4fmJ67kJyH%2BVpdAfElVfJeIZwphCU38Q8d728gLF%2F2xv6XovjSOcyaC%2BRjCKqYKXO3eu%2Fd3T5nQRg82dCP2qTjiRLT4pSKG7gOdkXTBFs13ypr26aRkl9s1DUKZeErX8OSk4wXO1JQ8rNs6QQDrj3f5Ym86IXEOEicFMccaxkKloxxUqPhfl6X8WCC%2BrPFQvp41AaNBHmft7rzdFJndzvFDNed06lOxTIPyPQjl6UVBW274rpxWREdTZfhTv1ypeVkgPyt82pPes%2BIgEEe6r%2BGMckGX0NF%2BTRpOBFX98%2F4oPw%2FqzcflGV398945%2FAw%3D%3D

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
