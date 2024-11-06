### DESAFÍO I

Células Procariotas:

No tienen núcleo definido.
Su ADN está en el citoplasma.
Carecen de organelas complejas.
Ejemplos: bacterias y arqueas.

Células Eucariotas:

Tienen un núcleo delimitado por una membrana.
Su ADN está en el núcleo.
Poseen organelas complejas (mitocondrias, cloroplastos).
Ejemplos: animales, plantas, hongos.


### DESAFÍO II

```python
# Diccionario con algunos codones de ARN de ejemplo
codigo_genetico = {
    'A': ['GCU', 'GCC', 'GCA', 'GCG'],
    'T': ['ACU', 'ACC', 'ACA', 'ACG'],
    'V': ['GUU', 'GUC', 'GUA', 'GUG'],
    'K': ['AAA', 'AAG'],
    'G': ['GGU', 'GGC', 'GGA', 'GGG'],
    'H': ['CAU', 'CAC'],
    'E': ['GAA', 'GAG'],
    'P': ['CCU', 'CCC', 'CCA', 'CCG'],
    'N': ['AAU', 'AAC'],
    'I': ['AUU', 'AUC', 'AUA'],
    'F': ['UUU', 'UUC'],
    'L': ['UUA', 'UUG', 'CUU', 'CUC', 'CUA', 'CUG'],
    'R': ['CGU', 'CGC', 'CGA', 'CGG', 'AGA', 'AGG'],
    'S': ['UCU', 'UCC', 'UCA', 'UCG', 'AGU', 'AGC'],
    'Q': ['CAA', 'CAG'],
    'C': ['UGU', 'UGC'],
    'Y': ['UAU', 'UAC'],
    'M': ['AUG'], # codón de inicio
}

# Secuencia proteica 
proteina = "ATVEKGGKHKTGPNEKGKKIFVQKCSQCHTVLHGLFGRKTGQA"

# funcion que da una secuencia de ARN
def obtener_arn(proteina):
    arn_secuencia = ""
    for aa in proteina:
        if aa in codigo_genetico:
            arn_secuencia += codigo_genetico[aa][0]  # Escoge el primer codón de cada aa
        else:
            arn_secuencia += '---'  # Indica error si el aa no está en el diccionario
    return arn_secuencia

print("ARN codificante:", obtener_arn(proteina))
```
### DESAFÍO III
```python
def buscar_caja_tata(secuencia):
    caja_tata = "TATAAA"
    posiciones = []
    for i in range(len(secuencia) - len(caja_tata) + 1):
        if secuencia[i:i+len(caja_tata)] == caja_tata:
            posiciones.append(i)
    return posiciones

# Lee el archivo
with open("secuencia_dna.txt", "r") as f:
    secuencia_dna = f.read().strip()

print("Posiciones de la caja TATA:", buscar_caja_tata(secuencia_dna))

```

### DESAFÍO IV
```python
def inicio_juego():
    imprimir_con_retraso("""
    🧬 Bienvenido al Juego de la Expresión Génica RPG 🧬
    En este juego, eres una célula que debe completar la expresión génica.
    Tu misión es transformar la información en el ADN en una proteína funcional.

    Para ganar, tendrás que superar varias fases: transcribir el ADN, salir del núcleo,
    y traducir el ARN en una cadena de aminoácidos.

    ¡Buena suerte, héroe molecular! 🚀
    """, 1.5)

def fase1_transcripcion():
    imprimir_con_retraso("""
    === Fase 1: Transcripción ===
    Estás en el núcleo celular. Aquí, el ADN contiene todas las instrucciones necesarias.
    Para comenzar, debes transcribir una cadena de ADN en ARN mensajero (ARNm).
    
    """, 1.2)

    # Desafío al jugador
    respuesta = input("¿Quieres transcribir el ADN a ARN? (sí/no): ").strip().lower()
    if respuesta == "sí":
        imprimir_con_retraso("""
        💥 ¡Éxito! Has transcrito el ADN en ARN mensajero (ARNm).
        Ahora, tienes una copia de la información genética en una molécula de ARN
        lista para salir del núcleo.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ Has decidido no transcribir el ADN. La expresión génica no puede continuar sin este paso.
        ¡Inténtalo de nuevo!
        """)
        fase1_transcripcion()  # Reintenta la fase

def fase2_salida_nucleo():
    imprimir_con_retraso("""
    === Fase 2: Salida del Núcleo ===
    Ahora que tienes el ARNm, necesitas llevarlo fuera del núcleo al citoplasma,
    donde se encuentran los ribosomas para la traducción.

    """, 1.2)

    # Desafío al jugador
    respuesta = input("¿Estás listo para salir del núcleo? (sí/no): ").strip().lower()
    if respuesta == "sí":
        imprimir_con_retraso("""
        🌊 ¡Bien hecho! El ARNm ha salido del núcleo y ha llegado al citoplasma.
        Ahora está listo para la traducción en los ribosomas.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ No has salido del núcleo. La traducción no puede comenzar sin llevar el ARNm al citoplasma.
        ¡Inténtalo de nuevo!
        """)
        fase2_salida_nucleo()  # Reintenta la fase

def fase3_traduccion():
    imprimir_con_retraso("""
    === Fase 3: Traducción ===
    Ahora el ARNm se encuentra en el citoplasma, y los ribosomas están listos
    para decodificar la información en una secuencia de aminoácidos.

    Para traducir la información, cada triplete de nucleótidos (codón) del ARNm se convierte en un aminoácido.
    Este es el momento clave para formar una proteína funcional.
    """, 1.5)

    # Desafío de traducción
    respuesta = input("¿Quieres comenzar la traducción del ARNm? (sí/no): ").strip().lower()
    if respuesta == "sí":
        imprimir_con_retraso("""
        🎉 ¡Felicitaciones! Los ribosomas han traducido la secuencia de ARNm en una proteína.
        Has completado exitosamente el proceso de expresión génica.
        
        🏆 ¡Has ganado el juego! Ahora eres un experto en expresión génica.
        """, 1)
    else:
        imprimir_con_retraso("""
        ❌ Sin traducción, no se puede crear una proteína. 
        ¡Intenta de nuevo para completar el proceso de expresión génica!
        """)
        fase3_traduccion()  # Reintenta la fase

def jugar():
    inicio_juego()
    fase1_transcripcion()
    fase2_salida_nucleo()
    fase3_traduccion()

# Ejecutar el juego
jugar()
```