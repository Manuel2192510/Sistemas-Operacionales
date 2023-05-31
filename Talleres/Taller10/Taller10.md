**Taller 10**

**Manuel De Angel - 2192510**

**UIS - Sistemas Operacionales** 

**Pregunta 1**

**Exclusión mutua:** En la imagen, cada vehículo ocupa un carril exclusivo y no puede ser compartido. **Espera de retención:** Los vehículos mantienen un carril mientras esperan acceso a otro. **No interrupción:** Los vehículos no pueden ser obligados a liberar los carriles que ocupan.* **Espera circular:** Cada vehículo está en espera de que otro libere un recurso. Esta situación se aprecia claramente en la imagen con los autos esperando a que el vehículo anterior se mueva.

<a name="user-content-pregunta-2"></a>**Pregunta 2**

Para evitar interbloqueos en este sistema, se podría implementar una medida preventiva consistente en la introducción de un semáforo o una señal de control. Esta regulación permitiría que solo un carril avance a la vez, evitando así la posibilidad de que los vehículos queden bloqueados entre sí.

<a name="user-content-pregunta-3"></a>**Pregunta 3**

<a name="user-content-respuesta-2"></a>**Asignación ordenada de tenedores:** Los filósofos pueden acordar un protocolo que indique en qué orden deben tomar los tenedores. Por ejemplo, todos los filósofos pueden intentar primero tomar el tenedor a su izquierda y luego el tenedor a su derecha. De esta manera, se garantiza que al menos un filósofo pueda comer a la vez y se evita el interbloqueo.

**Liberación simultánea de tenedores:** Los filósofos pueden acordar liberar ambos tenedores al mismo tiempo después de comer, lo que permite que los demás filósofos los utilicen. Esto evita que un filósofo retenga un tenedor mientras espera el otro, lo que podría conducir al interbloqueo.

**Limitar la cantidad de filósofos concurrentes:** Si el número de filósofos se limita para que sea menor o igual al número de tenedores, se puede garantizar que siempre haya suficientes tenedores disponibles para que todos los filósofos puedan comer al mismo tiempo. Esto elimina la posibilidad de interbloqueo debido a la adquisición simultánea de recursos. 

<a name="user-content-pregunta-4"></a>**Pregunta 4**

Para evitar los interbloqueos en el problema de la cena de los filósofos, es posible tomar medidas que impidan el cumplimiento de una de las condiciones básicas del problema. Aquí se explican dos enfoques para evitar los interbloqueos al violar cada una de las condiciones:

**Impedir la adquisición simultánea de recursos:**

Para evitar que todos los filósofos intenten adquirir los tenedores al mismo tiempo y entren en un estado de interbloqueo, se puede utilizar un mecanismo de exclusión mutua. Por ejemplo, se puede utilizar un semáforo o un monitor para garantizar que solo un filósofo a la vez pueda intentar tomar los tenedores. Cada filósofo solicitaría el acceso al recurso compartido (los tenedores) y esperaría hasta que se le conceda el acceso antes de intentar tomar los tenedores. Esto asegura que solo un filósofo adquiera los tenedores a la vez y evita el interbloqueo por adquisición simultánea de recursos.

**Evitar la espera circular:**

Para evitar la espera circular, se puede establecer un orden de prioridad en la forma en que los filósofos adquieren los tenedores. Por ejemplo, se puede numerar cada tenedor y establecer una regla que requiera que los filósofos siempre tomen los tenedores en orden ascendente. De esta manera, si un filósofo no puede adquirir su segundo tenedor, lo colocará de vuelta y lo intentará más tarde, evitando que otros filósofos se queden esperando por los tenedores. Esta estrategia rompe la condición de espera circular y evita el interbloqueo.

Al violar una de estas condiciones, se puede garantizar que los filósofos no queden atrapados en un estado de espera indefinida y que no se produzcan interbloqueos. Sin embargo, es importante tener en cuenta que cada enfoque puede requerir una implementación cuidadosa para garantizar que se mantenga la justicia en la asignación de recursos y evitar otros problemas, como la inanición (starvation) de algunos filósofos.

**Pregunta 5**

