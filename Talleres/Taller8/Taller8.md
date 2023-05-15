Taller_08
Presentado por:
Manuel De Angel
Cod. De estudiante 2192510
Presentado a:
Pablo J. Rojas 
Sistemas Operacionales
Cod. De asignatura 22972
13/05/2023


1.	¿Por qué es importante para un planificador diferenciar entre un programa limitado por I/O y por CPU?
R/= Es importante para que el planificador pueda tomar decisiones informadas y maximizar la utilización de los recursos del sistema para mejorar el rendimiento general del sistema.
2.	¿Como entran en conflicto en determinadas configuraciones la utilización de CPU y tiempo de respuesta?
La utilización de la CPU y el tiempo de respuesta pueden entrar en conflicto en determinadas configuraciones debido a la limitación de recursos del sistema. Los administradores del sistema pueden utilizar técnicas de planificación y gestión de recursos para equilibrar la carga de trabajo y optimizar el rendimiento del sistema.
3.	¿Como entran en conflicto en determinadas configuraciones el tiempo medio de procesamiento y tiempo máximo de espera?
En determinadas configuraciones, el tiempo medio de procesamiento y el tiempo máximo de espera pueden entrar en conflicto debido a la limitación de recursos y la carga de trabajo en el sistema.
El tiempo medio de procesamiento se refiere al tiempo promedio que un proceso o tarea tarda en completarse en el sistema. Por otro lado, el tiempo máximo de espera se refiere al tiempo máximo que un proceso o tarea debe esperar en la cola de procesamiento antes de ser atendido por el sistema.
En un sistema con carga de trabajo alta, puede haber una gran cantidad de procesos en la cola de procesamiento, lo que puede aumentar el tiempo máximo de espera. Si se da prioridad a la reducción del tiempo máximo de espera, es posible que se deba aumentar la capacidad del sistema, lo que puede aumentar el costo y la complejidad del diseño del sistema.
Por otro lado, si se da prioridad a la reducción del tiempo medio de procesamiento, es posible que se deba sacrificar el tiempo máximo de espera, lo que puede afectar negativamente la satisfacción del usuario y la experiencia del cliente.
En la práctica, los administradores del sistema deben encontrar un equilibrio entre el tiempo medio de procesamiento y el tiempo máximo de espera para optimizar el rendimiento del sistema y garantizar una experiencia satisfactoria para el usuario. Esto puede implicar la utilización de técnicas de planificación y gestión de recursos para priorizar los procesos y tareas en función de sus requerimientos de tiempo de respuesta, y la optimización de la capacidad del sistema para manejar la carga de trabajo actual y futura.
4.	Como entran en conflicto en determinadas configuraciones la utilización de los dispositivos I/O y la utilización de la CPU? 
Cuando un proceso realiza una operación de entrada/salida, se debe esperar a que se complete la operación antes de que el proceso pueda continuar. Durante este tiempo, la CPU no está haciendo nada y se desperdician recursos valiosos. Además, el tiempo de espera asociado con la operación de entrada/salida puede ser considerable, especialmente si se trata de una operación de lectura o escritura en un dispositivo de almacenamiento externo lento.
Por otro lado, si un proceso utiliza intensivamente la CPU, puede reducir la capacidad del sistema para manejar las operaciones de entrada/salida en tiempo real. Si hay muchos procesos compitiendo por recursos de CPU limitados, las operaciones de entrada/salida pueden experimentar cuellos de botella y retrasos significativos.
Para evitar estos problemas, los administradores del sistema pueden utilizar técnicas de planificación y gestión de recursos para equilibrar la carga de trabajo entre los procesos y optimizar el rendimiento del sistema. Por ejemplo, pueden utilizar técnicas de priorización para asegurarse de que los procesos de entrada/salida de alta prioridad se manejen de manera oportuna, o pueden utilizar técnicas de caché para reducir la cantidad de tiempo necesaria para realizar operaciones de entrada/salida.
5.	Dibuje el diagrama de Gantt para FCFS, SJF, por prioridades (# de prioridad baja = a alta prioridad) y RR (cuanto = 1). (Tomé uno como mas alta prioridad y 5 como la mas baja)

 
6.	¿Cuál es el tiempo de ejecución de cada proceso para cada algoritmo?
Prioridades:
P2: 1 ms
P5: 5 ms
P1: 10 ms
P3: 2 ms
P4: 1 ms
Round Robin:
P1: 9 ms
P2: 1 ms
P3: 2 ms
P4: 1 ms
P5: 5 ms
SJF:
P2: 1 ms
P4: 1 ms
P3: 2 ms
P5: 5 ms
P1: 10 ms
FCFS según tiempo de ráfaga sin prioridades:
P2: 1 ms
P4: 1 ms
P3: 2 ms
P5: 5 ms
P1: 10 ms
FCFS:
P1: 10 ms
P2: 1 ms
P3: 2 ms
P4: 1 ms
P5: 5 ms
7.	¿Cuál es el tiempo de espera de cada proceso para cada algoritmo?
FCFS: 
P1: 0 milisegundos
P2: 10 milisegundos (tiempo de ejecución de P1)
P3: 11 milisegundos (tiempo de ejecución de P1 y P2)
P4: 13 milisegundos (tiempo de ejecución de P1, P2 y P3)
P5: 14 milisegundos (tiempo de ejecución de P1, P2, P3 y P4)
FCFS según tiempo de ráfaga (sin prioridades): 
P2: 0 milisegundos
P4: 1 milisegundos (tiempo de ejecución de P2)
P3: 2 milisegundos (tiempo de ejecución de P2 y P4)
P5: 4 milisegundos (tiempo de ejecución de P2, P4 y P3)
P1: 9 milisegundos (tiempo de ejecución de P2, P4, P3 y P5)
SJF:
 P2: 0 milisegundos
P4: 1 milisegundos (tiempo de ejecución de P2)
P3: 2 milisegundos (tiempo de ejecución de P2 y P4)
P5: 4 milisegundos (tiempo de ejecución de P2, P4 y P3)
P1: 9 milisegundos (tiempo de ejecución de P2, P4, P3 y P5)
Según Prioridad:
P2: 0 ms
P5: 1 ms (tiempo de ejecución de P2)
P1: 6 ms (tiempo de ejecución de P2 y P5)
P3: 16 ms (tiempo de ejecución de P2, P5 y P1)
P4: 18 ms (tiempo de ejecución de P2, P5, P1 y P3)
Round Robin: 
P1:  Tiempo de espera: 0 ms
P2: Tiempo de espera: 9 ms
P3: Tiempo de espera: 10 ms
P4: Tiempo de espera: 12 ms
P5: Tiempo de espera: 13 ms
8.	¿Qué algoritmo puede dar lugar a bloqueos indefinidos?
R/= Planificación por prioridades
9.	Considere un sistema que implementa una planificación por colas multinivel. ¿Qué estrategia puede utilizar una computadora para maximizar la cantidad de tiempo de CPU asignada al proceso del usuario?
Utilizar un algoritmo de planificación que tenga en cuenta la proporción de tiempo de CPU asignado a cada proceso ó asignar una prioridad más alta a los procesos del usuario en las colas de mayor prioridad.
