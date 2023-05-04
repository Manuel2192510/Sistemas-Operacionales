Manuel De Angel

Codigo de estudiante: 2192510

Taller06

2023-05-03

Pregunta 1:

1.1 Operaciones de entrada/salida (I/O-bound): Si una aplicación está realizando principalmente operaciones de entrada/salida, como leer o escribir en un archivo o enviar y recibir datos a través de una red, el uso de múltiples hilos puede no proporcionar una mejora significativa en el rendimiento. Esto se debe a que la mayoría del tiempo se gastará esperando que se completen las operaciones de entrada/salida y no se aprovechará al máximo el uso de múltiples hilos. Además, el uso excesivo de hilos puede aumentar la sobrecarga del sistema y reducir el rendimiento general.

1.2 Operaciones de computación intensiva (CPU-bound) en sistemas con un solo núcleo: Si una aplicación está realizando principalmente operaciones de computación intensiva en un sistema con un solo núcleo, el uso de múltiples hilos puede no proporcionar una mejora significativa en el rendimiento. Esto se debe a que, aunque los hilos adicionales pueden ayudar a dividir la carga de trabajo, todos los hilos compiten por el mismo recurso del procesador, lo que puede provocar una sobrecarga y un rendimiento reducido. En este caso, la mejor opción puede ser utilizar un enfoque de programación secuencial o paralelismo a nivel de proceso para aprovechar al máximo los recursos del sistema.

Pregunta 2:

2.1 Planificación: La biblioteca de hilos debe tener un planificador de hilos que decida qué hilo se ejecutará a continuación. El planificador puede utilizar una variedad de algoritmos de planificación, como round-robin, prioridad o basado en eventos.

2.2 Interrupción de hilos: Cuando se produce una interrupción, como una operación de entrada/salida o una señal de temporizador, la biblioteca de hilos debe detener el hilo actualmente en ejecución y seleccionar otro hilo para ejecutar. El planificador de hilos se encarga de tomar esta decisión.

2.3 Cambio de contexto: Cuando se selecciona un nuevo hilo para ejecutar, la biblioteca de hilos debe realizar un cambio de contexto para cambiar del hilo actualmente en ejecución al nuevo hilo. Esto puede implicar guardar el estado del hilo actual, como los registros de la CPU y la pila, y restaurar el estado del nuevo hilo.

2.4 Sincronización: Los hilos pueden compartir recursos, como memoria o archivos. La biblioteca de hilos debe proporcionar mecanismos de sincronización para garantizar que los recursos se utilicen de manera segura y que no se produzcan condiciones de carrera o bloqueos. Los mecanismos de sincronización comunes incluyen semáforos, mutex y variables de condición.

2.5 Finalización de hilos: Cuando un hilo ha terminado de ejecutarse, la biblioteca de hilos debe liberar los recursos asociados con el hilo y eliminarlo de la lista de hilos activos. También puede proporcionar mecanismos para que otros hilos esperen a que un hilo termine, como join().

Pregunta 3:

Depende del tipo de registro al que se esté refiriendo; ya que los registros de uso general, como los registros de la CPU que almacenan valores de datos y direcciones de memoria, son compartidos por todos los hilos de un proceso multihilo, mientras que existen registros especiales que no son compartidos entre los hilos.

Pregunta 4:

Los cúmulos de memoria (heap) de un proceso multihilo son compartidos entre todos los hilos del proceso. Esto se debe a que el cúmulo de memoria es un recurso compartido utilizado por todos los hilos para asignar y liberar memoria dinámicamente durante la ejecución del programa.

Pregunta 5:

Sí, las variables globales se comparten entre los hilos de un proceso multihilo. Esto se debe a que las variables globales se almacenan en una sección de memoria compartida que se encuentra fuera del ámbito de cualquier función o hilo específico. Todos los hilos del proceso pueden acceder a esta sección de memoria y leer o escribir en las variables globales.

Pregunta 6:

No, la memoria de pila no se comparte entre los hilos de un proceso multihilo. Cada hilo tiene su propia pila, que es una sección de memoria reservada para almacenar datos locales y registros de activación de funciones. Los registros de activación de funciones son estructuras de datos que contienen información sobre las variables locales, los parámetros de la función y la dirección de retorno de la función.

Pregunta 7:

7.1 Operaciones de entrada/salida (I/O-bound): Si una aplicación realiza principalmente operaciones de entrada/salida, como leer o escribir en un archivo o enviar y recibir datos a través de una red, el uso de múltiples hilos puede mejorar significativamente el rendimiento. Mientras que un hilo está esperando a que se complete una operación de entrada/salida, otro hilo puede realizar cálculos o realizar otras operaciones. Esto puede proporcionar un uso más eficiente del tiempo de CPU y mejorar el rendimiento general.

7.2 Operaciones de computación intensiva (CPU-bound) en sistemas con múltiples núcleos: Si una aplicación realiza principalmente operaciones de computación intensiva en un sistema con múltiples núcleos, el uso de múltiples hilos puede mejorar significativamente el rendimiento. Cada hilo puede ejecutarse en un núcleo separado, lo que permite un uso más eficiente de los recursos del procesador y puede reducir el tiempo total de procesamiento.

7.3 Procesamiento paralelo: Si una aplicación puede dividirse en subprocesos independientes que pueden ejecutarse simultáneamente, el uso de múltiples hilos puede proporcionar un rendimiento significativamente mejor que un solo hilo. Por ejemplo, en una aplicación de renderizado de video, cada fotograma puede procesarse en un hilo separado, lo que permite que se procesen varios fotogramas al mismo tiempo y acelera el proceso de renderizado.

Pregunta 8:

Sí, una solución multihilo que utiliza múltiples hilos de usuario puede conseguir mejor rendimiento en un sistema multiprocesador que en un sistema de un solo procesador. Esto se debe a que en un sistema multiprocesador, hay múltiples núcleos de procesador que pueden ejecutar hilos simultáneamente. Si la solución multihilo está diseñada para aprovechar estos núcleos, puede haber una mejora significativa en el rendimiento.

Pregunta 9:

Puede haber un impacto negativo en el rendimiento debido a la espera de recursos del procesador. Es importante diseñar cuidadosamente la asignación y programación de los hilos para minimizar la espera y maximizar la utilización de los recursos del sistema.