<a name="user-content-respuesta-4"></a><a name="user-content-pregunta-6"></a>En términos del tiempo de ejecución adicional necesario, el esquema de espera circular en el problema de la cena de los filósofos puede llevar a un tiempo de ejecución considerablemente mayor en comparación con los diferentes esquemas de evasión de interbloqueos.

En el esquema de espera circular, los filósofos toman los tenedores en un orden fijo y siempre esperan el tenedor adicional necesario. Esto puede resultar en una espera prolongada para que cada filósofo adquiera ambos tenedores. Si un filósofo no puede obtener el tenedor requerido, se coloca en espera y se produce un ciclo de espera, lo que lleva a un retraso en el progreso del sistema. Además, si todos los filósofos están esperando en un estado circular, el sistema quedará estancado y no se realizará ninguna acción hasta que se liberen los recursos necesarios. Esto puede resultar en un tiempo de ejecución adicional significativo y un bajo rendimiento general del sistema.

En contraste, los diferentes esquemas de evasión de interbloqueos, como la asignación asimétrica de tenedores o el uso de mecanismos de exclusión mutua, pueden evitar el interbloqueo sin incurrir en un tiempo de ejecución adicional significativo. Estos esquemas permiten un mejor aprovechamiento de los recursos y evitan situaciones en las que todos los filósofos esperan indefinidamente. Al establecer reglas claras sobre el orden de adquisición de los tenedores o utilizar mecanismos de sincronización adecuados, se puede garantizar que los filósofos puedan avanzar en su ciclo de pensar y comer sin quedar atrapados en estados de espera prolongados.

En resumen, el esquema de espera circular puede llevar a un tiempo de ejecución adicional considerable en comparación con los esquemas de evasión de interbloqueos, que permiten un mejor aprovechamiento de los recursos y evitan que los filósofos queden atrapados en estados de espera indefinidos.

**Pregunta 6**

En el esquema de espera circular, los filósofos están sujetos a una espera indefinida cuando no pueden adquirir ambos tenedores al mismo tiempo. Esto puede llevar a una situación en la que todos los filósofos están esperando que se liberen los recursos necesarios, lo que resulta en una baja tasa de procesamiento del sistema. A medida que aumenta el número de filósofos y tenedores, aumenta la probabilidad de que ocurra el interbloqueo circular y se reduzca aún más la tasa de procesamiento.

Por otro lado, los diferentes esquemas de evasión de interbloqueos están diseñados para evitar el interbloqueo y maximizar la tasa de procesamiento del sistema. Estos esquemas pueden permitir que los filósofos adquieran los recursos de manera más eficiente, sin quedar atrapados en estados de espera prolongados. Por ejemplo, en el caso de la asignación asimétrica de tenedores, se asegura que al menos un filósofo pueda comer a la vez, lo que mejora la tasa de procesamiento en comparación con el esquema de espera circular. Del mismo modo, el uso de mecanismos de exclusión mutua garantiza que solo un filósofo a la vez intente adquirir los tenedores, evitando esperas innecesarias.

**Pregunta 7**

<a name="user-content-pregunta-8"></a>Para demostrar que el sistema está libre de interbloqueos en este escenario, podemos analizar exhaustivamente las asignaciones de recursos posibles para los tres procesos.

Dado que hay cuatro recursos disponibles y cada proceso necesita como máximo dos recursos, podemos considerar todas las combinaciones posibles de asignación de recursos. Veamos cada una de ellas

1\. **Asignar dos recursos al primer proceso y dos recursos al segundo proceso:**

`   `En este caso, no quedan recursos disponibles, ya que los cuatro están asignados. El tercer proceso no puede obtener recursos adicionales y se mantiene en espera. Sin embargo, dado que el tercer proceso solo necesita como máximo dos recursos y no hay suficientes recursos disponibles, no puede entrar en un estado de espera circular. Por lo tanto, no se produce un interbloqueo.

2\. **Asignar tres recursos al primer proceso y uno al segundo proceso:**

`   `En este caso, aún queda un recurso disponible. El tercer proceso puede obtener este recurso disponible, ya que solo necesita como máximo dos recursos. No hay procesos en espera y no se produce un interbloqueo.

