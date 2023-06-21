---
title: "Taller 12-Investigación 9"
author: "Manuel De Angel 2192510"
date: "2023-06-16"
output: html_document
---
# <a name="pregunta-1"></a>**Pregunta 1**
Explique el soporte por hardware requerido para implementar la paginación bajo demanda
## <a name="respuesta"></a>**Respuesta:**
Unidad de gestión de memoria (Memory Management Unit, MMU): La MMU es un componente del procesador responsable de la traducción de direcciones virtuales a direcciones físicas. La MMU utiliza una tabla de páginas (page table) para realizar esta traducción. En el contexto de la paginación bajo demanda, la MMU debe ser capaz de identificar cuando una página solicitada no está presente en la memoria física y generar una interrupción para cargar la página desde el almacenamiento secundario.

Tabla de páginas (Page Table): La tabla de páginas es una estructura de datos utilizada por la MMU para realizar la traducción de direcciones virtuales a direcciones físicas. Cada entrada de la tabla de páginas contiene información sobre una página de memoria virtual, como su estado (presente o ausente en la memoria física), su dirección física correspondiente y otros atributos. En el caso de la paginación bajo demanda, las entradas de la tabla de páginas pueden tener un bit adicional para indicar si una página está presente en la memoria física o si se necesita cargar desde el almacenamiento secundario.

Almacenamiento secundario: La paginación bajo demanda implica cargar páginas desde el almacenamiento secundario (como un disco duro) cuando no están presentes en la memoria física. Por lo tanto, es necesario tener un medio de almacenamiento secundario disponible y accesible para poder recuperar las páginas solicitadas cuando sea necesario.

Mecanismo de interrupción: El hardware debe tener un mecanismo de interrupción para gestionar las solicitudes de página que no están presentes en la memoria física. Cuando se accede a una página que no está cargada en la memoria física, se genera una interrupción que detiene la ejecución normal del programa y permite al sistema operativo cargar la página correspondiente antes de continuar.

# <a name="pregunta-2"></a>**Pregunta 2**
¿Qué es la característica de copia durante la escritura y en que circunstancias es ventajoso usar estas características?
## <a name="respuesta"></a>**Respuesta:**
Además, la copia durante la escritura es especialmente ventajosa en situaciones en las que los datos compartidos son principalmente de lectura y se realizan pocas operaciones de escritura. En estos casos, se evita la sobrecarga de copiar los datos completos cada vez que se realiza una escritura, lo que puede ser costoso en términos de tiempo y recursos.

Algunas circunstancias en las que la característica de copia durante la escritura es ventajosa incluyen:

Sistemas de archivos: Cuando se realiza una copia de un archivo para realizar modificaciones, la copia durante la escritura evita tener que copiar todo el archivo de inmediato. En su lugar, se comparte el mismo bloque de datos hasta que se realice una escritura en una de las copias, momento en el cual se crea una copia independiente.

Máquinas virtuales y contenedores: Al crear instancias de máquinas virtuales o contenedores basados en imágenes existentes, la copia durante la escritura permite compartir recursos de memoria y disco entre las instancias, reduciendo el consumo de memoria y el tiempo necesario para clonar completamente la imagen.

Snapshotting: Al tomar instantáneas o "snapshots" de un sistema o de un conjunto de datos, la copia durante la escritura permite compartir los mismos datos entre el estado original y la instantánea, evitando así la necesidad de duplicar los datos completos en el momento de la creación de la instantánea.

# <a name="pregunta-3"></a>**Pregunta 3**
¿Cual es el soporte de hardware requerido para implementar las características de copia durante escritura?
## <a name="respuesta"></a>**Respuesta:**
La implementación de la característica de copia durante la escritura (copy-on-write) puede requerir cierto soporte de hardware para su funcionamiento eficiente. A continuación, se describen algunos elementos de hardware que pueden ser necesarios o beneficiosos para implementar esta característica:

