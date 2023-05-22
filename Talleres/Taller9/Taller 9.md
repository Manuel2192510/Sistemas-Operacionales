\---

title: "Taller 9"

author: "Manuel De Angel 2192510"

date: "2023-05-19"

output: html\_document

\---

\```{r setup, include=FALSE}

knitr::opts\_chunk$set(echo = TRUE)

\```

1\. ¿Cual es significado del termino espera activa?

R/=  Hace referencia a que mientras un proceso ejecuta su sección critica, los demás procesos ejecutan un bucle sin fin en el código de entrada o en otras palabras en vez de dormir el proceso o hilo y despertarlo cuando el evento ocurre, el programa repite constantemente una acción de verificación del estado del evento, consumiendo recursos de CPU mientras tanto.

2\. ¿De que manera se puede evitar la espera activa?

R/= Se puede evitar utilizando técnicas de espera más eficientes, como el bloqueo y la notificación;

en lugar de repetidamente verificar el estado de un evento en un bucle de espera, el proceso o hilo puede bloquearse y esperar a que ocurra el evento, mientras que el sistema operativo lo despierta una vez que el evento ha ocurrido.

3\.Explique por qué los bloqueos mediante bucle sin fin no son apropiados para sistemas

monoprocesador, pero se usan con frecuencia en los sistemas multiprocesador.

R/= No son apropiadas para sistemas monoprocesador porque pueden consumir una cantidad significativa de tiempo de CPU, lo que puede afectar negativamente el rendimiento del sistema.

4\.Explique por qué las interrupciones no son apropiadas para implementar primitivas de

sincronización en los sistemas multiprocesador.

R/=No son apropiadas porque pueden causar problemas de coherencia de caché y de rendimiento. Pueden causar problemas de coherencia de caché porque pueden interrumpir la ejecución de un proceso en un núcleo y transferir el control a otro núcleo para manejar la interrupción.

5\.Describa como se puede utilizar la instrucción swap() para proporcionar un mecanismo de

exclusión mutua que satisfaga el requisito de espera limitada.

R/= Supongamos que tenemos dos procesos, A y B, que desean acceder a una sección crítica de código de manera exclusiva. Además, supongamos que ambos procesos tienen acceso a una variable compartida "turno" que se utiliza para determinar cuál de los dos procesos tiene derecho a acceder a la sección crítica en un momento dado.

El proceso A comienza intentando adquirir el acceso a la sección crítica. En lugar de usar un bucle de espera activa, el proceso A utiliza la instrucción swap() para intercambiar el valor de su variable local "bandera" con el valor de la variable compartida "turno". Si el valor de "turno" es diferente del valor de "bandera", significa que el proceso B tiene el control y el proceso A debe esperar. 

Por lo tanto, el proceso A entra en un bucle while, repitiendo la instrucción swap() hasta que sea su turno de acceder a la sección crítica. Sin embargo, para evitar la espera indefinida, el proceso A también debe utilizar una técnica de espera limitada, como un temporizador o una cuenta de intentos máximos.Una vez que el proceso A tiene elcontrol y ha accedido a la sección crítica, debe liberar el acceso a la misma, establecer la variable "turno" en el valor correspondiente al proceso B y salir de la sección crítica. 

Luego, el proceso B puede intentar adquirir el acceso a la sección crítica siguiendo el mismo proceso: utiliza la instrucción swap() para intentar intercambiar el valor de su variable local "bandera" con el valor de la variable compartida "turno". Si el valor de "turno" es diferente del valor de "bandera", significa que el proceso A tiene el control y el proceso B debe esperar. De esta manera, la instrucción swap() se utiliza para proporcionar un mecanismo de exclusión mutua que garantiza que solo un proceso a la vez pueda acceder a la sección crítica, y que cumple con el requisito de espera limitada al utilizar una técnica de espera limitada para evitar la espera indefinida.

6\.Los servidores pueden diseñarse de modo que limiten el numero de conexiones abiertas.

Explique cómo puede utilizar un servidor los semáforos para limitar el numero de conexiones

concurrentes.

R/= El servidor puede crear un semáforo inicializado con el número máximo de conexiones concurrentes permitidas. Cuando un cliente se conecta al servidor, el servidor intenta adquirir el semáforo. Si el semáforo está disponible, el servidor acepta la conexión y reduce el valor del semáforo en uno. Si el semáforo no está disponible, el servidor rechaza la conexión; cuando un cliente se desconecta, el servidor libera el semáforo, lo que permite que otro cliente se conecte si el número máximo de conexiones aún no se ha alcanzado.

7\.Demuestre que los monitores y semáforos son equivalentes, en cuanto a que se pueden emplear

para implementar los mismos tipos de problemas de sincronización.

R/= Un monitor es una abstracción de alto nivel que proporciona una interfaz segura y sencilla para la sincronización de procesos o hilos. Los monitores utilizan bloqueo y espera para garantizar el acceso exclusivo a un recurso compartido. Solo un proceso o hilo puede estar activo en el monitor en un momento dado. Los monitores también proporcionan una condición de espera que permite a los procesos o hilos esperar a que se cumpla una determinada condición antes de continuar.

Por otro lado, los semáforos son una abstracción de bajo nivel que proporciona una interfaz más primitiva para la sincronización de procesos o hilos. Los semáforos pueden tener un valor entero no negativo y proporcionan dos operaciones atómicas: wait() (espera) y signal() (señal). La operación wait() decrementa el valor del semáforo y bloquea el proceso o hilo si el valor es cero. La operación signal() incrementa el valor del semáforo y desbloquea al siguiente proceso o hilo en espera (si lo hay).

A pesar de estas diferencias, los monitores y semáforos son equivalentes en el sentido de que se pueden utilizar para implementar los mismos tipos de problemas de sincronización. De hecho, los monitores se pueden implementar utilizando semáforos y viceversa. La elección de uno u otro dependerá del nivel de abstracción deseado y de las necesidades específicas de la implementación.

8\. La exclusión mutua estricta en un monitor hace que el monitor de búfer limitado sea adecuado

para porciones pequeñas. Explique por qué es cierto esto.

R/= En el caso de un monitor de búfer limitado, este cerrojo interno se utiliza para garantizar la exclusión mutua en el acceso al búfer compartido. Si un proceso está escribiendo en el búfer, ningún otro proceso puede escribir o leer del búfer al mismo tiempo.

Sin embargo, esta exclusión mutua estricta puede hacer que el monitor de búfer limitado sea adecuado solo para porciones pequeñas. Cuando un proceso adquiere el cerrojo interno del monitor, bloquea a todos los demás procesos que intentan acceder al monitor, incluso si solo quieren leer del búfer. Esto puede resultar en una baja utilización del procesador y una disminución del rendimiento del sistema.

Además, si los procesos realizan operaciones prolongadas dentro del monitor, como esperar a que lleguen datos para escribir en el búfer, bloquearán el monitor durante un período prolongado, lo que puede provocar el bloqueo de otros procesos que esperan acceder al monitoro al búfer.

Por lo tanto, la exclusión mutua estricta en un monitor de búfer limitado puede ser adecuada solo para porciones pequeñas, donde los procesos realizan operaciones rápidas dentro del monitor y no bloquean el monitor durante períodos prolongados. Para porciones grandes, es posible que se deba utilizar una estrategia de exclusión mutua menos restrictiva, como permitir que varios procesos accedan al monitor al mismo tiempo siempre que no estén realizando operaciones en el búfer compartido.

9\.Por qué Windows y Linux utilizan bloqueos mediante bucle sin fin como mecanismo de

sincronización solo en los sistemas multiprocesador y no en los sistemas monoprocesador? 

R/= Los sistemas operativos utilizan bloqueos mediante bucle sin fin como mecanismo de sincronización solo en entornos multiprocesador donde hay posibilidad de conflictos en el acceso a recursos compartidos. En los sistemas operativos monoprocesador, no es necesario utilizar este mecanismo de sincronización, ya que no hay posibilidad de conflictos en el acceso a recursos compartidos y pueden utilizarse otros mecanismos de sincronización más eficientes.