3\. **Asignar un recurso al primer proceso, dos recursos al segundo proceso y uno al tercer proceso:**

`   `En esta asignación, todavía queda un recurso disponible. El primer proceso puede obtener este recurso, ya que solo necesita como máximo dos recursos. No hay procesos en espera y no se produce un interbloqueo.

En cada una de las asignaciones posibles, se garantiza que los procesos no queden atrapados en estados de espera indefinidos y que no se produzca un interbloqueo. Por lo tanto, podemos concluir que el sistema está libre de interbloqueos en este escenario específico.

Es importante tener en cuenta que este análisis se basa en la configuración particular de los recursos y las necesidades de los procesos en este escenario. Si se modifican las cantidades de recursos o los requisitos de los procesos, es necesario realizar un análisis adicional para verificar si el sistema sigue siendo libre de interbloqueos.

**Pregunta 8**

<a name="user-content-pregunta-9"></a>En el problema de los filósofos, donde los palillos se colocan en el centro de la mesa y cada filósofo puede usar dos palillos, una regla simple para determinar si una solicitud de palillos podría ser satisfecha sin dar lugar a interbloqueos, dada la asignación actual de palillos a los filósofos, es verificar que al menos uno de los palillos requeridos esté disponible.

Cuando un filósofo desea realizar una solicitud de palillos, se debe verificar que al menos uno de los dos palillos requeridos esté disponible y no esté ocupado por otro filósofo. Si al menos uno de los palillos requeridos está disponible, el filósofo puede tomar ese palillo y esperar a que el segundo palillo esté disponible para completar su solicitud y proceder a comer. Esta regla simple garantiza que el filósofo no se quede esperando indefinidamente por ambos palillos y evita el interbloqueo.

Sin embargo, si ninguno de los dos palillos requeridos por el filósofo está disponible, es necesario denegar la solicitud para evitar posibles interbloqueos. En ese caso, el filósofo debe esperar a que se liberen los palillos necesarios antes de poder realizar su solicitud.

Esta regla simple permite que los filósofos avancen y tomen los palillos disponibles sin quedar atrapados en situaciones de espera circular, lo que podría conducir a un interbloqueo. Al verificar la disponibilidad de al menos uno de los palillos requeridos antes de otorgar una solicitud, se puede garantizar un progreso continuo en el problema de los filósofos sin interbloqueos.

**Pregunta 9**

La suposición optimista realizada en el algoritmo de detección de interbloqueos, como el algoritmo del banquero, es que cada proceso especifica de antemano el número máximo de recursos que necesitará en algún momento de su ejecución. Esta suposición optimista es necesaria para que el algoritmo funcione correctamente.

La suposición se basa en la idea de que los procesos no excederán sus necesidades máximas de recursos y que no realizarán solicitudes adicionales una vez que hayan alcanzado su máximo especificado. Esto implica que los recursos asignados a un proceso no serán liberados y solicitados nuevamente por el mismo proceso mientras aún se necesiten.

Sin embargo, esta suposición optimista puede violarse si un proceso realiza solicitudes adicionales de recursos después de haber alcanzado su máximo especificado. Esto podría ocurrir si un proceso cambia dinámicamente sus necesidades de recursos durante su ejecución o si se produce un error en la implementación del programa y se realizan solicitudes adicionales de manera incorrecta.

Si un proceso viola esta suposición optimista y realiza solicitudes adicionales de recursos después de alcanzar su máximo, podría generar una condición de interbloqueo. Esto se debe a que el algoritmo del banquero y otros algoritmos de detección de interbloqueos asumen que los procesos no solicitarán más recursos de los especificados previamente. Si esta suposición es violada, el algoritmo podría otorgar recursos adicionales a un proceso y no tener suficientes recursos para satisfacer las solicitudes de otros procesos, lo que podría conducir a un estado de interbloqueo.

Por lo tanto, es importante que los procesos respeten la suposición optimista y no realicen solicitudes adicionales de recursos después de alcanzar su máximo especificado para garantizar el correcto funcionamiento de los algoritmos de detección de interbloqueos.