1. Memoria virtual y protección de memoria: La característica de copia durante la escritura generalmente se utiliza en el contexto de la gestión de memoria virtual. Por lo tanto, se requiere soporte de hardware para la implementación de memoria virtual, incluyendo la capacidad de dividir la memoria en páginas y realizar traducción de direcciones virtuales a direcciones físicas. Además, se necesitan mecanismos de protección de memoria para controlar el acceso a las páginas compartidas y garantizar su integridad.

2. MMU (Unidad de Gestión de Memoria): La MMU es un componente del procesador responsable de la traducción de direcciones virtuales a direcciones físicas. En el contexto de la copia durante la escritura, la MMU debe ser capaz de manejar las referencias compartidas a las mismas páginas físicas, asegurándose de que los procesos o entidades compartan la misma ubicación de memoria. Además, la MMU debe ser capaz de detectar y manejar las escrituras en las páginas compartidas, desencadenando la creación de copias independientes cuando sea necesario.

3. Soporte de interrupciones y control de excepciones: Es posible que se necesite soporte de hardware para interrupciones y manejo de excepciones para facilitar la detección y el manejo de operaciones de escritura en páginas compartidas. Esto puede implicar la generación de interrupciones o excepciones cuando se intenta escribir en una página compartida y la realización de las acciones necesarias para crear una copia independiente.

4. Mecanismos de bifurcación de procesos o clonación de páginas: Para implementar la copia durante la escritura en el contexto de procesos o entidades clonadas, puede ser beneficioso contar con mecanismos de hardware que faciliten la bifurcación de procesos o la clonación de páginas. Estos mecanismos permiten crear copias independientes de las páginas compartidas cuando se realiza una escritura en una de las copias.

Es importante destacar que la implementación de la copia durante la escritura puede variar dependiendo del sistema operativo y la arquitectura de hardware específica. Por lo tanto, el soporte de hardware requerido puede diferir en cada caso particular. 

# <a name="pregunta-4"></a>**Pregunta 4**
Indique una situación en la que el algoritmo de sustitución de las páginas menos frecuentes utilizadas genere menos fallos de pagina que el algoritmo de sustitución de las paginas más recientemente utilizadas.
## <a name="respuesta"></a>**Respuesta:**
Una situación en la que el algoritmo de sustitución de las páginas menos frecuentemente utilizadas (LFU, por sus siglas en inglés) genere menos fallos de página que el algoritmo de sustitución de las páginas más recientemente utilizadas (LRU, por sus siglas en inglés) es cuando el acceso a las páginas sigue un patrón de uso no frecuente pero con una alta persistencia.

Imaginemos un escenario donde un programa tiene un conjunto de páginas en memoria y, en un momento dado, necesita acceder a un pequeño subconjunto de páginas de forma regular pero no frecuente. Estas páginas son necesarias para realizar tareas específicas, pero no se accede a ellas con la misma frecuencia que a otras páginas en el sistema.

En este caso, el algoritmo LFU podría tener un mejor desempeño que LRU. El LFU se basa en el principio de que las páginas utilizadas con menos frecuencia deben ser reemplazadas primero. Si las páginas de acceso poco frecuente pero persistente se mantienen en memoria debido a su alta persistencia, el LFU las considerará menos candidatas a ser reemplazadas. Por lo tanto, el LFU tendrá menos probabilidades de reemplazar estas páginas y, en consecuencia, generará menos fallos de página.

Por otro lado, el algoritmo LRU se basa en el principio de que las páginas utilizadas más recientemente son las más probables de ser utilizadas nuevamente en el futuro cercano. Si las páginas de acceso poco frecuente pero persistente no se han accedido recientemente, el algoritmo LRU podría considerarlas como candidatas a ser reemplazadas. Como resultado, puede haber un mayor número de fallos de página en comparación con el LFU.

