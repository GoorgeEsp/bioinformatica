### DESAFÍO I

¿Existe una única forma de alinearlas? 

No, ya que se pueden introducir gaps en distintas posiciones.

¿Es alguno de los posibles alineamientos mejor que otro? 

Un alineamiento "mejor" depende de los objetivos: en biología, el alineamiento que minimiza las modificaciones estructurales de las secuencias y ajusta mejor las posiciones conservadas sería considerado mejor.

¿Qué representan esos guiones? 

Los guiones representan inserciones o deleciones de nucleótidos o aminoácidos, es decir, variaciones estructurales.

### DESAFÍO II

¿Son todos los valores iguales? 

No, ya que las diferentes posiciones de los gaps afectan el cálculo de la identidad.

¿Qué consideraciones deberían tenerse en cuenta? 

La ubicación de los gaps y cómo se penalizan los cambios entre caracteres.

### DESAFÍO III
¿Cómo se relacionan los valores de identidad con las penalizaciones a los gaps? 

Una mayor penalización a los gaps reduce la cantidad de gaps en el alineamiento, lo que puede aumentar la identidad.

¿Qué implicancias tiene una mayor penalización de gaps? 

Penalizar más los gaps puede forzar el alineamiento de secuencias sin recurrir tanto a la inserción/deleción, lo que puede resultar en un alineamiento más conservado.

¿Qué otras formas de penalización podrían aplicarse? 

Además de la penalización por gaps, también podrían introducirse penalizaciones por sustituciones drásticas entre aminoácidos o nucleótidos.

### DESAFÍO IV

¿Qué implicaría la inserción o deleción de una región de más de un residuo? 

Esto podría alterar completamente la función de la proteína, dependiendo de la región afectada, ya que se alteraría la secuencia de aminoácidos.