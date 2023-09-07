[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/wbfJ62Ab)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11613740&assignment_repo_type=AssignmentRepo)

# Definición de los Agentes (Vehículos, Peatones y Semáforos)

## Propiedades de los Agentes

- Agentes Proactivos: Ya que está orientado a objetivos, el caso del carro es cruzar la calle sin que haya ninguna colisión con otro auto o peatón, además, reconoce oportunidades ya que en caso de que no sea necesario interactuar con otros agentes, el agente puede tomar la decisión de cruzar la calle cuando le corresponda. Para el caso de los peatones, el agente puede tomar la decisión de cruzar la calle cuando el semáforo esté en verde. Finalmente, en el caso de los semáforos, el agente puede tomar la decisión de cambiar de color cuando el tiempo de espera haya terminado.

- Habilidades Sociales: Los semáforos tienen coordinación, ya que se coordinan con los otros semáforos para decidir cuando cambiar de color. Los carros tienen cooperación, ya que se coordinan con los semáforos para decidir cuando acelerar, frenar o detenerse en el cruce. Finalmente, los peatones tienen cooperación, ya que se coordinan con los semáforos para decidir cuando cruzar la calle.

## Propiedades del Ambiente

- Es un ambiente en el que se puede acceder a la informacion de la posicion de los agentesy sus estados.

- Es determinista, ya que el estado del ambiente es completamente determinado por el estado actual del agente y las acciones que este realiza.

- Es estático, ya que el ambiente no cambia con el tiempo, es decir, no hay cambios en el ambiente que no sean provocados por los agentes.

- Es episódico, ya que la experiencia del agente se divide en episodios atómicos, es decir, cada episodio es independiente de los demás.

- Es discreto, ya que el ambiente es finito, es decir, el agente puede percibir un número finito de estados.

## Clasiﬁcación de los Agentes

En nuestro caso, todos los agentes son BDI.

### Vehículo:

- Beliefs: El agente tiene las creencias de su posición, dirección, velocidad y la ubicación de otros carros y peatones, asi como el estado del semáforo; es decir, los colores del mismo.
- Desires: Desea cruzar la calle o esperar a que otro carro cruce y después de cruzar él cuando le corresponda, sin generar colisiones con otros agentes.
- Intentions es que los carros deciden cuando acelerar, frenar o detenerse en el cruce. Deben obedecer las señales del semáforo para evitar accidentes.

### Peatón:

- Beliefs: Las personas en el cruce tienen información sobre la ubicación y velocidad de los carros cercanos, así como el estado actual del semáforo.
- Desires: Los peatones desean cruzar la calle de manera segura y eficiente. Quieren evitar colisiones con carros y cumplir con las señales del semáforo.
- Intentions: Basados en sus creencias y deseos, las personas deciden cuándo y cómo cruzar la calle. Esto implica esperar en el borde de la acera cuando el semáforo está en rojo y cruzar cuando esté en verde, siempre evaluando la seguridad.

### Semáforo carros:

- Beliefs: Los semáforos tienen conocimiento sobre el estado actual del tráfico en la intersección. Esto incluye información sobre la presencia de carros y diferentes direcciones, así como su cantidad que esperan para cruzar.
- Desires: El deseo principal de un semáforo es regular el flujo de tráfico de manera segura y eficiente. Esto implica permitir que los carros y peatones crucen la intersección de manera ordenada y segura.
- Intentions (Intenciones): En función de sus creencias y deseos, un semáforo toma la decisión de cambiar su estado de luz (rojo, amarillo o verde) para permitir o detener el tráfico en ciertas direcciones y determinar si es necesario mantener más tiempo un determinado color con el fin de eficientizar el trafico en función de la cantidad de carros que estén esperando. Su intención es mantener el orden y la seguridad en la intersección.

### Semáforo peatones:

- Beliefs: Los semáforos tienen conocimiento sobre el estado actual del tráfico en la intersección. Esto incluye información sobre la presencia de peatones y diferentes direcciones, así como su cantidad que esperan para cruzar.
- Desires: El deseo principal de un semáforo es regular el flujo de tráfico de manera segura y eficiente. Esto implica permitir que los peatones crucen la intersección de manera ordenada y segura.
- Intentions (Intenciones): En función de sus creencias y deseos, un semáforo toma la decisión de cambiar su estado de luz (rojo y verde) para permitir o detener el tráfico en ciertas direcciones y determinar si es necesario mantener más tiempo un determinado color con el fin de eficientizar el trafico en función de la cantidad de peatones que estén esperando. Su intención es mantener el orden y la seguridad en la intersección.

## Funciones