Es importante tener en cuenta que el desempeño de los algoritmos de sustitución de página depende en gran medida del patrón de acceso a las páginas y de la naturaleza del sistema en particular. En diferentes escenarios y con diferentes patrones de acceso, el resultado puede variar. Por lo tanto, es importante evaluar el comportamiento del sistema y considerar las características específicas antes de elegir un algoritmo de sustitución de página adecuado.

# <a name="pregunta-5"></a>**Pregunta 5**
Indique una situación en la que el algoritmo de sustitución de las páginas mas frecuentemente utilizadas genere menos fallos de página que el algoritmo de sustitución de las páginas menos recientemente utilizadas
## <a name="respuesta"></a>**Respuesta:**
Una situación en la que el algoritmo de sustitución de las páginas más frecuentemente utilizadas (MFU, por sus siglas en inglés) genere menos fallos de página que el algoritmo de sustitución de las páginas menos recientemente utilizadas (LRU, por sus siglas en inglés) es cuando hay un conjunto de páginas que son muy frecuentemente accedidas durante todo el tiempo de ejecución del programa.

Supongamos un escenario en el que hay un pequeño conjunto de páginas que se utilizan intensivamente y se accede a ellas con mucha frecuencia. Estas páginas son críticas para el funcionamiento continuo y eficiente del programa, y su acceso es constante durante toda la ejecución.

En este caso, el algoritmo MFU podría tener un mejor desempeño que LRU. El MFU se basa en el principio de que las páginas utilizadas con mayor frecuencia son las más importantes y deben tener prioridad para permanecer en memoria. Dado que estas páginas son accedidas repetidamente, el MFU las considerará altamente frecuentes y las mantendrá en memoria durante más tiempo, reduciendo así la probabilidad de fallos de página.

Por otro lado, el algoritmo LRU se basa en el principio de que las páginas utilizadas más recientemente son las más probables de ser utilizadas nuevamente en el futuro cercano. Si bien las páginas intensivamente utilizadas se acceden frecuentemente, también se acceden a otras páginas menos críticas pero más recientes, lo que puede hacer que LRU las considere como páginas más importantes y las mantenga en memoria.

# <a name="pregunta-6"></a>**Pregunta 6**
Un sistema utiliza un algoritmo de sustitución FIFO para las paginas resientes y un conjunto
compartido de marcos libres compuesto por páginas recientemente utilizadas. Si el conjunto
compartido de marcos libres se gestiona utilizando la política de sustitución menos
recientemente utilizadas. De una respuesta a los siguientes casos:
◦ Si se produce un fallo de página y la página se encuentra en el conjunto compartidos de
marcos libres, ¿cómo puede generarse espacio libre para la nueva página solicitada?
◦ Si se produce un fallo de página y la página se encuentra en el conjunto compartido de
marcos libres, ¿cómo se activa la página residente y cómo se gestiona el conjunto
compartido de marcos libres para hacer sitio para la página solicitada?
## <a name="respuesta"></a>**Respuesta:**
En el escenario descrito, donde se utiliza un algoritmo de sustitución FIFO para las páginas recientes y un conjunto compartido de marcos libres gestionado mediante la política de sustitución menos recientemente utilizadas (LRU), se pueden abordar los casos de fallos de página de la siguiente manera:

1. Si se produce un fallo de página y la página solicitada se encuentra en el conjunto compartido de marcos libres, se puede generar espacio libre para la nueva página solicitada de la siguiente manera:

   a. Se selecciona la página menos recientemente utilizada del conjunto compartido de marcos libres según la política LRU. Esta página será reemplazada para dar lugar a la nueva página solicitada.
   
   b. La página seleccionada se marca como no residente y se elimina del conjunto compartido de marcos libres.
   
   c. La nueva página solicitada se carga en el marco libre liberado por la página seleccionada.
   
   De esta manera, se genera espacio libre en los marcos de memoria para acomodar la nueva página solicitada. La página menos recientemente utilizada del conjunto compartido de marcos libres es reemplazada, lo que garantiza que se cumpla la política LRU.

