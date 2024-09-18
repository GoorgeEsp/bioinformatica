### DESAFÍO I

El **ADN** almacena la información genética que determina las características y la identidad de un organismo.

### DESAFÍO II
Podrías utilizar un array en Python para almacenar la secuencia de aminoácidos, representando cada aminoácido con su letra única.

### DESAFÍO III

Podrías usar un diccionario en Python, donde las claves sean los residuos de aminoácidos y los valores sean sus coordenadas en el espacio 3D.

### DESAFÍO IV
**Contribuciones de Rosalind Franklin:**
Rosalind Franklin fue clave en la comprensión de la estructura del ADN mediante su técnica de difracción de rayos X. Su trabajo proporcionó la evidencia crucial para el modelo de doble hélice. Su historia resalta la importancia de reconocer el aporte de mujeres en la ciencia y los desafíos del reconocimiento en un campo dominado por hombres.

### DESAFÍO V
```python
def predecir_estructura(secuencia):
    predicciones = []
    for aminoacido in secuencia:
        if aminoacido in ["A", "L", "M"]:  # aminoácidos que favorecen hélices
            predicciones.append("H")
        elif aminoacido in ["F", "I", "V"]:  # aminoácidos que favorecen láminas
            predicciones.append("B")
        else:
            predicciones.append("L") 
    return predicciones
```

### DESAFÍO VI
**Diferencias entre individuos de una especie:**
realizar un análisis de secuencias genéticas usando alineamientos múltiples y ver las variaciones en los nucleótidos.  
**Información necesaria:** Secuencias de ADN de los individuos.  
**Expresión de información:** Representación en matrices o listas para análisis.