![BDI](https://github.com/CodersSquad-Classes/reto-movilidad-urbana-delfines-xd/assets/141982258/580758b7-14c3-4aa9-9397-616733bb36d3)

### BRF (Belief Revision Function)

- Semaforo carros: Cuando el semáforo recibe información de un sensor que detecta la presencia de carros en la intersección, se actualizan las creencias del semáforo sobre el estado actual del tráfico. Por ejemplo, si un sensor detecta a un carro en el cruce, el semáforo debe revisar su creencia sobre la seguridad de cambiar a luz verde para los carros.
- Semaforo peatones: Cuando el semáforo recibe información de un sensor que detecta la presencia de peatones en la intersección, se actualizan las creencias del semáforo sobre el estado actual del tráfico. Por ejemplo, si un sensor detecta a un carro en el cruce, el semáforo debe revisar su creencia sobre la seguridad de cambiar a luz verde para los peatones. También considera el estado de los semaforos adyacentes para tomarlo en consideración al momento de cambiar su estado de colores.
- Carro: Los carros actualizan sus creencias sobre el estado del semáforo y la ubicación de otros agentes en el cruce.
- Peatón: Los peatones también actualizan sus creencias sobre el estado de su semáforo correspondiente y la ubicación de otros peatones.

### Options:

- Aplicación en los semaforos: Un semáforo puede tener varias opciones de cambios de luz en función de las creencias actuales. Puede decidir entre cambiar a luz verde, a luz roja o mantener el estado actual en función de las creencias sobre la seguridad y el flujo de tráfico.
- Aplicación en peatones y carros: Tanto las peatones como los conductores pueden generar opciones de movimiento, como avanzar o detenerse, en función de sus deseos y creencias sobre la seguridad y el estado del semáforo.

### Filter:

- Aplicación en los semaforos: Cuando el semáforo genera opciones para cambiar su luz, el filtro puede seleccionar la opción que minimice el riesgo de colisión y maximice la eficiencia del flujo de tráfico.
- Aplicación en peatones y carros: Los peatones y conductores pueden utilizar el filtro para evaluar las opciones de movimiento en función de sus deseos y creencias sobre la seguridad.

## Clasiﬁcación de Ontología

La ontología es taxonomía formal que describe relaciones y clases en un contexto relacionado con el control de tráfico y agentes en un entorno vial. Esta ontología se ha diseñado utilizando el lenguaje de marcado RDF (Resource Description Framework) y OWL (Web Ontology Language) para estructurar y definir estos conceptos y relaciones de manera precisa. A continuación, se detalla la descripción de las partes más significativas de esta ontología:

**Propiedades de Objeto (Object Properties):**
- `controla`: Esta propiedad simétrica representa la relación de control entre diversos agentes, como semáforos peatonales y vehículos, y objetos de control de tráfico. Esta relación significa que un agente puede controlar otro agente, y viceversa. Tiene dominios y rangos específicos que determinan qué tipos de agentes pueden estar involucrados en esta relación.

- `es_controlado_por`: Esta propiedad es la inversa de `controla`. Define la relación inversa entre los mismos agentes y objetos de control de tráfico, lo que indica quién está controlando a quién.

**Clases (Classes):**
- `Agente`: Representa un tipo de entidad que está relacionada con el control de tráfico en el contexto vial. Se define como una restricción que especifica que un agente está siendo controlado por peatones.

- `Autobus`, `Camion`, `Camioneta`, `Carro` y `Tractor`: Son clases que representan distintos tipos de vehículos. Todas estas clases son subclases de la clase `Vehiculo`.

- `Control_De_Trafico`: Representa un objeto o entidad que tiene la capacidad de controlar aspectos del tráfico en un entorno vial. Esta clase es una subclase de `Agente`.

- `Gato`: Representa una clase de mascotas. Estas mascotas son subclases de `Peatones`, lo que sugiere que están relacionadas con las actividades peatonales.

- `Hombre` y `Mujer`: Son clases que representan a personas, y ambas son subclases de `Peatones`.

- `Mascotas`: Representa una clase de mascotas, que también son subclases de `Peatones`.

- `Personas`: Es una clase general que abarca a las personas, y es una subclase de `Peatones`.

- `Peatones`: Representa una clase que engloba diferentes tipos de agentes peatonales, como personas y mascotas. También es una subclase de `Agente`.

- `Semaforo_Peatonal` y `Semaforo_Vehicular`: Representan semáforos específicos para peatones y vehículos, respectivamente. Ambas clases son subclases de `Control_De_Trafico`.

**Diagrama**

<img width="514" alt="Captura de pantalla 2023-09-01 a la(s) 22 16 39" src="https://github.com/CodersSquad-Classes/reto-movilidad-urbana-delfines-xd/assets/105934515/02fd2950-7521-4e95-82c9-3f2dbd21cf64">