2. Si se produce un fallo de página y la página solicitada se encuentra en el conjunto compartido de marcos libres, la página residente se activa y se gestiona de la siguiente manera:

   a. La página residente que se encuentra en el conjunto compartido de marcos libres se selecciona para su activación y uso.
   
   b. La página seleccionada se marca como residente y se carga en un marco de memoria disponible.
   
   c. La página seleccionada se elimina del conjunto compartido de marcos libres, ya que ahora está en uso y se considera una página residente.
   
En este caso, no se requiere generar espacio libre para la nueva página solicitada, ya que se activa una página existente en el conjunto compartido de marcos libres. La página seleccionada se mueve a la memoria principal y se marca como residente para su uso continuo.

# <a name="pregunta-7"></a>**Pregunta 7**
Considere un sistema de paginación bajo demanda con las siguientes tasas de utilización:

-Uso de CPU 20%
-Paginación de disco 97,7%
-Otros dispositivos de I/O 5%
Para las siguientes afirmaciones, indique si permitirá o es probable que permita mejorar las tasas de utilización de la CPU. De razones para su respuesta.

-Instalar una CPU más rápida.
-Instalar un disco de paginación de mayor tamaño.
-Incrementar el grado de multiprogramación.
-Instalar mas memoria principal.
-Instalar un disco duro mas rápidos.
## <a name="respuesta"></a>**Respuesta:**
1. Instalar una CPU más rápida: Sí, instalar una CPU más rápida permitiría mejorar la tasa de utilización de la CPU. Una CPU más rápida puede procesar las instrucciones y tareas más eficientemente, lo que podría reducir el tiempo de ejecución de los procesos y aumentar la capacidad de procesamiento de la CPU. Esto puede resultar en una mayor utilización de la CPU y, potencialmente, en un mejor rendimiento general del sistema.

2. Instalar un disco de paginación de mayor tamaño: No, instalar un disco de paginación de mayor tamaño no mejorará directamente la tasa de utilización de la CPU. El tamaño del disco de paginación está más relacionado con la capacidad de almacenamiento y el rendimiento del sistema de paginación, que afecta principalmente a la eficiencia de la gestión de memoria y a la reducción de los fallos de página. Si bien una gestión de memoria más eficiente puede tener un impacto indirecto en la utilización de la CPU, el tamaño del disco de paginación en sí no está directamente relacionado con la tasa de utilización de la CPU.

3. Incrementar el grado de multiprogramación: Sí, incrementar el grado de multiprogramación puede permitir mejorar la tasa de utilización de la CPU. La multiprogramación se refiere a la capacidad del sistema operativo para ejecutar múltiples procesos al mismo tiempo. Al aumentar el grado de multiprogramación, se permite que más procesos se ejecuten simultáneamente, lo que puede aumentar la utilización de la CPU al proporcionarle más tareas para procesar en paralelo.

4. Instalar más memoria principal: Sí, instalar más memoria principal puede permitir mejorar la tasa de utilización de la CPU. Una mayor cantidad de memoria principal permite almacenar más páginas y datos en la memoria, lo que reduce la necesidad de acceder al disco de paginación con frecuencia. Esto reduce los tiempos de espera asociados a los accesos a disco y permite que los procesos accedan más rápidamente a los datos necesarios, lo que puede aumentar la eficiencia y utilización de la CPU.

5. Instalar un disco duro más rápido: Sí, instalar un disco duro más rápido puede permitir mejorar la tasa de utilización de la CPU. Un disco duro más rápido puede reducir los tiempos de acceso a disco, lo que beneficia al sistema de paginación y a la gestión de la memoria. Menores tiempos de acceso a disco significan que los datos pueden ser leídos y escritos más rápidamente, reduciendo las esperas y mejorando el rendimiento general del sistema. Esto a su vez puede permitir una mayor utilización de la CPU al reducir los cuellos de botella relacionados con los accesos a disco.

